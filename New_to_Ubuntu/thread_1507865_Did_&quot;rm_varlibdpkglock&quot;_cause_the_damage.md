---
title: "Did &quot;rm /var/lib/dpkg/lock&quot; cause the damage?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by spai on 2010-06-12
Hello all,

The following is a snapshot of what I did :confused:

```
srikanth@spai-laptop:~$ sudo apt-get install vinagre
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
srikanth@spai-laptop:~$ sudo rm /var/lib/dpkg/lock 
srikanth@spai-laptop:~$ sudo apt-get install vinagre
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
srikanth@spai-laptop:~$ sudo dpkg --configure -a
Setting up ttf-mscorefonts-installer (3.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer

```

I shouldnt have removed the lock file... what do I do?
Do I reinstall dpkg?

---

### Post by llawwehttam on 2010-06-12
Have you tried turning it off and on again?

---

### Post by spai on 2010-06-12
I rebooted my system. I used synaptic to install vba. But the installer tries to intall ttf-mscore-fonts from various sourceforge.net places and fails. What do I do? I do not whether this is related to the original problem. I never faced problems like this before!

By the way, the following error still exists:

```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ttf-mscorefonts-installer (--configure):
```

---

### Post by Soul-Sing on 2010-06-12
after sudo rm /var/lib/dpkg/lock 
you should kill/close all -apt/dpkg/software managers

and do a simple: ```
sudo apt-get update
```

you did
srikanth@spai-laptop:~$ sudo rm /var/lib/dpkg/lock 
srikanth@spai-laptop:~$ sudo apt-get install vinagre
 thats impossible.

---

### Post by SRST Technologies on 2010-06-12
Oh dear.  I don't know who told you to use the command line to remove the lock, but yes, it causes damage.  It causes so much damage to your computer that the only way to fix it is to install Windows and use that for the rest of your life even if you get another computer.

---

### Post by -kg- on 2010-06-12
@ SRST Technologies:

Just so you know, I think that comment was completely inappropriate and uncalled for.

Either help, or ***_don't post_!***

---

### Post by bapoumba on 2010-06-12
> **SRST Technologies said:**
> Oh dear.  I don't know who told you to use the command line to remove the lock, but yes, it causes damage.  It causes so much damage to your computer that the only way to fix it is to install Windows and use that for the rest of your life even if you get another computer.

Removing the lock can be useful at times, when no other package manager is running. A simple reboot usually clear things up in that case too.

---

### Post by MichealH on 2010-06-12
I agree. I have removed APT lock plenty of times when It had done but not removed the lock. I just remove the lock and carry on. It recreates itself

---

