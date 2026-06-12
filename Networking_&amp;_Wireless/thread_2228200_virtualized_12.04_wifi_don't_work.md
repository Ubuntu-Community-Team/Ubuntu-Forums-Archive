---
title: "virtualized 12.04 wifi don't work"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by cris_1986 on 2014-06-06
I am using an Asus K56C notebook with windows 8. I have virtual box with Ubuntu 12.04 lts. In the host when I use the wifi connection the guest can't connect, he lost the connection. But when in the host I use the wired connection in the guest I have no problem.

Can you help me?

---

### Post by TheFu on 2014-06-06
The actual physical connection doesn't matter to the guestOS.   Have you setup both the wired and wifi connections inside the VM settings (click advanced to select the hostOS network adapter) and enabled "cable connect" for both?  Inside the guest, both should be emulated with either a PRO/1000 or virtio adapter, regardless.

Having both connected concurrently in the hostOS can be problematic inside the guests - check the routing inside the guestOS carefully to ensure wired connections have higher priority (lower metrics numbers) than the wifi link does.

---

### Post by cris_1986 on 2014-06-06
In the host I have try to disable the wired connection. So now in the guest I have only the wifi connection, but don't work.

---

### Post by TheFu on 2014-06-06
Can you show the settings, including advanced, please?  It isn't that we don't believe you, but ... 

BTW, if the wifi connection doesn't work on the hostOS, it won't work on the guestOS.  You are using Bridge Mode, right?

---

### Post by cris_1986 on 2014-06-06
In the Host the wifi works fine. I'm using bridge mode.
[ATTACH=CONFIG]253776[/ATTACH][ATTACH]253777[/ATTACH]

---

### Post by cris_1986 on 2014-06-06
[ATTACH=CONFIG]253778[/ATTACH]In the Host the wifi works fine. I'm using bridge mode.
[ATTACH=CONFIG]253776[/ATTACH][ATTACH]253777[/ATTACH]

---

### Post by TheFu on 2014-06-06
Doesn't the interface need to be active - the top checkbox? My Italian is non-existent. ;)
Also - the wired connection should be on NIC-1, the wifi connection on NIC-2 - the next tab over.  Does this make sense?

---

### Post by cris_1986 on 2014-06-06
The top checkbox is the enable/disable flag. So in my case is not enabled. The wired connection is in the NIC-1(disabled). The wifi connection is in the NIC-2(enabled). The next tabs (NIC-3,NIC-4) are over.

---

### Post by TheFu on 2014-06-06
Can you please post an image of the 2nd tab for NIC-2?

---

### Post by cris_1986 on 2014-06-06
[ATTACH=CONFIG]253779[/ATTACH]

---

### Post by TheFu on 2014-06-06
> **cris_1986 said:**
> [ATTACH=CONFIG]253779[/ATTACH]

Ouch - I got nothing to help now.  It all looks good to me, sorry.

---

### Post by cris_1986 on 2014-06-06
i have switched from bridge to NAT. now it works

---

