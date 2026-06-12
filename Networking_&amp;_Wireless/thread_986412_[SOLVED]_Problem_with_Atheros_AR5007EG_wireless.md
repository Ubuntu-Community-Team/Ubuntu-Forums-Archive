---
title: "[SOLVED] Problem with Atheros AR5007EG wireless"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by sahil01 on 2008-11-18
I have a Toshiba Satellite A205-S5879 laptop with a Atheros AR5007EG Wireless network adapter. I am using ubuntu 8.10 and am quite new to it. I faced the common problem of not being able to get the wireless working and have tried many options (ndiswrapper, WICD, madwifi) but still no success. Needed help with the same. Thanks.

---

### Post by sahil01 on 2008-11-25
I switched to ubuntu 8.04 but still have the same problem.

---

### Post by carml on 2008-12-03
way is the one I followed,I suggest you if you feel better using the gui:
go to System->Administration->Synaptic and search for ndiswrapper.
The packages you have to install are those listed here

-ndisgtk
-ndiswrapper-common
-ndiswrapper-utils-1.9.
Doing so you install a program to load Windows driver for the wireless lan;you also need to download a driver like this Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL).
Once you have downloaded the drivers you have to disable the other drivers in System->Driver Hardware,they should to be :
- Atheros Hardware Access Layer (HAL)
-Support for Atheros 802.11 wireless LAN cards;
then reboot.
After you rebooted unzip(best would be on your Desktop or your home folder) the driver you first dowloaded, ,then go to System->Windows Wireless Driver,to access ndiswrapper.On the new window select "Install new driver",select the path where you unzipped the drivers and you've done.
An other to try to solve the problem is to follow the instructions submitted here:[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847).
Let me know if I've been unclear or I've helped you;if these ways don't function for you,you can always try others searching on the forum.):P

---

### Post by acreech on 2008-12-03
> **sahil01 said:**
> I have a Toshiba Satellite A205-S5879 laptop with a Atheros AR5007EG Wireless network adapter. I am using ubuntu 8.10 and am quite new to it. I faced the common problem of not being able to get the wireless working and have tried many options (ndiswrapper, WICD, madwifi) but still no success. Needed help with the same. Thanks.

[http://ubuntuforums.org/showthread.php?p=6201697#post6201697]("http://ubuntuforums.org/showthread.php?p=6201697#post6201697")

Have you tried the information on this post? It is the only way to get the wireless to work on my laptop. I have the Atheros AR5007EG on an Acer Aspire 7520 laptop.

---

### Post by sahil01 on 2008-12-08
Thanks acreech ! I finally got it to work !

---

### Post by acreech on 2008-12-08
> **sahil01 said:**
> Thanks acreech ! I finally got it to work !

Not a problem. Glad it worked for you. Since you started this thread..... if it is solved for you, you can mark it as solved in the thread tools at the top of the page. 

acreech

---

### Post by sahil01 on 2008-12-09
Thanks for letting me know about that as well !

sahil01

---

