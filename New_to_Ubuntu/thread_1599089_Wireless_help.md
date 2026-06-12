---
title: "Wireless help?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by LisaZ on 2010-10-17
So before I begin I'd just like to clarify by saying I'm pretty much the epitome of noob when it comes to computers. I'm really bad at technical jargon, so if you offer advice, just pretend you're talking to kindergartener.

So a few days ago, when I had Vista, my laptop stopped booting up except in safe mode without networking. I decided I'd had enough, and installed Ubuntu on my computer. Now I don't have wireless capabilities. I'm unsure if this has anything to do with Ubuntu, or if my computer just somehow lost it's ability to get wireless connections. When I click on the internet icon in the upper right hand corner, the dropdown menu has Wireless Networks and then "Device not ready". Obviously, the computer I'm on can use the wireless in our house, and so can my mother's laptop.

Any advice appreciated.

---

### Post by cpmman on 2010-10-17
Go into BIOS - when you first switch on - it will say you need to press F12 or Escape or similar.

Once in BIOS check the wireless setting - it should offer wireless on or off - make sure it is on.  Exit BIOS saving the setting and boot normally.

---

### Post by linux-hack on 2010-10-17
open a terminal and type : ```
lspci
``` this will show you all your pci devices and you wireless card.
post the output of that comand in here.

---

### Post by LisaZ on 2010-10-17
@linux hack
 
 
 
rachel@rachel-HP-G60-Notebook-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
[EMAIL="rachel@rachel-HP-G60-Notebook-PC:~$"]rachel@rachel-HP-G60-Notebook-PC:~$[/EMAIL]




 @cpmman When I looked in "BIOS settings" or such, I didn't see anything about wireless...

---

### Post by linux-hack on 2010-10-17
this is your network card :

> 02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

If you go to System->Administration->Drivers Install (or something like this) click on 'it and look it it shows you some drivers to install ..

---

### Post by LisaZ on 2010-10-17
I went under System -> administration -> additional drivers, if that's what you meant...

The first message that popped up was "Downloading package indexes failed, please check your network status. Most drivers will not be available."

Then after that it said "Searching for available drivers..." and popped up with "No proprietary drivers are in use on this system."

...?

---

### Post by Quackers on 2010-10-17
Can you connect an ethernet cable between your computer and your router and try Additional Drivers again?

---

### Post by GaryTheCat on 2010-10-17
+1 Quackers

---

### Post by LisaZ on 2010-10-17
Okay, so I hooked it up and have a connection to the internet through the cable. When I went to Additional Drivers, it still said the thing about no proprietary drivers...
However, a message popped up from Ubuntu saying I had some updates to install, so I went ahead and did that.
Maybe I'm under the wrong thing?

---

### Post by Quackers on 2010-10-17
Just a suggestion, but try rebooting and then go to System > Admin > Additional Drivers again.

---

### Post by LisaZ on 2010-10-17
Same deal.

---

### Post by Quackers on 2010-10-17
What version of Ubuntu are you running please?
I have been googling and it seems there are many threads on your wireless card. Some of them mention HP in particular.
I'm surprised that "additional drivers" doesn't appear to be doing anything other than reporting no drivers in use.

---

### Post by LisaZ on 2010-10-17
I'm running Ubuntu 10.10, 32 bit.

---

### Post by Quackers on 2010-10-17
Does your laptop have a physical on/off switch for wireless and/or bluetooth?
If so perhaps you could turn it off and then back to on. It seems some people have had problems with Ubuntu detecting the switch position.
Also there is a Networking & Wireless forum here. Maybe you would receive more advice there.
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by LisaZ on 2010-10-17
Thanks. It's odd, when I press the button it doesn't change color, which would indicate it's off. It's just constantly blue/on.

Would it be wiser to just start a new topic in the other forum or have an administrator move this one?

---

### Post by amjjawad on 2010-10-17
> **cpmman said:**
> Go into BIOS - when you first switch on - it will say you need to press F12 or Escape or similar.

Once in BIOS check the wireless setting - it should offer wireless on or off - make sure it is on.  Exit BIOS saving the setting and boot normally.

I've never heard about this in my whole life. Wireless settings are not suppose to in BIOS. At least, this is what I'm aware of.

---

### Post by amjjawad on 2010-10-17
> **LisaZ said:**
> Thanks. It's odd, when I press the button it doesn't change color, which would indicate it's off. It's just constantly blue/on.

Would it be wiser to just start a new topic in the other forum or have an administrator move this one?

What laptop do you have? is it Toshiba?

---

### Post by LisaZ on 2010-10-17
It's an HP G60-235DX.

---

### Post by Quackers on 2010-10-17
Maybe if you just jump over there and see if you can find anything about your card and what other people have done with it. If you use the search function in that forum with AR5001 as key words you will come up with several threads :-)

---

### Post by amjjawad on 2010-10-17
> **LisaZ said:**
> It's an HP G60-235DX.

If you had the same issue with Windows then it's either a hardware issue or driver issue.
I don't have 10.10, I have 10.04 desktop version.

As mentioned previously, I suggest to use google or search this forum hopefully you can find something useful.

I know it's a bit too late but something to learn from this. Whenever you want to install Ubuntu or any other distributions of Linux which has the LiveCD feature, make sure to TRY before INSTALL. By doing that, you could test your system and see what works for you and what does not.

Good luck :)

---

### Post by LisaZ on 2010-10-17
Fixed following the instructions here;

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Big thanks to everyone who offered help! Would've never been able to fix it in Windows!

---

### Post by Quackers on 2010-10-17
Nice work :-) Good result.

---

### Post by amjjawad on 2010-10-17
> **LisaZ said:**
> Fixed following the instructions here;

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Big thanks to everyone who offered help! Would've never been able to fix it in Windows!

Well done :D

---

