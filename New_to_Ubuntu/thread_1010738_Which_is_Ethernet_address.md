---
title: "Which is Ethernet address?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-12-14
Ok, I need to find out my Ethernet address.
Typed in the right command in the terminal but get two HWaddr.

One in the ath0 section and one in the eth0.

Which is the right one?

thanks

---

### Post by HotShotDJ on 2008-12-14
> **highlyevolved said:**
> Ok, I need to find out my Ethernet address.
Typed in the right command in the terminal but get two HWaddr.

One in the ath0 section and one in the eth0.

Which is the right one?I shall assume that by "Ethernet address" that you are trying to get your IP address (inet addr when you type ifconfig in a terminal).  You should only be getting one.  HWaddr is showing you the mac address of the hardware in your machine.  Apparently you have both an Ethernet controller and a Wireless controller.  Only one of them should be giving you an internet address.

---

### Post by highlyevolved on 2008-12-14
I mean The MAC address

---

### Post by HotShotDJ on 2008-12-14
> **highlyevolved said:**
> I mean The MAC addressOk... That is the HWaddress.  eth0 is the one for your ethernet card.

---

### Post by highlyevolved on 2008-12-14
> **HotShotDJ said:**
> Ok... That is the HWaddress.  eth0 is the one for your ethernet card.

So use the HWaddr in the atho0 section?

---

### Post by superprash2003 on 2008-12-14
post your ifconfig output.. would be easier..

---

### Post by HotShotDJ on 2008-12-14
> **highlyevolved said:**
> So use the HWaddr in the atho0 section?
If you are looking for the Mac address of your Wireless card, then use ath0.  If you want the Mac address of your Ethernet card, then use eth0.  Since I'm not sure exactly what you are trying to do, I can't really offer much more than that.

---

### Post by highlyevolved on 2008-12-14
It's on a different comp with no net but this is the short of it.

atho - Link encap: Ethernet HWaddr:00:16:e3:64:c2:00


OR

etho0 -Link encap: Ethernet HWaddr 00:0e:7b:9b:b5:97

---

### Post by Nepherte on 2008-12-14
etho0 -Link encap: Ethernet HWaddr **00:0e:7b:9b:b5:97**

---

