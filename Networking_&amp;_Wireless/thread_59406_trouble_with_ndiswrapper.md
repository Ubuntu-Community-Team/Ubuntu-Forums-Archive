---
title: "trouble with ndiswrapper"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by bionnaki on 2005-08-23
greetings. I am trying to install ndiswrapper + the driver for my wmp54g wireless card. It is V4 and uses Ralink chipset.

I have followed the instructions here: [http://ubuntuforums.org/showthread.php?t=42193&highlight=wmp54g](http://ubuntuforums.org/showthread.php?t=42193&highlight=wmp54g)

as well as 

[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)

About a week ago (when I first installed Ubuntu) this was successful and I had an excellent internet connection. After making a mistake with my Ubuntu partition (while toying with my Win XP partition) I had to re-install Ubuntu and start over. No big deal.

The first thing I did was try to get my internet connection running. I havent had much luck the 2nd time.

I follow the instructions as presented by the SetupNdiswrapper Howto. The only difference is I am using Ndiswrapper 1.2 and the Ralink drivers (rt2500.sys). When I get to the part where I **modprobe ndiswrapper** I receive this error:

> root@ubuntu:~# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


I am not sure what to do. Should I modify my permissions? I do not recall having this error before...

I really appreciate your help. Switching back and forth between Ubuntu and XP just so I can go online is a headache.

Thanks!

---

### Post by bionnaki on 2005-08-23
success!

I searched the forums one more time and came across a solution I must have missed earlier. the problem appeared to have been an older version of ndiswrapper-utils. I removed them (and everything to do with ndiswrapper) and downloaded the updated versions.

worked perfectly.

---

