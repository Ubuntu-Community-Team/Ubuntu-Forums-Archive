---
title: "Wireless USB Adapter not recognized"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Sly1972 on 2011-06-05
Hi,

I have purchased recently a Hercules HWGUm-54 USB wireless adapter to move my desktop (10.04) to wireless (fed up with all those cables lying around).

lsusb indicates that the adapter is connected and functional.

As no connections was available, I downloaded the Windows drivers and installed them via ndiswrapper (ndisgtk).

ndiswrapper indicates that the driver is correctly installed, but that no hardware is present.

Network Manager does not offer wireless connections and ifconfig cannot find any connection except for Ethernet and loopback.

Any idea what I am doing wrong?

---

### Post by harlanwolfe on 2011-06-05
I found that restarting the computer a couple times helps it to recognize the hardwre. Be sure that your driver is listed a s proprietary driver.

Could be more complicated, but I'm newbie as well.

---

### Post by Sly1972 on 2011-06-05
Thanks for the feedback.

Tried it 4 times, no difference.

The drivers were extracted from the Windows installation package from the manufacturer, so they are digitally signed/authenticated, but I am not sure it makes any difference for ndiswrapper, and certainly not for Ubuntu, which does not recognize the driver.

Any other suggestion?

---

### Post by cogier on 2011-06-05
I can only tell you about my experience with a Netgear USB adaptor.

I did not need to do anything but plug it in to the computer and it worked. No Windows drivers required. Have you tried it without ndiswrapper?

---

### Post by Old_Grey_Wolf on 2011-06-05
Nice mini-USB wireless adapter.

When you downloaded the Hercules HWGUm-54 driver .exe file did you extract the files?

1. Browse to the .exe file, right click on it, and select open with archive manager.

2. Click extract at the top of the window that opens and copy all the files to an easy to find location.

3. Then use ndisgtk to install the .inf file from the extracted .exe file.

ndisgtk attempts to do this for you; however, it is not always successful.

I hate it when companies are so Windows centric that they package drivers in .exe files.

I hope this helped.

---

### Post by Sly1972 on 2011-06-06
Cogier,
 
Thanks, but did not work: lsusb does see the adapter, but nothing happens then to install it
 
Old_Gray_Wolf:
 
You are going to love this: Archive manager was able to open the exe but, inside, there was only ANOTHER exe! And the Archive manager was not even able to extract it!
 
I have installed the adapter on my laptop (Win7 32b) and it worked. I extracted the inf files during the install, transferred those files onto my Ubuntu box, used ndisgtk to install it: ndisgtk indicates that the driver is correctly installed, but no hardware is detected.
 
The same procedure was described in another forum [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Hercules_HWGum-54](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Hercules_HWGum-54), so it should work, but not for me. 
 
Why, oh why me :(?

---

### Post by gandaran on 2011-06-06
> lsusb indicates that the adapter is connected and functional.
no, lsusb doesn't show its functional, what it does is show type of hardware/chip brand
post the output of 'lsusb' so we can see what you have and help you find the correct driver.

edit:
if the adapter has the rtl8192su chip you don't need to install windows drivers, this chip works out of the box on ubuntu 11.04, older versions of ubuntu you will need to install firmware, post what ubuntu version and lsusb output.

---

### Post by bkratz on 2011-06-06
You are aware that ndiswrapper is meant to work with xp drivers--not vista or windows 7 right?

---

### Post by Sly1972 on 2011-06-07
bkratz, 

Thanks for the tip. I already checked on the ndiswrapper docs and found this. This is why I downloaded the XP version of the installation package and ran it in mode compatibility in Win7 to extract the .inf. No luck.

Gandaran,

full output of lsusb:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b8:0103 Seiko Epson Corp. Perfection 610
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 006: ID 06f8:e032 Guillemot Corp. [/COLOR]
Bus 001 Device 003: ID 1058:070a Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The chip of this adapter is indeed the rtl8192su. Unfortunately, I am using Ubuntu 10.04 and, as this is a rather old machine, I am not sure it will still have the resources to run 11.04.

Thanks for any help you can provide to find the correct driver/firmware.

---

### Post by gandaran on 2011-06-07
> **Sly1972 said:**
> bkratz, 

Thanks for the tip. I already checked on the ndiswrapper docs and found this. This is why I downloaded the XP version of the installation package and ran it in mode compatibility in Win7 to extract the .inf. No luck.

Gandaran,

full output of lsusb:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b8:0103 Seiko Epson Corp. Perfection 610
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 006: ID 06f8:e032 Guillemot Corp. [/COLOR]
Bus 001 Device 003: ID 1058:070a Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The chip of this adapter is indeed the rtl8192su. Unfortunately, I am using Ubuntu 10.04 and, as this is a rather old machine, I am not sure it will still have the resources to run 11.04.

Thanks for any help you can provide to find the correct driver/firmware.
I don't see any wireless adapter, is the adapter usb or pci?
for pci output
```
lspci
```
I would like confirmation first that it really has rtl8192su chip.
anyway, [follow this to get the rtl8192su]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html") working om ubuntu 10.04 (its for ubuntu 10.10 but should work on 10.04 too) and remove every trace of the windows drivers first to avoid any driver conflict.

---

### Post by Sly1972 on 2011-06-10
Gandaran,

Thanks for the tips.

It is a USB adapter and it is based on the rtl8192su chip.

I tried the instructions in the link you provided, but it did not work.

In the end, I gave up and upgraded to 11.04: it now works as well as some other few things that were not working in 10.04 (e.g. Logitec Webcam).

Again, thanks for the infos.

---

