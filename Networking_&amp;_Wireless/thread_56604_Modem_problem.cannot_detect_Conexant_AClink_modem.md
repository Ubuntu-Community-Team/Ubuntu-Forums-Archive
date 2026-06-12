---
title: "Modem problem.cannot detect Conexant AClink modem"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by byen on 2005-08-13
Hey Guys,
Man..to tell yu the truth I am really suprised at this issue but oh well! If all pc-hardware makers gave support to linux... life wouldnt be so intersting would it? Anyways..here goes my problem:

All these months ive been using my Wifi connection to connect to the internet and last week I had to use a dial-up and BOOM! it does not detect my modem..I dont know what to do and where to begin...can someone help me here...this is what my modem list shows in windows:
Under Modems:
-Modem: Conexant 56k ACLink Modem
Under Network Adapters:
-Microsoft Network adapter (made by Texas Instruments)
-National semiconductor DP83815-based PCI fast Ethernet adapter (made by Netgear)


So my question for you is...what do i need to do to configure my modem and my Ethernet adapter.....

thanks guys.

---

### Post by jasmuz on 2005-08-13
First off, run HAL to check how your system recognizes the modem, then yo might want to look if its listed in: [www.linmodems.org](www.linmodems.org)

Dont confuse the modem configuration with network configuration, network configuration is reserved for Ethernet cards, and Wifi.

Your ethernet must be detected, also check HAL and open a terminal, type ifconfing -a to see all connection devices enabled for your machine.

Hope this helps.

---

### Post by stiperstones on 2005-08-14
Can i ask a question how do you run hal

---

### Post by blastus on 2005-08-14
Bah Conexant...I hate Conexant! :mad:

If you want find out how Linux recognizes your modem, download [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz). Unpackage the contents of this file...

gunzip scanModem.gz

If you notice the scanModem.gz has been replaced with a file called scanModem. To execute this program you may need to give the file execute permission...

chmod +x scanModem

Now you can run the program...

sudo ./scanModem

You should see a bunch of text output. The scanModem program creates a directory called Modem that contains the results of the scan. Now take a look at the contents of one of the files in the Modem directory...

gedit Modem/ModemData.txt

If your modem has a DSP you should see a line in the file something like “The modem has a supported Lucent/Agere DSP (digital signal processing) chipset” Of course your modem is a Conexant modem so you'll see something different from my Lucent WinModem. If your modem has a DSP then you *may* be able to get some free drivers for it and use them. I am in the midst of creating a tutorial for getting a Lucent WinModem to work on Ubuntu Hoary ([http://www.ubuntuforums.org/showthread.php?t=55488](http://www.ubuntuforums.org/showthread.php?t=55488)) Some of this may or may not be applicable to your modem.

Some helpful instructions on using scanModem can be found at [https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)

---

