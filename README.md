## Installation

### Install [Gridsome CLI tool](https://gridsome.org/docs/#1-install-gridsome-cli-tool)

- **Using YARN**  `yarn global add @gridsome/cli`
- **Using NPM**   `npm install --global @gridsome/cli`

## Create your wikis project 

### create a new project using gridsome-cli tools
```
gridsome create my-project https://github.com/threefoldfoundation/gridsome-docc
```

### Run the project for the firt time
- `cd my-project`
- `gridsome develop`

### support loading markdown from several repos (example) 

- use example directory `cp -r examples/wikis ~/wikis`
- Update `gridsome.conf.js` then re-run
  ```
    nav: {
          links: [
            { path: '/github/wikis1/', title: 'Docs' }
          ]
        },
        sidebar: [
          {
            name: 'docs',
            sections: [
              {
                title: 'Getting Started',
                items: [
                  '/github/wikis1/',
                  '/github/wikis1/installation/',
                  '/github/wikis1/writing-content/',
                  '/github/wikis1/deploying/',
                ]
              },
              {
                title: 'Configuration',
                items: [
                  '/github/wikis1/settings/',
                  '/github/wikis1/sidebar/',
                ]
              }
            ]
          }
        ]
    ...

    plugins: [
        {
          use: '@gridsome/source-filesystem',
          options: {
            baseDir: '~/wikis/',
            path: '**/*.md',
            typeName: 'MarkdownPage',
            remark: {
              externalLinksTarget: '_blank',
              externalLinksRel: ['noopener', 'noreferrer'],
              plugins: [
                '@gridsome/remark-prismjs'
              ]
            }
          }
        },
    ...
    ```

### Support for markdown inclusions

use  `!!!include:$orgname:$reponame:$docname` i.e `!!!include:$github:$wikis2:$settings`  in your marddown page to include another page

## More Documentation
can be found [here](https://docc-theme.netlify.com/)


