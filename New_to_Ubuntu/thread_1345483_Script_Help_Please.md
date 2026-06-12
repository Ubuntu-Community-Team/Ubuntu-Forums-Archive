---
title: "Script Help Please"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-04
So, I'm working in a Sams RedHat 9 book, on an Ubuntu install (I know, but I'm doing the best with what I have).  I'm writing my first script and it's discussing $PATH and environment variables.  When issuing the "echo $PATH" command in my terminal, what is printed is:

me@me:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Which is different then what is printed in the book:

/usr/local/bin:/bin:/usr/bin::/usr/X11R6/bin:/home/you/bin

Could this be why when attempting to follow the directions of (from the book):

me@me:~$ mkdir ~/bin
me@me:~$ mv myscript ~/bin
me@me:~$ chomd u+x ~/bin/myscript
me@me:~$  myscript myfile.tex

Where "myscript" (written in vi from the home directory) is:

**Code**: 

#!/bin/sh
LATEX="$1"
DVIFILE="$(echo "$LATEXFILE" | sed 's/tex$/dvi/')"
latex "$LATEXFILE"
dvips "$DVIFILE"

Returns the results of:

me@me:~$ myscript myfile.tex
No command 'myscript' found, did you mean:
 Command 'pyscript' from package 'python-pyscript' (universe)
myscript: command not found

Any help would be greatly appreciate.

---

### Post by Some Penguin on 2009-12-04
Yep, that would do it.  Add /home/wherever/bin to your path.

---

### Post by Diametric on 2009-12-04
Cool, I figured as much.  I don't mean to be dense, but could you please specify the " Add /home/wherever/bin to your path." directions? Specifically, where on my path should I create /home/wherever/bin?  I'm also curious as to why at the terminal I do not default in $PATH to some home directory.  I know how to make a directory, but where should I so I can follow the instructions and why does my terminal path not default to home?

Thanks for the reply.

---

### Post by ukripper on 2009-12-04
```
vi ~/.bashrc
```


add below to that file
> PATH=$PATH:/home/**yourusername**/bin
export PATH

then run this in terminal:
```
source ~/.bashrc
```

---

### Post by Diametric on 2009-12-04
ukripper: thanks for your reply.  However, I'm still new to this, so:

1. The first code you wrote: Is that from the terminal or should I create a new vi file, or append my existing file?

2. You say "add below to that" ...to what...the new vi file, my file?

I know this sort of issue must frustrate some of you, but I'm determined to rid myself of Windows and that means I gotta get dirty with the basics...and it seems I may need a bit of hand holding here.

---

### Post by ukripper on 2009-12-04
> **Diametric said:**
> ukripper: thanks for your reply.  However, I'm still new to this, so:

1. The first code you wrote: Is that from the terminal or should I create a new vi file, or append my existing file?

This already exist for all users and determines your paths at login.

> 
2. You say "add below to that" ...to what...the new vi file, my file?

add to ~/.bashrc file where "~" means same as path /home/yourusername. in other words yiou can use /home/yourusername/.bashrc or simply use ~/.bashrc

---

