---
title: "How to do setenv DISPLAY :0 ?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Cesaar on 2009-05-28
Hello, I'm using Ubuntu 9.04. I am trying to get the Libero IDE from Actel running but I'm running into problems. I found an install instructions pdf online saying how to get it running. It points out possible quirks. One of them is, when launching Libero, i get ```
Wind/U X-toolkit Error: wuDisplay: Can't open display
``` The instructions say that in such case to do the following:> Set the $DISPLAY environment variable to:0 using the command
  ```
setenv DISPLAY :0
```


I'm not sure if it's telling me to do this on a terminal. When I do run this command in the Terminal I get this error: ```
bash: setenv: command not found
```

If any body could give me some pointers it would make me happy Ü
Thanks

---

### Post by Didius Falco on 2009-05-28
Hi,

Have a read through this thread - it's a little old, but it should still apply:

[http://ubuntuforums.org/showthread.php?t=2793&page=2](http://ubuntuforums.org/showthread.php?t=2793&page=2)

I hope it helps...

Regards,

Didius

---

### Post by kpkeerthi on 2009-05-28
```
DISPLAY=:0 /whatever/command/you/want/to/run.sh
```

---

### Post by Cesaar on 2009-06-29
> **kpkeerthi said:**
> ```
DISPLAY=:0 /whatever/command/you/want/to/run.sh
```

Thanks kpkeerthi, that does the work. :)

---

