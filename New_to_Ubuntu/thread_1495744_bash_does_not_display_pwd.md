---
title: "bash does not display pwd"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by abraxas334 on 2010-05-28
Hi,
this is a really silly question and i didn't really know how to look for this on interwebnet so here it goes.
on my lovely ubuntu computer when i am using my shell I always know in which working directory I am at.
so say```
 username@computername:/etc$ 
```and then you can just do your usual stuff. When I log into a remote computer (don't think it is running ubuntu)all i get is this:

```
-bash-3.2$
``` I would like it to tell me my working direcotry too. I there an easy fix to that?

---

### Post by nmaster on 2010-05-28
you need to change the .bashrc file on the remote machine.  you should look at the file you have locally and make the changes that you want accordingly.

in particular you need to add $PWD to the variable PS1.  for example from my ~/.bashrc file, ```
  PS1='${debian_chroot:+($debian_chroot)}\u@\h:$PWD \n$ '
```

leave out anything dealing with debian of course if its not a debian system. you can figure out more stuff by googling .bashrc

---

### Post by gmargo on 2010-05-28
The primary prompt is controlled by the shell variable $PS1.  This is normally set in your $HOME/.bashrc.  The default value for PS1 is '\s-\v\$ ' which translates to the "bash-3.2$ " prompt that you saw.  So the destination account either does not have a $HOME/.bashrc file or the PS1 variable is not set within it.  Read the bash man page and search for PS1 for more info.

---

### Post by abraxas334 on 2010-05-28
Thanks gmargo and neal.m.master this info was very useful!

---

