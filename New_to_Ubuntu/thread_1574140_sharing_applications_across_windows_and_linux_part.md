---
title: "sharing applications across windows and linux partitions"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by trinityclare on 2010-09-13
This is more of a question than a problem, but here's the situation:

I have a laptop with three main partitions -- 100GB Windows 7, 100GB Ubuntu 10.04, and a 300GB FAT32 shared partition. Is there a way for me to install applications to the shared partition and have them be usable in both OSes? For example if I install something to the shared drive using Wine, will Windows be able to run it? The answer is probably no, but I thought I would ask. (The apps in question are [MediaMonkey]("http://www.mediamonkey.com/") and Photoshop.)

---

### Post by rockerphil on 2010-09-13
it seems possible so long as you install the program in Windows first seeing as Wine installs a program to the ~/.wine/drive_c/Program Files folder in your home partition which isn't natively readable by Windows (at least without the ext2IFS application) and since Ubuntu uses ext4 by default it makes it completely unreadable by Windows. so in this case i'd boot the Windows OS and install the program from there and choose the drive you want to install it to (in this case the FAT32 drive) so that it can be accessed by the Ubuntu install and ran through Wine. please feel free to report back here with any bugs or quirks.

hope this helps,

Phil

---

### Post by Mark Phelps on 2010-09-14
> **trinityclare said:**
> ...For example if I install something to the shared drive using Wine, will Windows be able to run it? The answer is probably no, but I thought I would ask. 

I think that you're right -- the answer is most likely no.

When you install an MS Window app, it loads stuff into the registry.  Your MS Windows install and your Wine install do not share registries -- each has its own.

So, when you're in Wine, you don't see the MS Windows registry; when you're in MS Windows, you don't see the Wine registry.

But, it's worth trying to see if it DOES work.

---

### Post by Jazzy_Jeff on 2010-09-14
Install it through Windows first and then you should be able to launch the .exe file by right clicking on it and tell it to use Wine. I have done this in the past with games. Not sure if it will work with other programs though. Try and experiment with it.

---

### Post by trinityclare on 2010-09-14
It seems to be working so far. Wine launches the .exe file perfectly, now all that's left is finding out if it remembers settings from one session to another.

---

