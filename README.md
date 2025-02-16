# issue-to-markdown

[GitHub Issue から Markdown ファイルを生成してブログ記事を公開する](https://ikuma-t.com/blog/publish-blog-from-github-issue/)  

`Commit Content File`で権限エラー  
GitHub Actionsの実行中にリポジトリへの書き込み権限がないために発生しています。具体的には、github-actions[bot] ユーザーがリポジトリにプッシュしようとしていますが、権限が不足しているため、HTTP 403 エラーが返されています。  

解決方法  
permissionsを設定する。  

[github actionsの「permissions」とはなにか？](https://zenn.dev/not75743/scraps/926f2693809744)

``` log
{
  raw: '',
  remote: null,
  branches: [],
  tags: [],
  updated: [],
  deleted: []
}
> Checking-out branch...
Creating '2025-02-16' branch.
> Not pulling from repo.
> Creating commit...
{
  author: null,
  branch: '2025-02-16',
  commit: '420af1014ea5c966e77581d72b626fc1e3b2bb23',
  root: false,
  summary: { changes: 1, insertions: 12, deletions: 0 }
}
> No tag info provided.
> Pushing commit to repo...
Error: Error: Pushing to https://github.com/rendya2501/issue-to-markdown
remote: Permission to rendya2501/issue-to-markdown.git denied to github-actions[bot].
fatal: unable to access 'https://github.com/rendya2501/issue-to-markdown/': The requested URL returned error: 403


Outputs
Error: Error: Pushing to https://github.com/rendya2501/issue-to-markdown
remote: Permission to rendya2501/issue-to-markdown.git denied to github-actions[bot].
fatal: unable to access 'https://github.com/rendya2501/issue-to-markdown/': The requested URL returned error: 403
```

Create PullRequestでのエラー

解決方法
[GitHub ActionsでのPR操作権限はデフォルトでオフになったよ](https://zenn.dev/kenghaya/articles/d7f766e5db6437)

``` log
Run gh pr create --title "2025-02-16" --body "#1" --base main --head 2025-02-16
  gh pr create --title "2025-02-16" --body "#1" --base main --head 2025-02-16
  shell: /usr/bin/bash -e {0}
  env:
    GITHUB_TOKEN: ***
pull request create failed: GraphQL: GitHub Actions is not permitted to create or approve pull requests (createPullRequest)
Error: Process completed with exit code 1.
```
