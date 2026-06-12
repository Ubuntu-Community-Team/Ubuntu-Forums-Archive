---
title: "Another Wireless Problem"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by axslinger on 2005-11-22
Hello,

I have installed Ubuntu 5.1 on a Sony PCG-FX140 laptop a few times now.  Installation goes fine, except I have to use the "acpi=off" option, otherwise it hangs in the initial stage of installation/detection.  The rest of installation is uneventful.

I have tried installing it with a Linksys WPC54G as well as a D-Link DWL-650.  In both cases the installation didn't fully install the wireless card.  When I say that, I mean that the device shows up in the device manager but not in the network settings.  I've jumped through all the "ndiswrapper" hoops.  That part of it works fine.  I am able to install the windows driver and ndiswrapper -l shows "driver present, hardware present".

I also installed the Windows Wireless Driver applet, and it even shows up as being present there.  However, when I go to Network Settings, I only have eth0 (the onboard ethernet) and ppp0.  Thats it.

iwconfig shows no wireless extensions.  I've added the interface entery to my /etc/network/interfaces file because there was no wlan0 present.  That didn't help either.  As a side note, with the Linksys, the lights came on after the system was booted, but with the D-Link, they never come on.

I've been searching this forum for 3-days, loading/reloading but nothing is working.  Am I missing something?  How is it that ndiswrapper shows "driver present, hardware present" but there is NO wlan0?  

Thanks in advance.

Brian

---

### Post by aznboi on 2005-11-22
try this tutorial, I have the same Linksys card and mine works
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)

---

### Post by Lambert on 2005-11-22
Pay close attention to this section on that link.

> 
**Important: Do NOT use drivers on your CD. They may work, but you may experience kernel crashes etc., if the driver on your CD has not been tested.**
Instead, you need to download appropriate Windows XP driver for your card from the Wiki entry [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"). To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output.
 The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. Now you need to get the Windows driver for this chipset. In the [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"), find out an entry for the same PCI ID and download the driver corresponding to it. Unpack the Windows driver with unzip/cabextract/unshield tools and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). 
  If there are multiple INF/SYS files, you may look in the [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files for example, TI drivers use BIN firmware files are all in one directory. Now use 'ndiswrapper' tool to install the driver with

There is a driver loaded and the hardware is present but it's not working properly and doing what it's supposed. You probably need a different driver.

---

### Post by taurus on 2005-11-22
I have the exact same card, Linksys WPC54G, on my HP laptop and everything works just fine for me.  Instead of using the driver on the CD that comes with it, I downloaded it from Linksys's sign (make sure you download version 3.0) and installed the driver as

ndiswrapper -i LSBCMNDS.inf (in "WPC54G Setup Wizard 3.1/Driver/NT" directory)
-then-
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/lsbcmnds/*.conf

Reboot and there it is in System --> Administration --> Networking as wlan0!!!

Let me know if you want me to send you a full description of how I got it to work.

---

### Post by axslinger on 2005-11-22
I did a little digging into the logs and see that there is an error 22 and "request for irq0 failed".  So I believe there is an issue at a lower bios/hardware level.  I tried adding "pci=biosirq" to the kernel-img.conf.  (That was a wild guess as I don't know where the kernel control settings go).  It still didn't work.  Got the same errors in the logs.

I checked the bios and I have either the option of PNP OS or Not.  I tried it both ways, neither worked.  I get the exact same results with the Linksys or the D-Link, so again, I believe it's at a deeper hardware level.  And, Sony doesn't even offer generic BIOS updates!  You have to have a Windows OS loaded to get their BIOS updates installed because it creates the boot disk from Windows.  If you attempt to create the boot disk on a different machine, it sees that it's not a Sony and bombs.  Nice.

Anyway, unless a miracle happens, I'm probably gonna trash this project.  I was just putting Ubuntu on this lappy because it wasn't being used for anything.  Thanks for your input.

Brian

---

### Post by taurus on 2005-11-22
I already told you to download the latest driver from Linksys' site for your WPC54G since I have it working just fine on my laptop with that driver.  But since you wouldn't bother to try that, I guess it's up to you now what you want to do with it...

---

### Post by axslinger on 2005-11-23
Sorry, I should have mentioned, getting the drivers from the Linksys site was the *first thing* I did.

But I appreciate the input.

Brian

---

### Post by aznboi on 2005-11-23
did u follow the guide in teh website i gave?

---

### Post by Lambert on 2005-11-23
**> Important: Do NOT use drivers on your CD. They may work, but you may experience kernel crashes etc., if the driver on your CD has not been tested. **Instead, you need to download appropriate Windows XP driver for your card from the Wiki entry [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"). 

Did you download the driver directly going to the linksys site or from the the ndiswrapper site? It is very possible the driver on linksys site is not going to work for your card like it has for others. If you go to the ndis site you can see there are different drivers for different variations of your card. You need to verify exactly what one you need to use.  And this is how you do it.

> To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output.
 The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. **Now you need to get the Windows driver for this chipset. In the [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"),** find out an entry for the same PCI ID and download the driver corresponding to it.

This is pretty much the only way to know you have the correct driver for your card. As you can see here there are 5 different pci ids for the wpc54g card.

pciid: 14E4:4320
pciid: 104c:9066 
pciid: 14e4:4318
pciid: 17fe:2220
pciid: 11ab:1faa

Currently your card is working but the it's not communicating to the os which is the drivers responsibility. So if ndiswrapper -l shows driver present hardware present then you do not have a correct driver.


>  Unpack the Windows driver with unzip/cabextract/unshield tools and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). 
   If there are multiple INF/SYS files, you may look in the [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") if there are any hints about which of them should be used. 

This is another common solution when driver is not working. Make sure you have the .inf and .sys file in a directory on your harddrive. The location  you're using when installing the driver. In some cases the .inf and .sys file are linked in some way and if you only have the .inf file the driver won't work.

> Make sure the INF file, SYS file and any BIN files for example, TI drivers use BIN firmware files are all in one directory. Now use 'ndiswrapper' tool to install the driver with

Your card will work with ndiswrapper. It's listed on the ndiswrapper wiki and there are testimonials here in the forums such as taurus who has one working. You just need to make sure the driver is installed properly

Uninstall the driver and start over

sudo modprobe -r ndiswrapper

sudo ndiswrapper -e <driver>

start over.

---

### Post by axslinger on 2005-11-24
FYI,

As a test, I installed BB 5.10 and the exact same LinkSys NIC on another spare laptop I had laying around (a Micron TransPort ZX).  I did the ndiswrapper/Windows driver installation, did the modprobe, went to Networking Configuration and the NIC was there, which further confirms my suspicion that this problem is at a lower level than the NIC itself.  I did nothing different with the Micron than what I did on the Sony.

---

