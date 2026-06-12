---
title: "how to compile c and ncurses code in ubuntu linux?"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by mac73 on 2006-07-19
hi guys

iwant to compile c code in ubuntu linux, bt unable to do so.
i tried gcc command but it is givin d msg dat  
         
                 comman not found

pls help me.

and if possible also give detail in formation 4 configuring SAMBA server.
right from d start as i want to share home directory in MSHOME domain.

also commands to add user n 4 everything.

pls..............
tnx

---

### Post by x64Jimbo on 2006-07-19
I'm not sure what the second half of your post is asking, but I can tell you that you will need to install gcc
sudo aptitude install gcc

---

### Post by OpsVentus on 2006-07-19
For the compiling install the "build-essentials".
For the Samba server install the samba-server.

How to do this, try the search button. This is coverd many times befor and there are howto's on this.

Good luck,
Bart.

Howto on samba: [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+server+howto](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+server+howto)

ps. gcc isn't enough to compile a program.

---

### Post by mogelhead on 2006-07-19
As for ncurses I think you should install libncurses5-dev. Type this in a terminal:
```
sudo apt-get install libncurses5-dev
```

---

