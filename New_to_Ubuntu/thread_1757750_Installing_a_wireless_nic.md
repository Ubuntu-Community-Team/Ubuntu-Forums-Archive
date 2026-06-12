---
title: "Installing a wireless nic"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by nzashadow on 2011-05-13
Hello, I'm trying to install ubuntu 11.04 onto my tower and it's working fine except I am having trouble with my wireless nic.

Using lspci -nn command in terminal, it says my network controller is: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 010)

Also on the antenna it says WN311b

On the network manager under wireless networks it states: device not ready (firmware missing)


When I ran the live CD on the tower, it detected the proprietary driver, and let me install it. However after the installation it is not detecting the driver at all, which has left me a little confused.

I installed Ubuntu 11.04 alongside Windows 7, for dual boot, and both are 64bit.

Any help would be appreciated, thank you.

---

### Post by TeoBigusGeekus on 2011-05-13
Try this
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by nzashadow on 2011-05-13
> **TeoBigusGeekus said:**
> Try this
```
sudo apt-get install bcmwl-kernel-source
```

"E: Unable to locate package bcmwl-kernel-source"

I think I may not have mentioned that I do not have any internet connection on the computer in trial here.

---

### Post by BertN45 on 2011-05-13
Probably you can find the driver on your Ubuntu cd

---

### Post by irv on 2011-05-13
If you have the capability of plugging in a cable to get on the Internet then do so otherwise you need to use the CD. Then go to the following thread and follow the last post. There is a problem with the 43xx Broadcom card. This worked for me.
[http://ubuntuforums.org/showthread.php?t=1742147&page=4]("http://ubuntuforums.org/showthread.php?t=1742147&page=4")

---

### Post by nzashadow on 2011-05-13
My only source of internet where I am at is through wi-fi, so I can't set up a wired connection.

I'm also not familiar with how to use the cd how y'all are implying. Also following the instructions on the link I consistently get

 E: Unable to locate package...

I tried to mount my cd in the synaptic package manager and it states:

E:Unable to stat the mount point /media/cdrom/-stat (2: No such file or directory)
E:Unable to stat the mount point /media/cdrom/ -stat (2:No such file or directory)
E:Failed to mount the cdrom.

---

### Post by irv on 2011-05-13
You need to go to the Synaptic Package Manager then goto Settings> Repository> and on the Ubuntu Software tap make sure you put a check mark in the box next to CD. See screen shot:
This will install packages from the CD. When you get on the Internet you will want to remove the check mark.
[ATTACH]192074[/ATTACH]

---

### Post by wildmanne39 on 2011-05-13
> **irv said:**
> You need to go to the Synaptic Package Manager then goto Settings> Repository> and on the Ubuntu Software tap make sure you put a check mark in the box next to CD. See screen shot:
This will install packages from the CD. When you get on the Internet you will want to remove the check mark.
[ATTACH]192074[/ATTACH]

HI, thats a nice tutorial on your laptop.:)

---

### Post by nzashadow on 2011-05-13
Alright guys, thanks very very much. I got it working :D !!!!!!!!!!!!!!!!


The community here is very helpful thank you :)

---

### Post by wildmanne39 on 2011-05-13
> **nzashadow said:**
> Alright guys, thanks very very much. I got it working :D !!!!!!!!!!!!!!!!


The community here is very helpful thank you :)

Thats great please mark this thread as solved by going to the threads tool as the top of the patch and clicking on it.:D):P

---

### Post by irv on 2011-05-14
[attach]192098[/attach]

---

