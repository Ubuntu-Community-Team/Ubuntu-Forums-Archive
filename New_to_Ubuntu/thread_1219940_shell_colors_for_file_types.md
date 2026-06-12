---
title: "shell: colors for file types"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by shaheru on 2009-07-22
Hello,
I would like to have colors in my shell that describe different file types, but when I type "ls", no colors appear for directory, executable and so on. Is there an easy way to change this parameters? It is working fine when I am super user, but I would like to have it also as simple user,

Thanks!

---

### Post by kpkeerthi on 2009-07-22
Test with:
```

ls --color=auto

```
If the above works, setup a bash alias in ~/.bashrc

```

gedit ~/.bashrc

```
Add this line to the end of the file:
```

alias ls='ls --color=auto'

```

Relaunch your terminal window.

---

### Post by shaheru on 2009-07-22
Thanks, it is working well!

---

