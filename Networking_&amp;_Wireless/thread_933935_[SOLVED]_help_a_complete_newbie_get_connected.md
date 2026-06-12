---
title: "[SOLVED] help a complete newbie get connected"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by MyNameIsDerek85 on 2008-09-30
Let me start by saying that I'm a completely uneducated newbie when it comes to Linux and I have always used Windows. I am not familiar with the Ubuntu OS at all since I haven't really taken much time to play with it. My main goal right now is to get up and running. Therefor, the absolute best way to help me would be to teach me as if you were helping a child make a peanut butter and jelly sandwich (don't worry, I know how to make a peanut butter and jelly sandwich, but you get what I'm saying). 

I'm running the latest version of Linux Ubuntu on an Aspire 5050, dual booted with Windows XP. (Random fact: My laptop originally came with Windows Vista but I downgraded to XP because I hated Vista, surprise! God, I hate Microsoft). My hard drive is seperated into two seperate drives. XP is installed on my "C://" drive and I installed Ubuntu on my "D://" drive (which had absolutely nothing on it). 

Basically, I want to get on the internet using wireless. I don't know if it's useful, but I connect to a free public wireless internet connection (nothing illegal or anything, it's sent off by a local coffee shop and they allow local neighbors to connect) and I don't have a clue what I'm doing. 

I did try to figure it out before posting here by constantly switching between XP (where I'm able to connect to the internet) to find online help and Ubuntu (which, as you know, is unable to connect). The fact of the matter is that A) I failed horribly or B) it was giberish to me. 

So, I'm going to start from scratch. So, for all you Linux experts out there that are willing to take it step by step with me (as if you were at an illiterate friends house, helping him get his Ubuntu internet ready), I call on your expertise.

---

### Post by pytheas22 on 2008-09-30
First of all, go to System>Administration>Hardware Drivers ('System' is one of the main menus in the top-left corner of your screen on Ubuntu).  You will be prompted for your password.  After you enter it, a window will open; you may see an option there for enabling wireless.  If it's there, check it, reboot and see if your wireless works.  For some kinds of wireless cards requiring proprietary drivers, this is what it takes to get online.

If that doesn't work or you see no wireless option there, please go to Applications>Accessories>Terminal.  A command-prompt will open up (don't be scared; I'll always tell you exactly what to type in it, so all you will have to do is copy-and-paste).  Please run the following commands (remember that case matters in Linux, so if you see a capital letter below, you need to enter it as a capital letter).  For each command, copy-and-paste the output here (you can copy text from the terminal by highlighting it, right-clicking and selecting 'copy,' then pasting using control-V):

```
lshw -C Network
```

After entering this command, you will see a message for a few seconds that says something like "Warning: You Should be Root to Run this Program."  Ignore that message and wait a few seconds, and you will see some textual output and be returned to the command prompt.  Copy that textual then continue with the following commands:

```
lspci -nn
lsusb
uname -m
```

With that information, we can figure out what you need to do to get wireless working.

Also, I understand that it may be difficult for you to copy-and-paste information from the terminal onto this forum, since you don't currently have any Internet access in Ubuntu.  To get around that, you can go to Applications>Accessories>Text Editor, which will open up a blank text file.  Save the terminal output into the text file, then save the file to a USB stick.  Plug the USB stick into a computer that has Internet access, open the text file there, and copy-and-paste the terminal output here that way.

Alternatively, if possible, just hook your computer up to ethernet (if this is possible, it would be best, as it's going to be easier to get your wireless working if you have a wired connection first).

---

### Post by MyNameIsDerek85 on 2008-09-30
Hey, thanks. I really appreciate you taking the time to explain this to me in a way that I can understand. 

Alternatively, because I didn't have access to any USB storage devices (I'm poor, give me a break, haha), I found that I could save the text files to one of my windows folders and convert them using Microsoft Word. 

I did the hardware device thing and all that came up was my graphic card (I think that's what it was anyway, I don't remember. bad short term memory), so I followed the next steps and here's the information you requested.

```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:b5:87:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:2c:e3:fd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
08:01.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
08:01.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
08:01.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
08:01.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
08:01.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)
08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
08:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

~$ uname -m
i686

```

The codes are in order of the way you told me to enter them. I also left the code on some of them too to make sure I entered them right.

---

### Post by pytheas22 on 2008-09-30
Thanks for the information.  You have a Broadcom 4318 wireless chipset (in case you care to know).  I think that the easiest way to get it working in your case will be to use ndiswrapper, which will allow you to drive it using Windows drivers (there are also native Linux drivers that would support your card, but they would be harder to install without any pre-existing Internet connection available).  To get the card working with ndiswrapper, please follow these steps:

1. in Windows, download this file: [http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip](http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip)  You will need to transfer the file somehow to your Ubuntu system, and save it on the desktop there.  One way of doing this would be to burn the file onto a CD.  Another way is to install ext3 drivers in Windows, which will allow you to access your Ubuntu file system from within Windows.  You can find an ext3 driver and installation instructions at [http://www.fs-driver.org/](http://www.fs-driver.org/)

Whichever route you go, make sure that the file Driverv3100640.zip is saved to your desktop on Ubuntu (the path to your desktop on your Ubuntu system is /home/<username>/Desktop).

2. insert your Ubuntu live CD into your drive
3. go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, you will see a section labeled "Installable from CD-ROM/DVD," and you should see a checkbox in that section to enable the use of your CD as a repository.  Make sure that this box is checked, then close the window.  If you're asked about reloading the sources list, say yes.

4. open up a terminal (Applications>Accessories>Terminal) and run the following commands:

```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
cd ~/Desktop
unzip Driverv3100640.zip
cd Driver/WinXP/
sudo ndiswrapper -i bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
sudo gedit /etc/init.d/wifi-fix.sh
```

A blank file should now be open.  Add to the file these lines:

```
#!/bin/bash

rmmod b43
rmmod b44
rmmod b43legacy
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
```

Then save and close the file, and continue with these commands:

```
cd /etc/init.d
sudo -s
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh
```

If you get any error messages while trying to run any of the above commands, please post them here.  Otherwise, reboot, and your wireless should work.  You can view a list of wireless networks by left-clicking on the icon that looks like two computer screens (it should be in the top-right corner of your screen).  If your wireless still doesn't work after a reboot, please post the output of:

```
ndiswrapper -l
dmesg | grep -e ndis -e wlan
sudo iwlist scan
lsmod | grep -e ndis -e ssb
```

I know this is a lot of work, but it's tricky to do this without any Internet connection, and I want to make sure that we cover all possible bases so that this has the highest likelihood of succeeding on the first try (if it doesn't, however, don't worry; we'll figure out what's wrong and fix it).  I need to go to sleep for now but will be back tomorrow.

---

### Post by MyNameIsDerek85 on 2008-09-30
I'm going to bed myself, so I'll try this when I get home from work tomorrow. Thanks for all your help so far, though. 

I was almost going to uninstall the OS, but on a hunch I decided to try asking for help on the forums as a last resort before I gave up on what seems to be a nice OS. So, if we can get wireless working, I can honestly say that I will definatly be keeping Ubuntu.

---

### Post by MyNameIsDerek85 on 2008-09-30
Well, the good news is that I think we're *really*close. The only errors that I got were minor errors that included not being able to contact certain internet websites, but I ignored them and continued on. 

When I restarted my computer, I got a message that said new hardware drivers were ready to be installed. One of those drivers was, of course, my broadcom wireless driver. So, I clicked the enable button and it installed (with only one error, which once again included not being able to contact a website, but it still seemed to have installed correctly). I restarted my computer, again and checked my hardware devices and it recognized my wireless driver. However, I still didn't see any networks to connect to. 

So, here's the information that you requested...

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
08:01.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
08:01.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
08:01.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
08:01.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
08:01.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)
08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
08:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

derek@derek-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

derek@derek-laptop:~$ uname -m
i686

``` 

I remember reading something somewhere else when I was trying to do this on my own about a guy who had the same laptop as me. He said that he had a switch on the front of his laptop that enables and disables wireless internet and his problem was that he needed to get that enabled. I'm wondering if that's not the same problem? If that helps you figure something out?

---

### Post by MyNameIsDerek85 on 2008-09-30
Sorry, the above information that I posted was not what you asked for. HERE is the information you requested.

```
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

[   43.820674] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   43.902943] usbcore: registered new interface driver ndiswrapper

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ndiswrapper           192920  0 
ssb                    34308  1 b43
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd

```

---

### Post by pytheas22 on 2008-10-01
Actually, you shouldn't enable the option for the Broadcom driver--that wants to install a proprietary driver, not ndiswrapper (it's a long story and if you want the full explanation I'd be happy to give it when I have time, but just know for now that you should leave the option in Hardware Drivers unchecked).

What is the output when you type these commands (in this order):
```

sudo modprobe -r b43 b44 b43legacy bcm43xx ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail
sudo iwlist scan
```

I think that we are close, as ndiswrapper seems to have been installed properly; now we just need to clean up a few things.

---

### Post by MyNameIsDerek85 on 2008-10-01
Nooo! And here I thought I was doing the right thing by "enabling" that driver. Well, it says "in use" now when I look at it in the "Hardware Drivers", so we might need to change that... (I don't know how if we do).

Anyway, here's what it says when I put in those commands.

```
[  495.211389] ACPI: PCI interrupt for device 0000:08:04.0 disabled
[  495.211557] usbcore: deregistering interface driver ndiswrapper
[  495.224182] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  495.272220] ndiswrapper: driver bcmwl5 (ASUS,02/11/2005, 3.100.64.0) loaded
[  495.272612] ACPI: PCI Interrupt 0000:08:04.0[A] -> GSI 21 (level, low) -> IRQ 20
[  495.281662] ndiswrapper: using IRQ 20
[  495.634088] wlan0: ethernet device 00:19:7d:2c:e3:fd using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[  495.634168] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  495.634297] usbcore: registered new interface driver ndiswrapper
[  495.687245] ADDRCONF(NETDEV_UP): wlan0: link is not ready

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:EF:BA:F8
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

---

### Post by pytheas22 on 2008-10-01
Everything looks good from the command above--ndiswrapper is loaded and you can see wireless networks.  Can you connect if you left-click on the Network Manager icon (should be in the top-right corner of your screen) and choose your network from the list?  If you've rebooted since your last post, please run the commands from post #8 again to get back to the state where ndiswrapper is working (we can clear this all up later so that these changes will be applied automatically).

If that doesn't work, you can try connecting manually by running:

```
sudo iwconfig wlan0 mode managed essid "linksys"
sudo dhclient wlan0
```

That should get you an IP address and connected to the network 'linksys', which seems to be in your neighborhood (however 'linksys' is the only network detected and it seems to have a weak signal; do you have a different network?).

---

### Post by MyNameIsDerek85 on 2008-10-01
Whoa, umm, it didn't show up before (when I originally posted all that information)... But it's showing up now, so don't ask me what happened. Anyhow, I'm officially typing this while I'm using Ubuntu!!! 

If I could jump through this computer and kiss you right now in a totally heterosexual way, I probably would. 

But seriously, thank you a ton.

---

### Post by pytheas22 on 2008-10-01
Well, glad to hear that it's finally solved!  As for making the fix permanent (so that you don't have to run any commands manually to get online), please type this command:

```
sudo gedit /etc/init.d/wifi-fix.sh
```

A file should open.  Please erase whatever's in it, and replace it with this:
```

#!/bin/bash

modprobe -r b43 b44 b43legacy bcm43xx ssb ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up
```

Then save the file, and reboot your computer.  Are you able to get online automatically and seamlessly?  If not, what is the output of:
```

lsmod | grep -e ndis -e b43 -e ssb
cat /etc/init.d/wifi-fix.sh
```

---

### Post by MyNameIsDerek85 on 2008-10-01
Well, it takes a few minutes to get on. I don't know if it has anything to do with it, but both times I tried re-entering that code (the one to check the status of my internet connection) and that's about when it came on... Although, I'm sure I'm just being impatient.

---

### Post by pytheas22 on 2008-10-01
It might be taking a few tries to connect because the signal is flaky (only 12% in the scan).  Did you always get on quickly in Windows?  If you're noticing that it *always* takes a certain number of tries to get on in Linux, even if you move closer to the coffee shop, let me know and we can look into it.

---

### Post by isbront on 2008-10-01
following pytheas22 instructions in above thread went to Systems>Administration>Hardware Drivers except Hardware Drivers is not available in my version of Ubuntu (hardy heron 8.04 )is there somw other way to do this?

---

### Post by pytheas22 on 2008-10-01
> following pytheas22 instructions in above thread went to Systems>Administration>Hardware Drivers except Hardware Drivers is not available in my version of Ubuntu (hardy heron 8.04 )is there somw other way to do this?

Hardware Drivers should definitely be there in Ubuntu 8.04.  Are you sure you are using Hardy?  In earlier versions of Ubuntu, this utility had a different name ('Restricted Drivers' I think).

Either way, Hardware Drivers may not be the key to your problem--it only helps if you a wireless card that has a native Linux driver which is not open-source (I think Broadcom and Atheros cards are the only examples of this).  If you could please post the output of the following commands, I'll see if I can find instructions on how to get things working in your particular situation:
```

lspci -nn
lshw -C Network
lsusb
uname -m
```

Please also let me know if you've done anything thus far to try to make your wireless work.

---

