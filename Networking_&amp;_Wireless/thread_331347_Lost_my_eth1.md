---
title: "Lost my eth1"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by KentS on 2007-01-04
I managed to lose my wireless eth1. Is there anyway I can create that connection again?

When I first installed Ubuntu (Dapper Drake) eth1 came up automatically. I then deleted some drivers and eth1 was gone. It didn't come back when I reinstalled Ubuntu, even though I formated the relevant partitions.

Writing "ndiswrapper -l" I get 
"bcmwl5          driver present, hardware present".

Can someone please help me?

---

### Post by zgornel on 2007-01-04
Isn't there a wlan0 ?

---

### Post by KentS on 2007-01-05
Nope. Writing iwconfig I get an lo, eth0 (my cabled connection) and sit0. None of them have any wireless extensions. Using ifconfig lo and eth0 are listed.

---

### Post by zgornel on 2007-01-05
Does lspci report any wireless adapter ?

---

### Post by KentS on 2007-01-05
My wireless card is 
> 0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

I know the Broadcom cards are problematic, but I have managed to get this card to work with Dapper Drake.

The first time I installed Ubuntu eth1 came up automatically. I used the fwcutter to get the firmware. It worked, but connection was slow. So I decided to try ndiswrapper. I think the problem started when I deleted everything starting with bcm43xx in /lib/firmware and /lib/firmware/`uname -r` to try a fresh install of the driver. After that I lost eth1. And reinstalling Ubuntu after formatting the disk didn't help.
Currently the two directories doesn't contain any bcm43xx-files.


The entire output from lspci is
> 0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
0000:03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:09.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:09.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by Henry Rayker on 2007-01-05
Had you upgraded from a previous version? I know that, from version to version, some wireless cards functionality fluctuate wildly.

---

### Post by KentS on 2007-01-05
Ubuntu Dapper Drake was the first Linux OS installed on this PC. The wireless card worked on kernel version 2.6.15-27-386, which is the version I'm currently using. I have winXP installed on another partition. I have not done anything with that partition since I bought the PC.

---

### Post by mxrten on 2007-01-05
Silly question perhaps: is ndiswrapper, the module, loaded?

I've the exact same chipset, and I solved my problem by downloading the latest ndiswrapper tarball (version 1.33) from [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) and compiling it myself:

```
tar xvf ndiswrapper-1.33.tar.gz
cd ndiswrapper-1.33
make DISABLE_USB=1
sudo make DISABLE_USB=1 install
```

You will need package build-essential before executing the above commands, and there might be some more dependencies...

It's not a perfect solution, but it works for me, until ubuntu will include an updated version in their repositories.

---

### Post by KentS on 2007-01-05
A couple of questions. 
What do I do with the ndiswrapper version already installed? I tried 
> sudo apt-get remove ndiswrapper
after having removed the driver, but that didn't work. Do I have to remove it manually?

Output from 
> make DISABLE_USB=1
was
> make -C driver
make[1]: Entering directory `/home/kent/Desktop/ndiswrapper-1.33/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/kent/Desktop/ndiswrapper-1.33/driver'
make: *** [all] Error 2


The directory build doesn't exist in /lib/modules/2.6.15-27-386/
The newest version of build-essential available through the Ubuntu repositories was already installed. Do you know what compilers/files I need to give a path to?

---

### Post by darkmediator on 2007-01-05
Me too lost eth1, netwrok-manager doesn't show any wireless connection. But the strange thing **I didn't remove anything**. The previous day it was working excellent!!

---

### Post by mxrten on 2007-01-05
I think you need to apt-get the appropriate linux-source (linux-source-2.6.15 ?)

ndiswrapper come bundled as ndiswrapper-utils and ndiswrapper-common, so to remove the old one:
```
sudo apt-get remove ndiswrapper-utils
sudo apt-get autoremove
```

I hope that should do it!

ps. Use TAB to autocomplete, very useful, or press twice to list all that matches

---

### Post by KentS on 2007-01-06
Thank you very much!
I now have wlan0, and it detects my wireless network. (It was linux-kernel-headers I needed to install to run 'make DISABLE_USB=1, and autoremove doesn't seem to be a valid command. But anyway, it seems to have worked.)

Now I only need to figure out how to connect to my router...](*,)

---

### Post by mxrten on 2007-01-06
Glad it worked! :D 
You seem to have an older version of apt-get. If ndiswrapper-common is still on your system you can remove it manually with the same command as it is not needed.

This might help you configure the network: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface)

(I had to use **key open**, instead of **key restricted**)

---

### Post by darkmediator on 2007-01-06
@KentS : can u explain exactly what u did??

---

### Post by mxrten on 2007-01-06
darkmediator: what is your wireless network card? if it's the same as KentS's and mine I can help you, or you can follow the instructions in this thread.

---

### Post by darkmediator on 2007-01-06
^^Its intel Pro Wireless 2200 BG. I have been using ipw2200 drivers so far!

---

### Post by mxrten on 2007-01-06
Ok. KentS used the ndiswrapper module which make use of windows drivers for his card. That's not what you need (I think).

Have you installed the proper firmware as well? If not, you can get it here: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php), then extract all *.fw files to /usr/lib/hotplug/firmware/

If the firmware already is installed or the above doesn't help I don't know how to help you. My advice is to start a new thread so that people with more specific knowledge of that card can help you.

EDIT: the correct firmware directory is **/lib/firmware/`uname -r`** in the newer dists... and they already have the firmware in place

---

### Post by KentS on 2007-01-06
mxrten: I'm now writing this using my wireless, and it works perfectly. So again; thank you very much.

darkmediator: According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel ](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel ) your card should work out of the box. Mine doesn't, that's why I had to use ndiswrapper. Have you tried to reinstall the driver and firmware? That's basically what mxrten helped me with. I found a couple of guides for your card following the previous link. I don't know if they can help, but I'll list them so you can have a look.
[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)
[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)
I'm afraid I can't be of any assistance. I'm not very experienced with Linux, and I've never used the card you're using.

---

### Post by darkmediator on 2007-01-06
Hey don't worry! My problem's resolved now. Thanx for replying anyways! I did many things installed ndiswrapper and windows drivers, did "modprobe ipw2200" etc. I guess latter did the trick. I'm not sure, which one did the trick! :)

---

