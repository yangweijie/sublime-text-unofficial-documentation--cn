# 缩进配置
---

### 概述

缩进配置包括设置制表符大小和`Tab`键功能（插入制表符还是空格），除了在文件加载时自动检测文件缩进外，这些设置全部都可以由用户重新进行自定义，可以是针对于文件类型甚至是个别文件。

## 配置

`tab_size`: 整数类型——制表符缩进的大小（默认应该是4字符）
 
`translate_tabs_to_spaces`： 布尔类型, 如果为真，按下`Tab`键时插入空格代替制表符

`detect_indentation`： 布尔类型, 如果为真 (默认), `SublimeTex`t将会在文件加载时自动检测文件的缩进设置。

`use_tab_stops`： 布尔类型, 如果为真, `use_tab_stops`将使`Tab`键和`Backspace`的`insert/delete`提到下一个制表位。

### 配置文件

配置文件将按如下顺序被读取：

1. `Packages/Default/Preferences.sublime-settings`
2. `Packages/Default/Preferences (<platform>).sublime-settings`
3. `Packages/User/Preferences.sublime-settings`
4. `Packages/<syntax>/<syntax>.sublime-settings`
5. `Packages/User/<syntax>.sublime-settings `    

一般情况下。应该将自定义的配置放在`Packages/User/Preferences.sublime-settings` 文件下,如果要对某个文件类型进行指定配置，例如，`Python`，应该将配置内容保存在`Packages/User/Python.sublime-settings`中。

### 配置文件样例

将下面的内容保存在`Packages/User/Preferences.sublime-settings`文件中。

	{
	    "tab_size": 4,
	    "translate_tabs_to_spaces": false
	}

### 单个语法配置

配置可以在每一个语法基础上单独指定。你可以通过`Preferences/Settings - More/Syntax Specific - User` 文件来编辑当前语法的配置。

## 缩进检测

当文件被加载时，将会自动检测文件内容，确定`tab_size`和`translate_tabs_to_spaces`设置，同时状态栏区域将会显示具体信息。另外，虽然在一般情况下缩进检测是个不错的功能，但保不齐你或许会想要禁用它，这时，你可以通过`detect_indentation`配置来进行修改。

缩进检测可以通过`View/Indentation/Guess Settings From Buffer`菜单来运行`detect_indentation`命令达到手动运行缩进检测的目的。

## 制表符和空格的相互转换

在`View/Indentation`菜单下拥有在当前文档实现制表符和空格转换的菜单项。这些菜单项通过运行`expand_tabs`和`unexpand_tabs`命令来实现制表符和空格之间的相互转换功能。

## 自动缩进

当你按下`Enter`键时，自动缩进功能将会根据当前行空格的数量来猜测新增行的缩进并根据此猜测来插入新增行。此功能通过下列配置来控制：

auto_indent： 布尔类型, 默认启用。 启用自动缩进功能
smart_indent： 布尔类型, 默认启用。使自动缩进变得更智能, `e.g., by indenting the next line after an if statement in C.`
trim_automatic_white_space: 布尔类型，默认启用。当移动插入符移出一行时移除`auto_indent`生成的空白格。    
indent_to_bracket：布尔类型，默认禁用. `Adds whitespace up to the first open bracket when indenting. Use when indenting like this`:

	use_indent_to_bracket(to_indent,
    	                  like_this);
