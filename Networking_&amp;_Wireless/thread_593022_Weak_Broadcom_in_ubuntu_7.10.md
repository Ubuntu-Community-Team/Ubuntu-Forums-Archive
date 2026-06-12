---
title: "Weak Broadcom in ubuntu 7.10?"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by daleus on 2007-10-26
I am using Ubuntu 7.10 (final) on my laptop (A Dell Inspiron 1501)

I have installed the WiFi card using restricted-manager (which works).

The card works fine, but at a friends house when using his desk I can use his wireless connection just fine in Windows (albeit 1 bar of signal) and can even use it for playing World of Warcraft (and it's generally fine, despite low signal). However in ubuntu I can only see this Access Point, I can not connect unless I am physically (a lot) closer than I need to be when booted into Windows.

I had a quick search of 'the google' and these forums but couldn't find anything directly matching what I was looking for.

So basically, does anyone know a way to make me able to connect to weak access points in ubuntu, I know the card can do it as it works in Windows. I thought about turning down noise tolerances or similar, but I have no idea how to do it.

---

### Post by kevdog on 2007-10-26
Try installing your drivers with ndiswrapper -- just for a comparative test. At least you have a second option (look at it that way)!!

---

### Post by daleus on 2007-10-27
It is exactly the same. I will reinstall again just to make sure.

---

### Post by xpilesx on 2007-10-30
i'm having the exact same issue...any help would be great

---

### Post by Ossus on 2007-10-30
I have the exact same issue with my Dell laptop running a Broadcom BCM94311MCG wlan mini-PCI. 

I know this started when I upgraded to Gutsy Gibbon. 

I also know that when I boot into windows, I don't have this problem.

Any Ideas?

Ossus

---

### Post by daleus on 2007-11-03
Just an update :-

I can *see* the network at the same range, but at this range Windows WILL connect, whereas Ubuntu will just seemingly connect forever. Also if I connect and MOVE TO that place I am apparntly still connected, but no network connections work. Windows is fine with this.

---

### Post by kevdog on 2007-11-03
Did you try ndiswrapper??

---

### Post by DavidTangye on 2007-11-03
I have the same problem with Feisty vs Windows, dual-booting on the same machine. I am wirelessing across the fence into the neighbours house. With Firefox-Windoze all websites work. With Firefox-Ubuntu some do not. Ftp works fine with both. I am wondering if its a 'Quality Of Service' sort of thing?  I think I have narrowed the problem down to Ubuntu not driving the wireless card with as much power as the Windoze driver does. I cant remember which wireless driver I am using under Ubuntu, native or via ndiswrapper. I shall check later.

---

### Post by xpilesx on 2007-11-04
this is definitely an issue that needs looking into...i am sitting 2 feet away from my router and it says the signal is 75%...what's with this...is there any way to boost the power to wireless adapter or something,,,i think i might have read that can help gain more signal

---

### Post by Ossus on 2007-11-04
I just disabled and blacklisted the 43xx firmware and started up NDISwrapper again. From what I can tell, there is no noticeable difference, in fact it might be worse, but I don't have any empirical way of determining that.

Ossus

---

### Post by pinow on 2007-12-10
This is an old thread, but I'm having the same problem. Very low signal, slow connection.
In Vista my connection is superb, router is only 4m away.

Has this been fixed meanwhile?

---

### Post by redDEADresolve on 2007-12-11
[http://www.ubuntu1501.com/2007/06/ubuntu-gutsy-gibbon-710-new-user-guides.html](http://www.ubuntu1501.com/2007/06/ubuntu-gutsy-gibbon-710-new-user-guides.html)

You have two options for wifi

ndiswrapper can connect to networks that the restricted driver can and works at full speed.

---

### Post by pinow on 2007-12-18
> **redDEADresolve said:**
> [http://www.ubuntu1501.com/2007/06/ubuntu-gutsy-gibbon-710-new-user-guides.html](http://www.ubuntu1501.com/2007/06/ubuntu-gutsy-gibbon-710-new-user-guides.html)

You have two options for wifi

ndiswrapper can connect to networks that the restricted driver can and works at full speed.
I installed ndiswrapper using this:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29)

Now it works much better and faster :)

---

### Post by berthiggins on 2007-12-18
I have a broadcom card and my network is much faster using ndiswrapper which is a shame as I would rather use the native/foss driver I shall continue to try the foss drive periodically and when it is up to speed I shall change.
The broadcom driver is great work but still has some rough edges

---

