---
title: "btnx problems"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by dgub on 2009-09-20
I tried to configure my Cherry 7 button mouse yesterday. Just as I was halfway through it, it crashed bringing the whole computer down, so I abandoned it and returned to Windows to continue browsing.

Today I thought I would have another go at it but when I try to run it nothing happens. If I run it from terminal I get the following

```
dg@dg-desktop:~$ btnx
 btnx: uinput modprobed successfully.
 btnx: Opening config file: /etc/btnx/btnx_config_Default
 btnx: Could not read the config file: No such file or directory
 btnx: Configuration file error.

```

Checked and the file does not exist. Tried making a blank file but that is baulked by permisions.

No idea what to do here so could someone help please.

---

### Post by Liolikas on 2009-09-20
Find that file in:
your system
program homepage
google
...

---

### Post by dgub on 2009-09-20
> **Liolikas said:**
> Find that file in:
your system
program homepage
google
...

Thanks

I found a post that says "Remove the Manager" and that works. However having gone through the configuration the mouse buttons still do not respond.

---

### Post by falconindy on 2009-09-20
btnx broke with the release of 8.10. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=968530").

[Easystroke](http://sourceforge.net/projects/easystroke/) is another option, as well.

---

### Post by dgub on 2009-09-23
> **falconindy said:**
> btnx broke with the release of 8.10. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=968530").

[Easystroke](http://sourceforge.net/projects/easystroke/) is another option, as well.

Thanks for the reply.

I have managed to get btnx working. Shame it is not supported in later versions. Reckon I will just stay with 8.04 as I really don't fancy getting into scripting.

Tried mouse gestures in the past and don't really like them that much.

---

