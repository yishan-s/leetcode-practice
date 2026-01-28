# 0217. Contains Duplicate

## Core Intuition
- **HashSet Optimization**: 利用 Hash 結構 $O(1)$ 的查找特性。
- **Java Trick**: `Set.add()` 若元素已存在會回傳 `false`。透過此特性可將「檢查」與「新增」合併為一個步驟。

## Complexity Analysis
- **Time Complexity**: $O(n)$ — 僅需遍歷一次陣列。
- **Space Complexity**: $O(n)$ — 最糟情況下（無重複）需儲存所有元素。

## Key Learnings!!
- **== vs .equals()**: 
    - Primitive types (`int`, `char`) 用 `==`。
    - Objects (`Integer`, `String`) 用 `.equals()`。
- **Collection**: 宣告時建議使用介面 `Set<Integer>`，實作時再用 `new HashSet<>()`，這符合 OOP 的 Polymorphism。

## Refinement
- Version 1 使用了雙層迴圈 $O(n^2)$，效率超差。
  ```
  class Solution {
    public boolean containsDuplicate(int[] nums) {
      boolean res = false;
      for(int i = 0; i < nums.length; i++) {
        for(int j = i + 1; j < nums.length; j++){
          if(nums[i] == nums[j]) {
            res = true;
            return res;
          }
        }
      }
      return res;
    }
  }
  ```
- 優化版使用 `HashSet` 將時間縮短至線性時間。
