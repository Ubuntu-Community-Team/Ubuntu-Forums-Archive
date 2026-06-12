---
title: "problem with swap space!!!"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-02-22
I had allocated 510 MB of disk space for swap space in partition editor, but as u can see that sys monitr is showing 1.1 GB (which i had allocated when i was using intrepid but now working on ultimate) and not even a fraction of bit is engaged for paging process. I know that it can be solved by updating some file but don't know which commands and where those files are located.

please guide me........Thank you...:)

---

### Post by blueridgedog on 2009-02-22
Do you have two hard drives?  

What happens when you try:

```
sudo swapon /dev/sda2
```

---

### Post by eshant_engineer on 2009-02-23
This is the o/p
> swapon: /dev/sda2: Device or resource busy


---

### Post by xeth_delta on 2009-02-23
I might not be reading correctly your question, but will try to venture some insight.

Linux will not use the swap unless it is absolutely necessary (seap is way way slower), i.e. your system runs out of free physical memory. Until then, it will use only RAM.
From what I can see your system still has a lot of free RAM, Hence 0 MB of swap are being used.

What confuses me though, is that your swap partition seems to have been created with approx. 500 MB, while in the System Monitor it shows as approx. 1 GB.

---

### Post by eshant_engineer on 2009-02-24
I earlier asked abt files, actually i forgot that file name, but it may be problem with UUID, so i want to know that file where UUID is defined.

---

### Post by Simbo on 2009-02-24
/etc/fstab

or

type blkid (in a terminal window).

---

### Post by eshant_engineer on 2009-02-24
where i can get the right UUID?

---

### Post by blueridgedog on 2009-02-24
The command:

```
blkid /dev/device
```

Such as:

```
james@Ripstop:~$ blkid /dev/sda1
/dev/sda1: TYPE="swap" UUID="aa6d27c8-89cb-4cc3-842a-ab40cc18e3a5" 
```

---

### Post by ibuclaw on 2009-02-24
What does this output?
```
cat /proc/sys/vm/swappiness
```
A number close to 0 means that Linux is favouring your RAM, which it should, as RAM has quicker access than Disk, and you have 2GBs of RAM free for you to use!

A number closer to 100 means that Linux is favouring your swap more.

By default, I believe the number should be 40, unless otherwise tweaked to increase performance, one way or the other...

[EDIT]
On my machine, for whatever reason, the swappiness is set to 60.
And in the picture attached is my RAM/Swap usage. :)

Regards
Iain

---

### Post by eshant_engineer on 2009-02-24
No, in my case also it is showing 60. But abt what tweak u r talking about?
I will implement them to increase performance....:guitar:

---

### Post by zika on 2009-02-24
> **eshant_engineer said:**
> No, in my case also it is showing 60. But abt what tweak u r talking about?I will implement them to increase performance....:guitar:
from Your post we can see that You do not use swap, You have enough memory so any tweaking around swappiness **will not** make any difference. 60 is default. only once You start using the swap You could see a difference. not for better, of course ... ;)
You might see a performance increase by using tmpfs for /tmp, since You have, at least at the time screen-shot was taken, enough memory but that is another story ... I do not want to get warned that I'm hijacking the thread ... ;)

---

### Post by eshant_engineer on 2009-02-25
> **zika said:**
> 
You might see a performance increase by using tmpfs for /tmp, since You have, at least at the time screen-shot was taken, enough memory but that is another story ... I do not want to get warned that I'm hijacking the thread ... ;)

How? Since i am asking under Ab beginner talk, i m a newbie, So, u please clear it...

---

### Post by ibuclaw on 2009-02-25
Although there is no problem using a tmpfs filesystem for the /tmp directory, you may experience problems if you try to manually install an application that extracts, say 4GBs of data into the directory (ie: Quake3 for Linux).

But, other than that small hint, there is no reason why you shouldn't.

To mount /tmp as a tmpfs filesystem (so it sits in memory, rather than on harddisk), edit the /etc/fstab file
```
sudo gedit /etc/fstab
```
and put this at the bottom
```
# tmpfs
tmpfs           /tmp            tmpfs    defaults        0        0

```
Save, quit, and reboot.


Regards
Iain

---

### Post by zika on 2009-02-25
> **eshant_engineer said:**
> How? Since i am asking under Ab beginner talk, i m a newbie, So, u please clear it...
easy. I added this line to my */etc/fstab*```
tmpfs /tmp tmpfs defaults 0 0
```and, then, in FF, under *about:config*, I added variable named **browser.cache.disk.parent_directory** (type=string) and set it to */tmp*.

that way, *Cache* directory that FF uses is in /tmp and, since it is tmpfs (file-system), it is in memory (sort of ramdisk in Windows, or, better, in DOS) and is is faster and gets erased every time I reboot or shutdown. at first usage it is good to flush a cache in FF in order to clear the stuff from disk. also, original *Cache* directory on disk can be removed.

lots of other stuff can be put on tmpfs ... ;) (thanks adamlau [http://ubuntuforums.org/showpost.php?p=6703563&postcount=15](http://ubuntuforums.org/showpost.php?p=6703563&postcount=15) []("http://ubuntuforums.org/showpost.php?p=6797728&postcount=13") :) )

**please, since You are a newbie, as You state, take this advice with a grain of salt and be careful. make a note of every change in Your important files and backup. /etc/fstab is very important file.**

---

