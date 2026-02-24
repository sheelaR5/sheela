1.BST Construction from preorder
class TreeNode {
    int val;
    TreeNode left, right;

  TreeNode(int val) {
        this.val = val;
        left = right = null;
    }
}

class Solution {

  int index = 0;   

  public TreeNode bstFromPreorder(int[] preorder) {
        return build(preorder, Integer.MIN_VALUE, Integer.MAX_VALUE);
    }

  private TreeNode build(int[] preorder, int min, int max) {
        
  if (index >= preorder.length)
            return null;

  int value = preorder[index];
  f (value < min || value > max)
            return null;

  TreeNode root = new TreeNode(value);
        index++;

  root.left = build(preorder, min, value);

  root.right = build(preorder, value, max);

  return root;
    }
}
Output:
[8,5,1,7,10,12]




2.01 Matrix

import java.util.*;

class Solution {
    public int[][] updateMatrix(int[][] mat) {
        
  int m = mat.length;
  int n = mat[0].length;
        
  Queue<int[]> q = new LinkedList<>();
        
        
  for (int i = 0; i < m; i++) {
  for (int j = 0; j < n; j++) {
  if (mat[i][j] == 0) {
  q.offer(new int[]{i, j});
  } else {
  mat[i][j] = -1; // mark as unvisited
                }
            }
        }
        
        
  int[][] dir = {{1,0},{-1,0},{0,1},{0,-1}};
        
        
  while (!q.isEmpty()) {
  int[] cell = q.poll();
            
  for (int[] d : dir) {
  int r = cell[0] + d[0];
  int c = cell[1] + d[1];
                
  if (r >= 0 && r < m && c >= 0 && c < n && mat[r][c] == -1) {
  mat[r][c] = mat[cell[0]][cell[1]] + 1;
  q.offer(new int[]{r, c});
                }
            }
        }
        
  return mat;
    }
}

output:
[[0,0,0],
 [0,1,0],
 [0,0,0]]
