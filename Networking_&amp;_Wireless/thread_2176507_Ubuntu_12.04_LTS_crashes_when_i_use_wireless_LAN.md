---
title: "Ubuntu 12.04 LTS crashes when i use wireless LAN"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by irshsheikh on 2013-09-24
Hi,
I am new to the Ubuntu OS. A few days ago, I have downloaded 12.04 LTS version. Till yesterday i  had problems with the wirless  driver. The info of the driver is:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
        Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
```


today on September 25,2013. I tried to reinstall the Ubuntu 12.04LTS  again.  Immediately i got updates which i guess new kernal version was  included. I installed all the updates. the good thing happend was the  wirless worked smoothly for sometime.

the kernal version on my pc is as follows:

```
Linux dream-86 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linu
```

The new problem happend after the update . The operating system crashes  after i use the internet though wirless. once i open a browser  a black  screen comes and shows a big messages: like "Panic occured " and the  last line :"Switching back to text console".

I tried many things and i found  2 facts:
1) when i use the ethernet cable to use internet. the system works fine.
2) when i remove the ethernet cable and try to use the wirelss LAN, after a min or two, the system crashes..

i have attached the image of the error. please have a look

Please Help: i have been searching the solutions from last 5 days and various times i had to reinstall the OS.
thank you again

---

### Post by Hadaka on 2013-09-24
Hi, please make a wired connection to the internet
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
and..
```
sudo apt get install firmware-b43-lpphy-installer
sudo modprobe b43
```
thanks

---

### Post by irshsheikh on 2013-09-25
@ [COLOR=#000000]**Hadaka , Thank you so much. It works.**[/COLOR]

---

### Post by Hadaka on 2013-09-25
GREAT !!, glad that worked for you.
please mark your thread solved.
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

