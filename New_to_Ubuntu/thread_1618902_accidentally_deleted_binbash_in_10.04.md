---
title: "accidentally deleted bin/bash in 10.04"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by tonyescribex on 2010-11-11
Hi,
I accidentally deleted file /bin/bash.
Is there anyway to get the same copy of this /bin/bash file.
I appreciated for your help.

---

### Post by moody_mark on 2010-11-11
You can have my bash file, just put it back into /bin and it should be ok. Im running 10.04 64-bit so I imagine it should be ok. Make sure it has the right permissions

```
$ ls -la /bin/bash
-rwxr-xr-x 1 root root 934336 2010-04-19 03:16 /bin/bash

```

[ATTACH]175304[/ATTACH]

---

### Post by tonyescribex on 2010-11-11
Thank you Mark...
 
Tony

---

### Post by tonyescribex on 2010-11-11
Hello Mark,
 
I forgot that my OS is Ubuntu Server 10.04 - 32 bits.
 
So, do you have /bin/bash for 10.04 (32 bits)?
 
HELP.... Anybody.
 
Thanks,
Tony

---

### Post by moody_mark on 2010-11-11
Hey Tony, you could run up the live CD and copy the file to your hard drive from there or a USB stick?

---

### Post by Decatf on 2010-11-11
Or reinstall the package from here [http://packages.ubuntu.com/lucid/bash](http://packages.ubuntu.com/lucid/bash)

---

### Post by tonyescribex on 2010-11-12
Thank you Mark and Decatf,
 
I cannot retrieve the /bin/bash via both ways.
bin/bash is required so we can use shell commads. It kicks out immediately after I logged in.
I already did "apt-get install bash".
It said the package is upto date.
That's why I reboot the system and then that's why I cannot get back in.
 
I cannot retrieve 'bash' via Live CD either....
 
So, I decided to reinstall the 'ubuntu'.
 
Thank you very much for your time and help.
Tony

---

### Post by siddharth007 on 2013-01-03
To recover your bash follow these steps

1. remove your bash file (if present in /bin)

2. create a soft link
[B]ln -s /bin/sh /bin/bash
[/B]
3. Reinstall bash using apt-get command
apt-get install --reinstall bash

4. Close the terminal and open a new one again.Done!!!!

:guitar:

---

### Post by oldos2er on 2013-01-03
Old thread closed, please don't bump old threads.

---

