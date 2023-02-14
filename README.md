# yq

yq is written in go - so you can download a dependency free binary for your platform and you are good to go! If you prefer there are a variety of package managers that can be used as well as Docker and Podman, all listed below.

### GitHub Action
```
  - name: Set foobar to cool
    uses: mikefarah/yq@master
    with:
      cmd: yq -i '.foo.bar = "cool"' 'config.yml'
  - name: Get an entry with a variable that might contain dots or spaces
    id: get_username
    uses: mikefarah/yq@master
    with:
      cmd: yq '.all.children.["${{ matrix.ip_address }}"].username' ops/inventories/production.yml
  - name: Reuse a variable obtained in another step
    run: echo ${{ steps.get_username.outputs.result }}
```

```
Usage:
  yq [flags]
  yq [command]

Examples:

# yq defaults to 'eval' command if no command is specified. See "yq eval --help" for more examples.
yq '.stuff' < myfile.yml # outputs the data at the "stuff" node from "myfile.yml"

yq -i '.stuff = "foo"' myfile.yml # update myfile.yml inplace


Available Commands:
  completion       Generate the autocompletion script for the specified shell
  eval             (default) Apply the expression to each document in each yaml file in sequence
  eval-all         Loads _all_ yaml documents of _all_ yaml files and runs expression once
  help             Help about any command
  shell-completion Generate completion script

Flags:
  -C, --colors                        force print with colors
  -e, --exit-status                   set exit status if there are no matches or null or false is returned
  -f, --front-matter string           (extract|process) first input as yaml front-matter. Extract will pull out the yaml content, process will run the expression against the yaml content, leaving the remaining data intact
      --header-preprocess             Slurp any header comments and separators before processing expression. (default true)
  -h, --help                          help for yq
  -I, --indent int                    sets indent level for output (default 2)
  -i, --inplace                       update the file inplace of first file given.
  -p, --input-format string           [yaml|y|xml|x] parse format for input. Note that json is a subset of yaml. (default "yaml")
  -M, --no-colors                     force print with no colors
  -N, --no-doc                        Don't print document separators (---)
  -n, --null-input                    Don't read input, simply evaluate the expression given. Useful for creating docs from scratch.
  -o, --output-format string          [yaml|y|json|j|props|p|xml|x] output format type. (default "yaml")
  -P, --prettyPrint                   pretty print, shorthand for '... style = ""'
  -s, --split-exp string              print each result (or doc) into a file named (exp). [exp] argument must return a string. You can use $index in the expression as the result counter.
      --unwrapScalar                  unwrap scalar, print the value with no quotes, colors or comments (default true)
  -v, --verbose                       verbose mode
  -V, --version                       Print version information and quit
      --xml-attribute-prefix string   prefix for xml attributes (default "+")
      --xml-content-name string       name for xml content (if no attribute name is present). (default "+content")

Use "yq [command] --help" for more information about a command.
```
