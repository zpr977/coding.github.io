# coding.github.io
#include<iostream>
#include<string>


int LCS_func(const string &s1, const string &s2)
{
  if(s1.empty() || s2.empty())
  {
    return 0;
  }
  
  int row = s1.size();
  int col = s2.size();
  
  //状态：state[i][j]表示s1的前i个字符配合s2的前j个字符的最长lcs长度是多少
  vector<vector<int> > state(row + 1, vector<int> (col + 1, 0));
  
  //初始化：f[0][j] = f[i][0] = 0
  for(int i = 1; i<=row; ++i)
  {
    for(int j = 1; j <= col; ++j)
    {
      if(s1[i - 1] == s2[j - 1])
      {
        state[i][j] = state[i - 1][j - 1] + 1;
      }
      else
      {
        state[i][j] = max(state[i - 1][j]), state[i][j - 1];
      }
    }
  }
  
  //ans:
  return state[row][col];
}
