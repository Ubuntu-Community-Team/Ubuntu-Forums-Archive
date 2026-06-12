---
title: "creating a variable to hold a path with spaces and special chars"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by kgeary on 2011-03-25
I have a long path to a shared directory on a remote server I am frequently having to access.  I'll abbreviate it the path as:

**/home/user/.gvfs/c$ on blah/**

(It contains '.' '$' and space characters)

I can't change the path so I'm trying to create a variable in .bashrc so I can simply type **cd $myserver** to access it.

I have tried all sorts of variations of the following:

[B]export myserver="~/.gvfs/c\$\ on\ blah"
[/B]

But it typically says it can't find the path and it shows the path stopping after the $ and before the first space.
I've tried switching between single/double quotes, back ticks, etc. but nothing seems to work.

My questions are:

1.  Is creating and exporting a variable in the .bashrc a good solution here or should I be doing something else?

2.  how can I format this variable so it won't complain about the $ or spaces?

Thanks in advance

kg

---

### Post by asmoore82 on 2011-03-25
You have to use quotations when you reference the variable:
```
cd "$myserver"
```

An alias would probably work better for you:
```
#in .bashrc
alias myserver='cd "/some/wild/path"'
...
#in everyday terminal
myserver
```

---

### Post by SeijiSensei on 2011-03-25
Put the string in single-quotes rather than doubles.  bash interprets 

'/home/user/.gvfs/c$ on blah/'

literally while it interprets

"/home/user/.gvfs/c$ on blah/"

as including an environment variable after the dollar-sign.  See the section entitled "QUOTING" in "man bash".

---

