---
title: "Plug and Play out of the box ???"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by EmoDx on 2008-01-12
First off, I have read the Linux wireless networking support list at [http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/") and at [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/").  So, now I have a total list of what "can" work. But is there a list of what wireless cards work out of the box? I "could" spend time time trying to follow directions to get a PCMCIA card to work on my laptop. But I would rather spend that time doing something more important.
My specs:
Micron GX laptop
2 PCMCIA slots (preferred)
1 USB slot (not preferred)
1 Miniport slot (preferred if the card somes with Cat 5 also)
Ubuntu 6.06.1 Desktop
Windows Wireless Drivers GUI installed

Any help would be very much appreciated. BTW, I have a Linksys WPC300N with a Broadcom 4329 rev 1 chipset. I tried looking for the .inf for it, but it is hidden in the Linksys .exe. Any ideas how to get the .inf?

Emo

---

### Post by luisromangz on 2008-01-12
In the ndiswrapper webpage they have links to many inf files or the places they can be get. If you have a setup file with the inf file inside, you can try to "install" that exe file using Wine, that's how I got my inf file.

---

### Post by EmoDx on 2008-01-12
> **luisromangz said:**
> In the ndiswrapper webpage they have links to many inf files or the places they can be get. If you have a setup file with the inf file inside, you can try to "install" that exe file using Wine, that's how I got my inf file.

Can you point me in the right direction? I don't know what Wine is. I went to add/remove programs, typed wine in the search function. THe list that came up had Wine already checked, so I assume that it means that it is already installed. At this point I checked the Applications menu. Didn't find Wine anywhere. What do I do now to use wine to install the Windoze .exe?

Also, I tried the following the instructions in the 43xx sticky. Didn't work. So I read the read me's, was able to "sudo ./bcm43xxfirmware.sh" the files.  Still not working. FYI, the power light isn't even illuminating on the card. Yes, it works in my other laptop and it worked on this machine when it was a XP machine. Any ideas?

-E

---

### Post by EmoDx on 2008-01-12
emodx@MicronGX:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bri dge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridg e (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:08.0 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
0000:00:08.1 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
0000:00:0c.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cycl one] (rev 10)
0000:00:0d.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (r ev 10)
0000:01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
0000:06:00.0 Network controller: Broadcom Corporation: Unknown device 4329 (rev 01)
emodx@MicronGX:~$

---

