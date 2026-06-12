---
title: "Adding a shortcut to program in shell"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by makescents on 2010-10-19
Hello,

For my computer science course we have to use a language called Maude which has an interpreter that I downloaded from this site:

[http://maude.cs.uiuc.edu/](http://maude.cs.uiuc.edu/)

However everytime I wish to run the program I must navigate to the executable and run it using "./maude.linux" in the shell.

Is there anyway I can simply type "maude" in a shell to run the interpreter without navigating to where it is located everytime, like I can do with Python?

Thanks.

---

### Post by kerry_s on 2010-10-19
have you tried putting it in path?

create a folder in your home called "bin".
(mkdir ~/bin)

normally that would be where you put executables, but since you already got it somewhere else you can just link.
using the gui you drag & drop with the middle click.
in terminal: ln -s /path/to/script ~/bin/script

just a note: after you create the bin folder you need to log out & back in for it to be usable.

---

