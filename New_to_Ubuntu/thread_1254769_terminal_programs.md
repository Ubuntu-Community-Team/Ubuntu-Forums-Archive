---
title: "terminal programs?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by linux_noob0 on 2009-08-31
hi there! i was wondering if there was a way to make an executable file ( in my case a compiled c++ program ) executable without navigating to the actual file, but more like the other installed applications ( for example vim pops out just after i type vim, i don't have to look for the actual thing and call ./vim ).. thanks in advance!!!!!!

---

### Post by credobyte on 2009-08-31
```
alias mycoolapp='/home/dainis/myapp'

```

---

### Post by Locutus_of_Borg on 2009-08-31
add the path to your $PATH

e.g.

mkdir ~/.bin
mv Your_File ~/.bin
export PATH=~/.bin:$PATH

add that last line to your .bashrc file as well

---

### Post by linux_noob0 on 2009-08-31
whoa... that was too fast :D!! thank you sooooo much!!
edit: awesome, both methods work well

---

### Post by gsocker on 2009-08-31
> export PATH=~/.bin:$PATH
For security reasons, it is **strongly** recommended that, in Linux/Unix, if the current directory or anything in your home directory is in your $PATH, that you add it to the **end** of the PATH variable, not the beginning. This prevents someone from tricking you into executing something you don't want to by naming something the same as a normal system executable.
Example:
Say /home/user/bin is at the beginning of your path.
Someone takes advantage of a Firefox vulnerability to save a disk wiping program as "/home/user/bin/ls" while you're browsing the web.
Guess what gets executed the next time you run ls?
Having user writable directories at the end prevents this.

---

