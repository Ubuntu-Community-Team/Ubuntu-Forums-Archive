---
title: "How to use the find command?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Rumtscho on 2009-05-07
I just started learning LaTeX, and needed to read a package documentation, but didn't know where LaTeX is installed. So I tried using the find command, but didn't find anything. After browsing through the file system, I located what I needed in /usr/share. But this isn`t my idea of efficient work. 

```

rumi@LinuxPC:~/LaTeX$ find / texmf -type d
........... (here comes a very, very long list of directory paths) ....
find: `texmf': No such file or directory
rumi@LinuxPC:~/LaTeX$ ls /usr/share | grep tex
latex2html
latex2rtf
tex-common
texlive-base
texlive-bin
texmf
texmf-texlive
rumi@LinuxPC:~/LaTeX$ 

``` 

Obviously, the directory exists. Why didn't the find command find it? What should I have typed in order to find it?

---

### Post by sisco311 on 2009-05-07
something like:
```
find / -type d -iname "texfm"
find / -type d -name "tex*"
man find
```should work.

[uhelp]community/find[/uhelp]

but why don't you list the files installed to the system from the package, with:
```
dpkg-query -L package-name
man dpkg-query
```:evil:

---

### Post by Rumtscho on 2009-05-07
Thank you very much, 

Both variants worked. The reason I didn't use the dpkg-query is that I didn't know it existed :) (with my current Linux experience level, I am actually proud of myself when I don't forget that file names are case sensitive...)

---

### Post by mcduck on 2009-05-07
other search tools you might want to know about are *whereis* and *locate*.

*whereis* locates executable file, source code and documentation for a program.

*locate* searches for files by name, but uses a database-based search which makes it very quick tool (at least when searching for stuff that you didn't just install 5 minutes ago as it wouldn't be in the database yet..). To update the search database you can use "sudo updatedb"-command.

edit:

of course *apropos* could be useful as well. It searches from manual pages to find programs that do certain tasks. For example "apropos search" would list available search tools. Nice tool when you know what you need to do but not what program to sue to do it..

---

### Post by andrew.46 on 2009-05-07
Hi Rumtscho,

> **Rumtscho said:**
> [...] with my current Linux experience level, I am actually proud of myself when I don't forget that file names are case sensitive...

You may be interested in the first guide in a projected long series:


Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

All the best,

Andrew

---

### Post by Stefan_K on 2009-05-07
Hi Rumtscho,

you could use LaTeX tools like [kpsewhich]("http://texblog.net/hypertext-help/latex-tools/kpsewhich/") and [texdoc]("http://texblog.net/hypertext-help/latex-tools/texdoc/"). Examples:

```
kpsewhich -var-value=TEXMF
```
will show you all texmf directories.

```
kpsewhich latex.ltx
```
will output the location of latex.ltx.

```
texdoc babel
```
will show documentation of babel.

```
gedit `kpsewhich article.cls`
```
will find the article class source file and open it in gedit for you to read.

You've asked for information concerning efficient work, perhaps have a look here:

[LIST]
[*] [Speed up the work by shell scripts]("http://texblog.net/latex-archive/linux/shell-scripts-linux-unix/") - providing scripts and explanation for efficient work with (La)TeX sources, edit and search sourcefiles without needing to know their location: texedit, texgrep, texls
[*] [Speed up the work by shell scripts II]("http://texblog.net/latex-archive/linux/shell-scripts-linux-unix-source/") - one more script to change into the directory of a file, you just need to know the name, not its path. There's another approach discussed using shell functions instead of scripts.
[/LIST]

Stefan


--
[TeXblog.net]("http://texblog.net")

---

