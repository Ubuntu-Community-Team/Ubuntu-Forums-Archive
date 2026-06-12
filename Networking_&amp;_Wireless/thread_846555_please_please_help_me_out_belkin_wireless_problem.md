---
title: "please please help me out belkin wireless problem"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by ronitakon27 on 2008-07-01
hello every one.

here is my problem 
sure you can solve it because it is so noob.

i have only one question

PLEASE CAN ANY ONE MAKE MY WIRELESS BELKIN USB WORK? 


details


1.	computer with dual boot  vista(has net)(which ofcourse is not a problem) and ubuntu 8.04(no net)

2.	belkin wireless f5d7051

3.	kernel number  	2.6.24-16-generic

4.	ndiswrapper-common_1.50-1ubuntu1_all  ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64

5.	belkin driver windows xp (+ cd also)

6.




my --------


i felt the magic of ubuntu before i even installed it

but didnt know it was so hard (for me....)
    but hey willing to learn

I spend my five days sitting infront of computer tryna find something to get it work
(but found none)
probably finished every how to about this problem 
please help me out

thank you


codes
```

root@ronitakon27-desktop:~# ndiswrapper -i /home/ronitakon27/Desktop/abc/BCMRNDIS.INF

installing bcmrndis ...

forcing parameter IBSSGMode from 0 to 2

forcing parameter IBSSGMode from 0 to 2

root@ronitakon27-desktop:~# ndiswrapper -l

bcmrndis : invalid driver!

root@ronitakon27-desktop:~# iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.

root@ronitakon27-desktop:~# lsb
_release -a
No LSB modules are available.

Distributor ID: Ubuntu
Description:   
 Ubuntu 8.04
Release:   
     8.04
Codename:       hardy

root@ronitakon27-desktop:~# 

root@ronitakon27-desktop:~#  uname -r

2.6.24-16-generic

root@ronitakon27-desktop:~# 





 
```

---

