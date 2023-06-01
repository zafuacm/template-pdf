# ZAFU ACM 模板

基于 GitHub Action 的模板 PDF 导出框架。

## 如何使用

请 Fork 本仓库，授予 GitHub Action 相关权限。此后可以修改源文件和 [CI 编译命令](./.github/workflows/deploy.yml)。

src 目录下有两个文档示例，修改这两个文件，push 即可获得 PDF：

- `main.md`，MarkDown 格式，比较方便导出代码。
- `math.tex`，$\rm\LaTeX$ 格式，比较方便写数学公式，有定理等环境。

## 编译流程

如需更深层次的自定义，可以修改 CI 编译命令和 LaTeX 样式。对于 MarkDown 格式的文件，需要先合并再用 Pandoc 转换为 LaTeX 文档。我们提供了四种文件头，其章节样式、单栏双栏有所不同。

```bash
$ # 合并样式和文档
$ cat src/main-bookstyle-horizontal.md    src/main.md  > build/bookstyle-horizontal.md
$ # 生成 LaTeX 文档
$ pandoc build/bookstyle-horizontal.md --template="style/pureart.latex" --listings -o build/bookstyle-horizontal.tex --top-level-division=chapter
$ # 如是 Article 样式，不使用 top-level-division
$ pandoc build/articlestyle-horizontal.md --template="style/pureart.latex" --listings -o build/articlestyle-horizontal.tex 
```

## 备注

- 示例文件来自 [rogeryoungh](https://github.com/rogeryoungh/code-of-acm)，队名 pop rbp。
- 感谢 [ECNU F0RE1GNERS](https://github.com/XCPCIO/template-Markdown-ECNU-F0RE1GNERS) 提供的想法。
