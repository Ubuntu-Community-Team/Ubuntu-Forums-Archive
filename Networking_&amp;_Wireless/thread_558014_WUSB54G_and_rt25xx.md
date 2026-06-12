---
title: "WUSB54G and rt25xx"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by uputer on 2007-09-23
Linksys USB adapter WUSB54G (Ver.4) which has rt2500 (or rt2570) chipset work in Feisty using a static ip and WPA?  Or, can anyone confirm whether it works with WPA (if you are using dhcp)?

I read that the rt25xx chipsets (Ralink) are among the most compatible with Linux.   I have at least one more computer to set up with wireless (I would like to, anyway) and I thought I'd inquire about other adapters (I just bought a Belkin usb that is having some issues).   My router is a Linksys so I would go with Linksys but I just discovered this particular Linksys usb adapter is supposed to be relatively compatible.   

Any issues to be aware of?   Is there any write-ups on how to configure?   I would want to use WPA and a static IP if possible.   On the WikiDocs in the Ubuntu Doc pages, that particular Linksys usb adapter is listed as working but the trial was using WEP.   Can it function using WPA (without issues) and if anyone could confirm, with static ip?

I'd configure it manually if it's not too difficult, meaning if it is something I could learn/understand.   I don't want to just copy someone's instructions if it's complicated (I would like to have a clue of what I'm doing. :-)).  

Thanks for any answers.

---

### Post by noob12 on 2007-09-23
This might help:

[http://ubuntuforums.org/showthread.php?t=516649](http://ubuntuforums.org/showthread.php?t=516649)

Added:
Er.  Scratch that.  That's the GC; you've got the G USB.  Not sure if that posting applies.

You'll probably want to build latest from serialmonkey.

---

### Post by uputer on 2007-09-23
I didn't get either yet.   I'm wondering which Linksys (WUSB54G-based) adapter is most configurable or easiest (relatively speaking) in Linux/Ubuntu. ;)

---

### Post by noob12 on 2007-09-23
So the situation as far as I understand it is that Feisty ships with older serialmonkey drivers, which for the most part don't work all that well, but that upgrading to recent ones (building from source downloaded from the rt2x00 serialmonkey site) works acceptably.  Others have been successful with ndiswrapper.

---

### Post by uputer on 2007-09-23
I really would like to avoid the nsdwrapper thing, though.   It sounds like major work and frustration.   

If it doesn't work out of the box, I want something with linux/open source drivers.   I wanted to avoid the compiling/adding modules or whatever, too, but I prefer that over nsdwrapper which sounds equally unappealing but perhaps, even harder (and more time-consuming).

The problem is that the Ralink page is confusing (to me, anyway) and there are various chipsets so I have to determine which driver goes with which chipset.   The WUSB54G ver. 4 USB adapter sounds like it has a rt2570 chipset and would then use a rt2500 driver or rt2571 driver?   I'm not sure yet but it's one or the other.    From the site, it appears that the driver is "Drv2.0.8.0" but this driver is outdated, already a year old.

The rt25xx/Serial Monkey site has a driver file for the actual usb adapter but both options sound like major work and could be potentially frustrating.

---

### Post by kevdog on 2007-09-23
Id go ahead and compile the new serial monkey driver.  I know you want to avoid this but the process is really quite painless and takes less than 5 minutes.  If you plan on sticking with Linux or Ubuntu, compiling and installing from source is a good skill to learn since you will definitely need to do this in the future sometime (if you want cutting edge software)

---

### Post by rustybronco on 2007-09-24
> **uputer said:**
> Linksys USB adapter WUSB54G (Ver.4) which has rt2500 (or rt2570) chipset work in Feisty using a static ip and WPA?  Or, can anyone confirm whether it works with WPA (if you are using dhcp)?

it only works with wep.

---

### Post by dmg412 on 2007-09-25
I have had success with using ndiswrapper with this device.  Try installing ndiswrapper and inserting the driver cd (for windows).  

Use the command sudo ndiswrapper -i myDriverFile.inf where myDriverFile.inf is the .inf file found on your linksys disk (there is also a GUI tool that does the same install process).

If you have previously installed ndiswrapper, make sure no drivers are installed by typing ndiswrapper -l and make sure there is no output.

I do have a problem that when the system restarts, I have to remove and re-install the drivers through ndiswrapper, but I do not restart often so it is not that big of a deal to me.

---

### Post by wieman01 on 2007-09-30
> **uputer said:**
> I really would like to avoid the nsdwrapper thing, though.   It sounds like major work and frustration.   

If it doesn't work out of the box, I want something with linux/open source drivers.   I wanted to avoid the compiling/adding modules or whatever, too, but I prefer that over nsdwrapper which sounds equally unappealing but perhaps, even harder (and more time-consuming).

The problem is that the Ralink page is confusing (to me, anyway) and there are various chipsets so I have to determine which driver goes with which chipset.   The WUSB54G ver. 4 USB adapter sounds like it has a rt2570 chipset and would then use a rt2500 driver or rt2571 driver?   I'm not sure yet but it's one or the other.    From the site, it appears that the driver is "Drv2.0.8.0" but this driver is outdated, already a year old.

The rt25xx/Serial Monkey site has a driver file for the actual usb adapter but both options sound like major work and could be potentially frustrating.
Give the tutorial in my signature a go. If you have problems post there & I will help.

---

### Post by uputer on 2007-09-30
you know what, wieman, I think I would go with one of the adapters in your list.  From what I can tell, there doesn't seem to be anything really working out of the box.   I think you went to a lot of trouble and effort to get those adapters and chipsets configured.   Could you recommend one of those on your list or is any of them equally good?

Which adapter works well with WPA?  Do you know?

---

### Post by wieman01 on 2007-10-01
> **uputer said:**
> you know what, wieman, I think I would go with one of the adapters in your list.  From what I can tell, there doesn't seem to be anything really working out of the box.   I think you went to a lot of trouble and effort to get those adapters and chipsets configured.   Could you recommend one of those on your list or is any of them equally good?

Which adapter works well with WPA?  Do you know?
Sure... but before you go ahead, you should take a look at the Netgear WG311T which is fully supported including WPA2. See this thread for reference:

[http://ubuntuforums.org/showthread.php?t=363633&page=3]("http://ubuntuforums.org/showthread.php?t=363633&page=3")

That said, I can recommend the Linksys WUSB54G V4 (mind the version number) which works fine with "ndiswrapper" (WPA2 enabled). But I recommend only because I know it well... I don't know any others to be honest.

---

