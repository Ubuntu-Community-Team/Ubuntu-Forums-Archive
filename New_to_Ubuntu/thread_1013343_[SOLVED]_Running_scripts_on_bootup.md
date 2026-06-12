---
title: "[SOLVED] Running scripts on bootup"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Maverick1712 on 2008-12-16
If I have a file with a bunch of commands in it, what are the steps i need to take to make this executable, and further, where should I place this file to have it execute on bootup?

Cheers,
Adam

---

### Post by eraker on 2008-12-16
There are different runlevels in linux, representing different running states (standard, reboot, shutdown, custom, etc.). You can figure out which runlevel you're running by just typing "runlevel" into a terminal. 

Unless you did some custom stuff, you're probably in runlevel 2, which means that the scripts that run on startup are all symlinks in the directory /etc/rc2.d, and they're all named something like S[2-digit #]. (try ls /etc/rc2.d/ to see.)

Thus, one way to do this would be make your script executable: ```
chmod u+x yourscript
```

Then to add a symlink to it in the rc2.d folder using "S" and then making it the LAST number in there, unless something else depends upon your script and it needs to run first.

Depending on the script itself and what you're doing, however, this could be a bad idea.

---

### Post by eraker on 2008-12-16
Here's a better, simpler description of the same process:

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by Maverick1712 on 2008-12-16
Thanks eraker.

This is just a script to start my wireless on my server, so this should work just fine.

Cheers,
Adam

---

