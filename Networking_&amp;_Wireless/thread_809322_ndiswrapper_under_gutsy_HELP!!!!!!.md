---
title: "ndiswrapper under gutsy HELP!!!!!!"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Fenris_rising on 2008-05-27
hi all

i need a little help please. ive used the ndiswrapper to setup 3 various wireless devices all to good and stable effect. now ive just fixed a friends PC installed gutsy and updated as required. now i had the belkin usb wireless adapter working using ndiswrapper for 2 days. as soon as the pc has gone back to his place the belkin flashes at boot but then whilst the scan for the network is happening the belkin stops. i have checked the belkin on another pc and alls well with it. im pretty sure that the usb ports are ok on the PC. so im thinking that the module has corrupted. i did try just re running the ndiswrapper in terminal again but of course it just tells me the bits already exist. i want to remove the module and start from scratch again. problem is i dont know how.
so in a nutshell how do i remove the module that ndiswrapper made and can you make it easy to understand please.

---

### Post by mapes12 on 2008-05-27
ndiswrapper is notoriously fragile and should be a last resort compared to native drivers.

Have you been through this noting careful aspect to blacklisting drivers that may load and conflict with the ndiswrapper configuration:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59)

The same happened to me. For a few days ndiswrapper was OK but then the configuartion broke down to an useable state for no apparent reason. Fault = ndiswrapper conflicts!

---

### Post by Fenris_rising on 2008-05-27
hi
yep every alternate was blacklisted. and although the native drivers initially work it only runs at 1Mb/s. now the odd thing is that whilst running the code to try and reinstate it an alternate rt2500usb was shown, i blacklisted it again. now this was definately blacklisted originally. so how do i start with a clean slate??

---

### Post by mapes12 on 2008-05-27
I guess you've been through this as well??

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

What is the exact model of the card?

---

### Post by Fenris_rising on 2008-05-27
hi there

yeah pretty much. its like the tut that has worked great for my PC which has a PCI wireless card and my brandless usb dongle, for my laptop, and a belkin usb on my other m8s. the one in question is again a belkin F5D7050D the disk contains the rt73.inf and sys which i copy to the folder on the PC
(taken from the XP drivers folder on the disk) (should i try the win2000?)
from the page you directed me to i can see a couple of places where i can look and see if the ndiswrapper is listed '/etc/modules' and /etc/modules/ndiswrapper' any input would be gratefully received. seems odd that ive had rocksolid ndiswrapper use but this one has gone down. my OS is 8.04
the laptop has xubuntu 7.04.

---

### Post by mapes12 on 2008-05-27
I found this:

[http://ubuntuforums.org/showthread.php?t=248059](http://ubuntuforums.org/showthread.php?t=248059)

The card is not listed here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

When you say the dongle has been tested in another PC do you mean one running Ubuntu and was it the same version of Ubuntu to the one where the problem occurs?

Me thinks it's the dongle having a rogue chipset...........

---

### Post by Fenris_rising on 2008-05-27
yush your quite correct its not listed!!! ok the belkin i used was mine again its a 7050 i used my belkin disk. could it be that their belkin driver disk has slightly different drivers????unlikely i guess but hey who knows. i only ask because its their one that they have just bought thats not workin. also i checked theirs on a windows machine basically to make sure it wasnt duff. how would i get back to a position where i can try a fresh setup using the ndiswrapper and their belkin disk inf and sys files?

---

### Post by mapes12 on 2008-05-27
> could it be that their belkin driver disk has slightly different drivers?

From the minimal research I have looked at about these Belkin adaptors I'm not convinced that the chipsets are the same from card to card, even with the same model number. OK, they may work under windoze because of the amount of support vendors provide for a multitude of chipsets.

What would I do? Abandon this Belkin card. I do not know your territory but I know these work straight out the box natively with the Linux kernel and they ship worldwide:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

I have one of the Comtrend RT2500 PCMCIA cards which is just a plug and play procedure.

Other than my above suggestion I think you will be looking for an answer for sometime............unless another poster has the solution.

:guitar:

---

### Post by Fenris_rising on 2008-05-27
UK like yourself. ill run it past my m8, but i think budget issues need me to try and get this one going.

---

### Post by mapes12 on 2008-05-27
UK..........cool \\:D/

If your mate understands the issues and is OK to get a supported card then I would reinstall Ubuntu again to kill any system changes in the filesystem.

Best wishes and good luck.

Mark

:guitar:

---

### Post by Fenris_rising on 2008-05-27
thanks for your help with this. just had a word and as they are getting a second PC (im building it) ill put 8.04 on that and try this belkin and for the other ill check the compatability list and they will get one for the current PC.

---

