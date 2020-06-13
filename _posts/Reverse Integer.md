# **[Reverse Integer](https://leetcode-cn.com/problems/reverse-integer/)**

难度：简单

**Given a 32-bit signed integer, reverse digits of  integer.**

Example 1:

Input: 123
Output: 321

Example 2:

Input: -123
Output: -321

Example 3:

Input: 120
Output: 21

**Note:**
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

## 思路：

- 将数字转化成字符串，利用切片把字符串反转，在转化成数字，判断是否越界，得到结果。

  ```python
  class Solution(object):
      def reverse(self, x):
          """
          :type x: int
          :rtype: int
          """
          str_x=str(x)
          if str_x[0]=='-':
              str_x=str_x[:0:-1]
              x=int(str_x)
              x=-x
          else:
              str_x=str_x[::-1]
              x=int(str_x)
          return x if -2147483648 < x < 2147483647 else 0
  
  ```

- 每次取数字的最后一位，利用每次得到的最后一位组成新的数字，得到的数字即为原数字的反转，最后判断是否越界

  ```python
  class Solution(object):
      def reverse(self, x):
          """
          :type x: int
          :rtype: int
          """
          res=0
          a=abs(x)
          while a:
             res=res*10+a%10
             a=a/10
          if res>2147483647 or res<-2147483648:
              return 0
          else:
              return res if x>0 else -res
  ```

  