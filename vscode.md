# visual studio code 工作区配置文件
*******
```json
{
	"folders": [ ],
	"settings": { },
	"launch": { },
	"tasks": { }
}

```

******
### folders:在其中添加文件夹到工作区内
```json
{
	"path": "D:\\MYcode\\vsc_ACM-ICPC",
}
```
******
### launch :
```json
{
    "version": "0.2.0",
    "configurations":[
        {
            "name": "C++ Launch (GDB)",                 // 配置名称，将会在启动配置的下拉菜单中显示
            "type": "cppdbg",                           // 配置类型，这里只能为cppdbg
            "request": "launch",   // 请求配置类型，可以为launch（启动）或attach（附加）
            "targetArchitecture": "x64",                // 生成目标架构，一般为x86或x64
            "program": "${fileDirname}/${fileBasenameNoExtension}.exe", // 将要进行调试的程序的路径
            "args": [],              // 程序调试时传递给程序的命令行参数，一般设为空即可
            "stopAtEntry": false,                       // 设为true时程序将暂停在程序入口处，一般设置为false
            "cwd": "${workspaceRoot}",                  // 调试程序时的工作目录，一般为${workspaceRoot}
            "externalConsole": true,                    // 调试时是否显示控制台窗口，一般设置为true显示控制台
            "internalConsoleOptions": "neverOpen",      // 如果不设为neverOpen，调试时会跳到“调试控制台”选项卡",
            "MIMode": "gdb",                            // 指定连接的调试器
            "miDebuggerPath": "C:/TDM-GCC-64/bin/gdb64.exe", // 调试器路径
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for GDB",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": false
                }
            ],
            "preLaunchTask": "Compile"
        }
    ]
}
```
******
### tasks :
```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Compile",
            "command": "g++",
            "args": [
                "-g ${file}",   //指定编译源代码文件
                "-o ${fileDirname}/${fileBasenameNoExtension}.exe", // 指定输出文件名，不加该参数则默认输出a.exe
                "-ggdb3",   // 生成和调试有关的信息
                "-Wall",    // 开启额外警告
                "-static-libgcc",   // 静态链接
                "-std=c++17",       // 使用最新的c++17标准
                "-Wno-format",
                "-finput-charset=UTF-8",//输入编译器文本编码 默认为UTF-8
                "-fexec-charset=GBK"//编译器输出文本编码 自行选择
            ],

            "type": "shell",

            "group": {
                "kind": "build",
                "isDefault": true
            },

            "presentation": {
                "echo": true,
                "reveal": "always", // 在“终端”中显示编译信息的策略，可以为always，silent，never
                 "focus": false,
                 "panel": "shared" // 不同的文件的编译信息共享一个终端面板
            },

            "problemMatcher": {
                "owner": "cpp",
                "fileLocation": [
                    "relative", "\\"
                ],
                "pattern": {
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning|error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            }
        }
    ]
}
```
***********
### setting :
**********