---
title: "I need help with my Ralink card"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by italiano40 on 2006-10-14
I am dual booting Ubuntu with Winodws on an Averatec 2200 model
My Ralink card
-Driver Ver. 1.0.4.0
-Firmware ver 1.8
-Raconfig ver 1.1.7.0
can anyone help me to get this to work with Ubuntu

---

### Post by gvgerman on 2006-10-14
I'm sorry I can't give you a set of step-by-step instructions; too new at this myself.  I had problems with my wireless adaptor early on, as well, and the best advice I can give is to keep searching the forums and the web.

Here's some links to start with:

[Wireless Cards Supported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
[Wireless Trouble Shooting]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
[Wireless Trouble Shooting #2]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting")

---

### Post by JAwuku on 2006-10-14
From the Ralink driver version, it seems that you may have a **rt73** chipset, the same as in my USB wireless card.

If you boot into windows, you can find out the chipset model via Control Panel via the dialogs:

Start Button
Control Panel
Switch to Classic View
System
Hardware (tab at top
Device Manager
Network Adapters
(Double Click on your wireless card listed there)
Click on the Driver tab on the top
Click (finally:) ) on Details

The actual file name Windows uses for the driver comes up.

On my Windows XP system the file is **C:\WINDOWS\system32\DRIVERS\rt73.sys**

Yours may be very similar, or instead show something like rt2500, rt2571 etc.

Unfortunately, Ubuntu does not come with these rt73 drivers inbuilt by default, so we will have to use the wiki instructions to install them:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

(the latest Ralink driver is 1.0.6.0)

If however, you use the rt25** chipset, Ubuntu has a utility to use the Windows drivers as its own, called ndiswrapper.

An excellent tutorial is at:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

(the author uses Breezy, but it should work also in Dapper and Edgy)

Sorry for all the rigmarole :-k , but the instructions are quite straightforward, and hopefully, you should end up with a working wireless system. (:D not ](*,) !)

---

### Post by italiano40 on 2006-10-14
Thank you for all your help i am going to try it. and hopefull it will work

I am a newbie with Linux but a master with windows
So thanks you i will post back to tell if it work or not

---

### Post by blackest_knight on 2006-10-18
I have the edimax ew-7318ug usb wifi device which is built on the rt73 chipset.

it even claims support for linux in the forms of red hat debian and suse amongst others unfortunately ubuntu is not listed. 

I will also try the method suggested above

not had much success so far even compiling the gpl driver (I don't really know what i am doing to be honest)

---

### Post by blackest_knight on 2006-10-18
ok it works i got rausb0 installed and working i am going to post a seperate thread just for the Edimax ew-7318ug as a how to. 
its pretty much all in a terminal so it should be easy to cut and paste.

---

### Post by PriceChild on 2006-10-18
> **JAwuku said:**
> If however, you use the rt25** chipset, Ubuntu has a utility to use the Windows drivers as its own, called ndiswrapper.Actually... its built into the kernel... my rt2500 and rt2400 are detected out of the box :)

---

