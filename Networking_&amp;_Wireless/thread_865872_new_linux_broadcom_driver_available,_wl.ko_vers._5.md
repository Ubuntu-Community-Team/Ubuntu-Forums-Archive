---
title: "new linux broadcom driver available, wl.ko vers. 5.10.27.6"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by hpnux on 2008-07-21
Hello, 

i am new to ubuntu and have a hp with broadcom wireless card. 

i did find some guides about the b43 module with seems to work very well. 
i also found this driver for linux on the broadcom website

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

this seems very new, does anyone have experience with this driver ?

---

### Post by Ayuthia on 2008-07-21
Reading some of the posts in the forum, it seems to work ok if you don't have encryption on your router (WEP/WPA).  According to the README.TXT file, the driver only works for the 14e4:4315 device.

Ubuntu does include this wl driver in the linux-restricted-modules package and, if I recall correctly, if you have the correct chipset, lshw -C network would say that it is trying to use that driver.

---

### Post by rrm3 on 2008-07-21
This driver runs the wireless card in my HP Pavilion dv2815nr.  I'm not sure if the version above is the same version Ubuntu is currently using, but they both appear to work.

04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 137c

---

### Post by rrm3 on 2008-07-21
The wl included with Hardy atm is 5.10.18.0, so this is indeed an update.

---

### Post by linux_zindabad on 2009-03-01
This Driver works perfectly. It is also installed by dell in the dell studio 1535 n series. 


> **hpnux said:**
> Hello, 

i am new to ubuntu and have a hp with broadcom wireless card. 

i did find some guides about the b43 module with seems to work very well. 
i also found this driver for linux on the broadcom website

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

this seems very new, does anyone have experience with this driver ?

---

### Post by jordan420 on 2009-05-01
hey guys, does anybody know why i cant compile this driver in the 2.6.30RC kernel?

---

### Post by Ayuthia on 2009-05-01
> **jordan420 said:**
> hey guys, does anybody know why i cant compile this driver in the 2.6.30RC kernel?

There are probably some changes in the 2.6.30 kernel that the wl source will need to be patched.

You might try this one:
[http://bugs.gentoo.org/attachment.cgi?id=189250](http://bugs.gentoo.org/attachment.cgi?id=189250)

You will need to save it as a .patch file.  From the information in this patch, it looks like the 802.11 library changed location and names again.

I have not tested this so I am not for sure if it is the right patch or not.  It comes from:
[http://bugs.gentoo.org/show_bug.cgi?id=248450](http://bugs.gentoo.org/show_bug.cgi?id=248450)

If you know what you are doing, you can try it.  Worst case, you will have to extract the wl source again and find another patch.

---

### Post by fakbill on 2009-05-04
Well I had a look a the gentoo page but I did not manage to find the correct patchs/patch_sequence to be able to compile it :(

If someone manage to compile this driver on a 2.6.30-rcX....please tell us what the trick is.

---

### Post by definingmoment on 2009-05-04
> **linux_zindabad said:**
> This Driver works perfectly. It is also installed by dell in the dell studio 1535 n series.

I second that comment. I've used these drivers with great success. I've yet to find a network I couldn't connect to.

---

### Post by frista on 2009-05-06
Hi all, I upgraded today to wl.ko vers. 5.10.91.9.
Still I can't connect to my AP, that runs on channel 120 / freq 5600MHz.
iwlist freq doesn't report my frequency as supported :(
(iwlist scan finds many other APs on supported frequencies)
Windows connect to my AP without problems, they also use some wl5 driver.

My question is, how to configure supported frequencies list in the driver.
I suppose different frequencies are allowed in different countries. 
Maybe I should install some wifi locale package.

Can anybody share experience here?

---

### Post by ioan123 on 2009-09-02
The driver works fine, although it has a hard time connecting to hidden wireless networks. A patch is available, check this [https://bugs.launchpad.net/ubuntu/+bug/307637](https://bugs.launchpad.net/ubuntu/+bug/307637)
You will need to re-compile the driver though
Ioan

---

