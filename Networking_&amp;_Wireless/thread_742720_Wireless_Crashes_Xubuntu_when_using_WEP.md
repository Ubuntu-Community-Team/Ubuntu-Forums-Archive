---
title: "Wireless Crashes Xubuntu when using WEP"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by matrixbuntu on 2008-04-02
Hi folks, I'm new and excited.   Just installed Xubuntu 7.1 on my Old IBM A22E.\\:D/

Everything seems to be working well.  When connecting wireless with no security key settings on my router/wireless network card, it's fine. 

However once I add the WEP security Encryption 128bit- HEX, the lights will flash on my card to show it's connected, but then Xubuntu just freezes and I have to reset the system.  Strangely when Xubuntu crashes, the Scroll lock light and Caps light keep flashing.  

My router is a D-link 614+ Rev B while my PCMCIA card is a Dlink  DWL-650 Rev M.

Wonder if there is something I need to do to enable the encryption.:confused:

---

### Post by kevdog on 2008-04-02
Try just establishing a manual network connection to see if you can get around the issue for now.  Here are the instructions.  Seems like a lot, but its really straight forward for WEP:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by ugm6hr on 2008-04-02
Sounds like Network Manager misbehaving.

Manual connection (as kevdog's tutorial) is a good idea, or you could try Wicd (see below).

---

### Post by matrixbuntu on 2008-04-03
Hello. I tried the WICP thing and it also crashed as soon as I connected.
Actually reading the instructins, WICP says it is suppose to auto-uninstiall network manager. I am not sure if it was uninstalled as the old network setting menu is still there?

---

### Post by ugm6hr on 2008-04-04
The Network Monitor Setting (in the main menu - Applications->System->Menu) stays.

Network Manager (the computer / 4 vertical bars in the task manager) is uninstalled - the thing that shows circling green when it connects.

Network Manager should be uninstalled.  If not, you aren't running Wicd.

---

### Post by derekge on 2008-04-11
> **matrixbuntu said:**
> ...Xubuntu just freezes and I have to reset the system.  Strangely when Xubuntu crashes, the Scroll lock light and Caps light keep flashing.

I have this exact problem! I'm running RTL8180 chipset (which loads fine) on a Toshiba laptop and I have Xubuntu installed too.  If I use WEP - and I have tested using 2 different routers - the system locks up and the caps light blinks - WTF!?  I need to do a manual reboot.

I have tried the manual setup from the link above and it locks up too!  I'd love to find out a solution to this because I'm a big fan of Xfce and I want the wireless WEP to be stable.

---

### Post by derekge on 2008-04-13
I just tried another method: uninstalling network manager and editing /etc/network/interfaces to reflect WEP settings on my dhcp network and wouldn't you know it? - no desktop....just a blinking caps lock button.

For some reason Xubuntu / Ubuntu doesn't like WEP on my wireless chipset.  I'm beginning to believe that the there is a problem with the rtl8180 driver and ndiswrapper (I assume that's how Ubuntu gets it going).

---

### Post by Foster Grant on 2008-04-13
One possible solution: Use WPA protocols instead of WEP.

(WPA is proven to be more secure than WEP &#8212; it was implemented because of security problems with WEP &#8212; and in my experience it also seems to be faster. Could just be me, though.)

---

### Post by derekge on 2008-04-13
Yes FG - but that would be too easy! ;>

---

### Post by derekge on 2008-04-17
More info: I tried using WICD and it locks up the same way too!  As a sidenote, I used the Xubuntu live CD on my desktop system and network manager allowed me to connect to my WEP wireless network at home!  No lock up.

This has to be a chipset issue working on Xubuntu.  I think I know iwconfig pretty well now!

---

### Post by derekge on 2008-05-03
Verified: chipset issue.  I now used a Linksys G pcmcia card with a broadcom chipset and it works fine.

---

