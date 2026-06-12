---
title: "Long Username shown in terminal"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Rog 3236 on 2011-06-05
[SIZE=2]When I set up my account in Ubuntu as a dual boot with Windows 7, I set my username, i.e. roger, automatically, after set up my computer was identified and now appears every time I access the terminal (see below). This is new to me. I have used Ubuntu running as an application within Windows and the -Inspiron-560s wasn't added. Seems to me this is rather cumbersome. I would like information as to why this was done? Can this be changed, if so what effect would it have?

roger[ampersand]roger-Inspiron-560s:~$ [/SIZE]

---

### Post by nothingspecial on 2011-06-05
roger-Inspiron-560s is the host name of your computer, your user name is just roger

---

### Post by nothingspecial on 2011-06-05
Sorry, re-read your post, to change it type this
```

 PS1='${debian_chroot:+($debian_chroot)}\u:\w\$'
```

That will remove the host name

To make that permanent

```
nano ~/.bashrc
```

find the line that says
```

 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$
```

and delete @\h  from it

Ctrl-O to save, then Enter

Ctrl-X to exit

Then type ```
. ~/.bashrc
``` to have it take effect.

---

### Post by Rog 3236 on 2011-06-05
Thanks for the expeditious help.
Roger

---

