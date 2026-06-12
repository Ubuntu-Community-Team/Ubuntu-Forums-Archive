---
title: "Root user"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Phantom7777 on 2009-07-18
Please help. I want to install NVIDIA drivers, but must access the root account user. 
How do I access the root account???
:confused:

---

### Post by philcamlin on 2009-07-18
sudo is root 

so if you want to install something from terminal you type 

sudo apt-get install *package name goes here*

:popcorn:

---

### Post by Phantom7777 on 2009-07-18
I download the drivers from NVIDIA website, and shows I must use the "sh" command. It works, but must do it on root.

---

### Post by doas777 on 2009-07-18
just use 
```
sudo sh ./<filename>
or
sudo . ./<filename>

```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by barkej on 2009-07-18
type sudo before the command.

---

### Post by jeppewinther on 2009-07-18
Sudo is the command that tells your box to run the following command as a superuser, or root.

So in order to install your NVIDIA drivers you will need to run the command:

sudo sh NVIDIA-numbersandstuff.run

By the way, it might be a better alternative to use the built-in installer that comes with Ubuntu if you aren't that comfortable with the command line stuff.

One guide can be found here: [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by philcamlin on 2009-07-18
oh its not in sinaptic i see what your saying

do you see a folder with files in it and a file called install.sh ?

[http://ubuntuforums.org/archive/index.php/t-412044.html](http://ubuntuforums.org/archive/index.php/t-412044.html)

---

### Post by Phantom7777 on 2009-07-18
Thank you, it work!!!! :D I'll will remember sudo!!!

---

### Post by overdrank on 2009-07-18
> **Phantom7777 said:**
> Thank you, it work!!!! :D I'll will remember sudo!!!

[RootSudo]("https://help.ubuntu.com/community/RootSudo"):D

---

