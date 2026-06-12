---
title: "C++ Compiling and Running"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by igneousquill on 2008-12-17
I'm new to Ubuntu and also am just beginning to learn how to program.  This afternoon I tried to set up a simple program to compile and run through the terminal, but it just gives me a > prompt that won't do anything after that.  I downloaded/installed g++ and gcc through the terminal beforehand.  The tutorial I'm following can be found at the links below.

[http://www.intap.net/~drw/cpp/cpp02_01.htm](http://www.intap.net/~drw/cpp/cpp02_01.htm)
[http://www.intap.net/~drw/cpp/cpp02_02.htm](http://www.intap.net/~drw/cpp/cpp02_02.htm)

I realize this is an Ubuntu forum and not C++, and I am asking these questions at a C++ forum as well.  I just figured someone here might know the right answer.

Thanks for any help.

---

### Post by donkyhotay on 2008-12-17
There is a specific forum for programming questions. This should be moved there. Until a mod does this here is the link for it. 
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Shhnap on 2008-12-17
also make sure you have:

sudo apt-get install build-essential

And you would only get the > if you did not reach an EOF character of a finishing character. Try pressing Ctrl-D when this happens.

---

### Post by donkyhotay on 2008-12-17
> **Shhnap said:**
> also make sure you have:

sudo apt-get install build-essential

And you would only get the > if you did not reach an EOF character of a finishing character. Try pressing Ctrl-D when this happens.

That brings up a point I should have thought of, are you able to compile other programs?

---

### Post by ibuclaw on 2008-12-17
One of my favourite "on the fly" programming tools for C/C++ is definitely [a program called 'large-C']("http://freshmeat.net/projects/large-c/").
It's a pseudo-interpreter (doesn't actually do any interpreting). It just preps and compiles your .c/.cpp/<stdin> for you and runs. :)

Basic usage for C++
```
C -p
```
Then type:
```

#include <iostream>
using namespace std;
int main() {
cout << "Hello World\n" << endl;
return 0;
}

```
Press **Ctrl+D** to terminate the read from input, and wait for the output to come out :)


And when operating on files, just run
```
C -p [COLOR="Red"]helloworld[/COLOR].cpp
```
on your C++ source file

Now because it compiles the source, it will be slow the first time you run it - but - run the same app again, and it will be instant (as it caches all compiled scripts in the /tmp folder).


Regards
Iain

---

### Post by igneousquill on 2008-12-17
> **Shhnap said:**
> also make sure you have:

sudo apt-get install build-essential

And you would only get the > if you did not reach an EOF character of a finishing character. Try pressing Ctrl-D when this happens.

I did the install beforehand.  Ctrl-D gets me this:

> bash: unexpected EOF while looking for matching `''
bash: syntax error: unexpected end of file

---

### Post by Shhnap on 2008-12-17
Can you pop the code you're writing here??

---

### Post by igneousquill on 2008-12-17
> **donkyhotay said:**
> That brings up a point I should have thought of, are you able to compile other programs?

Ah...well, when I say I'm a "beginner" I really mean it!  My experience is limited at this point to a couple of weeks with Python so C++ is completely new territory for me.

---

### Post by ibuclaw on 2008-12-17
Also, I recommend that you'd learn from this tutorial here:
[http://www.cprogramming.com/tutorial.html#c++tutorial](http://www.cprogramming.com/tutorial.html#c++tutorial)

The above is what helped me get started onto C++.

It gives, in my opinion, excellent explanations, and the quizzes it provides are excellent for recapping (despite the fact that they only provide it for the first half dozen sections).

Regards
Iain

---

### Post by |{urse on 2008-12-17
C -p huh? that's awesome, Just when you think you knew something!

Ive always just used nano and g++

nano cprogram
<write some code>
g++ cprogram
./a.out

---

### Post by igneousquill on 2008-12-17
> **tinivole said:**
> Also, I recommend that you'd learn from this tutorial here:
[http://www.cprogramming.com/tutorial.html#c++tutorial](http://www.cprogramming.com/tutorial.html#c++tutorial)

The above is what helped me get started onto C++.

It gives, in my opinion, excellent explanations, and the quizzes it provides are excellent for recapping (despite the fact that they only provide it for the first half dozen sections).

Regards
Iain

Thanks!  I've bookmarked it.

---

### Post by ibuclaw on 2008-12-17
> **|{urse said:**
> C -p huh? that's awesome, Just when you think you knew something!

Ive always just used nano and g++

nano cprogram
<write some code>
g++ cprogram
./a.out
nano?

Real programmers use vim :)

```
sudo apt-get install vim
```
And paste this into your **~/.vimrc** file
```

" use visual bell instead of beeping
"set vb

" " incremental search
set incsearch

" syntax highlighting
set bg=light
syntax on

" autoindent
set autoindent|set smartindent

" 4 space tabs
set tabstop=4|set shiftwidth=4|set expandtab|set softtabstop=4

" show matching brackets
set showmatch

" show line numbers
"set number

" dont use Q for Ex mode
map Q :q

" make tab in v mode ident code
vmap <tab> >gv
vmap <s-tab> <gv

" make tab in normal mode ident code
nmap <tab> I<tab><esc>
nmap <s-tab> ^i<bs><esc>

" paste mode - this will avoid unexpected effects when you
" cut or copy some text from one window and paste it in Vim.
set pastetoggle=<F11>

" comment/uncomment blocks of code (in vmode)
vmap _c :s/^/#/gi<Enter>
vmap _C :s/^#//gi<Enter>

" syntax color complex things like @{${"foo"}}
let perl_extended_vars = 1


```
And program in [COLOR="Red"]c[/COLOR][COLOR="Blue"]o[/COLOR][COLOR="DarkOrange"]l[COLOR="Magenta"]o[/COLOR][/COLOR][COLOR="Lime"]u[/COLOR][COLOR="YellowGreen"]r[/COLOR]

Regards
Iain

---

### Post by |{urse on 2008-12-17
Um, okay, can i take my thanks back? lol @ Vim.

nanorc
> syntax "c" "\.(c|C|cc|cpp|cxx|h|H|hh|hpp|hxx)$"
## Preprocessor directives (Anything that begins with #)
color brightblack "#+(.*)"
##
## General syntax
color brightred "\<[A-Z_][0-9A-Z_]+\>"
color green "\<(float|double|bool|char|int|short|long|sizeof|enum|void|static|const|struct|union|typedef|extern|signed|unsigned|inline)\>"
color green "\<(u_?)?int(8|16|32|64|ptr)_t\>"
color green "\<(class|namespace|template|public|protected|private|typename|this|friend|virtual|using|mutable|volatile|register|explicit)\>"
color brightyellow "\<(for|if|while|do|else|case|default|switch)\>"
color brightyellow "\<(try|throw|catch|operator|new|delete)\>"
color magenta "\<(goto|continue|break|return|throw)\>"
color brightcyan "^space:*#space:*(define|undef|include|ifn?def|endif|elif|else|if|warning|error)"
color brightmagenta "'([^'\]|(\\["'abfnrtv\\]))'" "'\\(([0-3]?[0-7]{1,2}))'" "'\\x[0-9A-Fa-f]{1,2}'"
##
## GCC builtins
color cyan "__attribute__space:*\(\([^)]*\)\)" "__(aligned|asm|builtin|hidden|inline|packed|restrict|section|typeof|weak)__"
##
## String highlighting.  You will in general want your comments and
## strings to come last, because syntax highlighting rules will be
## applied in the order they are read in.
color brightyellow "<[^=        ]*>" ""(\\.|[^"])*""
##
## This string is VERY resource intensive!
color brightyellow start=""(\\.|[^"])*\\space:*$" end="^(\\.|[^"])*""
##
## Comment highlighting
color brightblue "//.*"
color brightblue start="/\*" end="\*/"


---

### Post by igneousquill on 2008-12-18
I should have thought of this last night.  Should the file name end with .C or .cpp?  I used the former, as I assumed the latter was for Windows only and I'm using Ubuntu.

I can't check it now because I'm at work on a Mac, but if that's it I'm going to feel pretty stupid.

---

### Post by ibuclaw on 2008-12-18
The standard naming convention of C++ source files depends from place to place, but the two most common are
[LIST]
[*].cpp
[*].cc
[/LIST]

I would recommending using the .cpp extension.

Regards
Iain

---

### Post by igneousquill on 2008-12-18
> **tinivole said:**
> The standard naming convention of C++ source files depends from place to place, but the two most common are
[LIST]
[*].cpp
[*].cc
[/LIST]

I would recommending using the .cpp extension.

Regards
Iain

Thanks.  I'll try first one then the other tonight or tomorrow morning.  I'm to the point where I'm thinking I should stick to Python until I've mastered it, then look at C++.  Dunno.

---

