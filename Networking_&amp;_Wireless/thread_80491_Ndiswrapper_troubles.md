---
title: "Ndiswrapper troubles"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by ril560 on 2005-10-22
Hi guys i have no clue what im doing to bear with me.
I recently installed ubuntu 5.10 onto my laptop and everything works fine, except that it didnt auto detect my netprism wireless card, so i decided to just install ndiswrapper. So, i searched the wiki and found HowToSetUpNdiswrapper.
Ive gotten to step 5 (Now you can set up your working Wlan device under Desktop->Administration->Networking) and have completely lost it.

im pretty sure that i installed the driver right and that the card is installed because i get these messages:

> 
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper (load_devices:479): Each driver can only support a single bustype
ndiswrapper (load_devices:479): Each driver can only support a single bustype
usbcore: registered new driver netprism
ndiswrapper: driver netprism (D-Link,07/17/2003, 3.0.8) added

and

> ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
netprism        driver present

---

