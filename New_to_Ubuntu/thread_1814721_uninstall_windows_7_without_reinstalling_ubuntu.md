---
title: "uninstall windows 7 without reinstalling ubuntu"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by arom2k11 on 2011-07-30
Hello and Good day to all...
I am planning to uninstall Windows 7 professional 64 bit and leaving behind Ubuntu 10.10 64 bit. But the problem is that I install Ubuntu using Wubi... Is there a way to completely uninstall Windows without damaging Ubuntu?

Thank you.

---

### Post by garvinrick4 on 2011-07-30
> **arom2k11 said:**
> Hello and Good day to all...
I am planning to uninstall Windows 7 professional 64 bit and leaving behind Ubuntu 10.10 64 bit. But the problem is that I install Ubuntu using Wubi... Is there a way to completely uninstall Windows without damaging Ubuntu?

Thank you.
Wubi install is a folder right next to Users in C: drive called Ubuntu and since it is in the 
Windows file system no it will go away with Windows if you uninstall Windows.

---

### Post by 2F4U on 2011-07-30
No, there isn't. Wubi installs Ubuntu inside the Windows partition and therefore, if you remove Windows you also remove Ubuntu.

---

### Post by coffeecat on 2011-07-30
The only way to achieve what you want would be to migrate the wubi installation to its own partition before removing Windows. See here:

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by arom2k11 on 2011-08-05
Thank you guys for your reply.
 
Well, I think I have to stick with the wubi for now. There are still some issues that I would like to learn in linux. By the way, could I post issues concerning Linux Mint here? I do have another computer dual booting Mint.
 
Again, thanks a lot.

---

### Post by coffeecat on 2011-08-05
> **arom2k11 said:**
> By the way, could I post issues concerning Linux Mint here? I do have another computer dual booting Mint.

The staff here generally discourage support threads for other Linux distros, redirecting people to the appropriate distro forum. This includes Mint. Although most versions of Mint are based on Ubuntu there are significant differences, and you will probably be better off in the Mint forum.

That being said, you could post in this subforum:

[http://ubuntuforums.org/forumdisplay.php?f=401](http://ubuntuforums.org/forumdisplay.php?f=401)

---

### Post by bodhi.zazen on 2011-08-05
Two or three general comments.

1. wubi is, IMO, to test Ubuntu. If you decide you want to stat with Linux, Ubuntu or otherwise, you should IMO migrate to a standard installation.

2. You can either do a fresh install, or move the wubi install as outlined in the link coffeecat gave you.

3. Please use the appropriate forums. This is the Ubuntu forums and while you may as general linux questions here, but, in order to encourage other communities to grow, please ask questions about or specific to Mint on the Mint forums.

The people on the Mint forums are very kind and competent and they are going to know more about Mint linux ;)

---

