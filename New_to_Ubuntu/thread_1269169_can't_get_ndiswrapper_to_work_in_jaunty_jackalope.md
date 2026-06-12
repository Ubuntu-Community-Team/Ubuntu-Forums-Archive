---
title: "can't get ndiswrapper to work in jaunty jackalope"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by Divertech132 on 2009-09-17
hi ive been banging my head against the wall. i can't get ubuntu 9.10 to recognize ndiswrapper.  my chipset is a broadcom 4318. i have an external wirless card that im trying to get it to recognize its an ASUS wireless LAN Card Bus Adaptor IEEE802.11g.  the computer is an hp dv8000

this is one of the threads i followed trying to fix this [http://ubuntuforums.org/showthread.php?t=407663](http://ubuntuforums.org/showthread.php?t=407663) 

in terminal when i get

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
**06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] **802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

next i try to blacklist the driver with

sudo nano /etc/modprobe.d/blacklist

this is the part i really dont get b/c the above command brings me to a screen entitled  
Gnu nano 2.0.9 file: /etc/modprobe.d/blacklist

with the text cd  ~/bcm4318


this does not make any sense sense to me so i continued.

with the command 
sudo aptitude install ndiswrapper ndisgtk cabextractwhich extracted all the programs without a problem
i then went to the hp website and downloaded the driver for my chipset entitled SP30379.exe. i then created a directory /home/sandra/SP30379.exe

using 
cabextract ./SP30379.exe
i extracted all the files to the above directory.

next i used 
ndiswrapper -i ./bcmwl5.inf (to install the required driver) 
followed by 
ndiswrapper -l 
which gave me this:
sandra@sandra-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.2, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.3, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with 'cd'
WARNING: Failed to open config file blacklist.save: Permission denied
WARNING: Failed to open config file blacklist.save.1: Permission denied
WARNING: Failed to open config file blacklist.save.2: Permission denied
WARNING: Failed to open config file blacklist.save.3: Permission denied
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)
sandra@sandra-laptop:~$ 
And i have no idea what that means. please help

---

### Post by wojox on 2009-09-17
Run this:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

And add 

```
blacklist bcm43xx
```

To the very end and save.

---

### Post by Divertech132 on 2009-09-18
k i did that then i rebooted to make shure everything settled right.
next i typed in ndiswrapper again and it gave me the same screen.

sandra@sandra-laptop:~$ ndiswrapper -l 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.2, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.3, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with 'cd'
WARNING: Failed to open config file blacklist.save: Permission denied
WARNING: Failed to open config file blacklist.save.1: Permission denied
WARNING: Failed to open config file blacklist.save.2: Permission denied
WARNING: Failed to open config file blacklist.save.3: Permission denied
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)
sandra@sandra-laptop:~$ 
 thanks for your help also.

---

### Post by Divertech132 on 2009-09-18
also when i try the command 
sudo modprobe ndiswrapper

i get
[sudo] password for sandra: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.2, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save.3, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with 'cd'
WARNING: /etc/modprobe.d/blacklist.save line 2: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist.save.2 line 2: ignoring bad line starting with '^x'
WARNING: /etc/modprobe.d/blacklist.save.3 line 3: ignoring bad line starting with 'cd'
sandra@sandra-laptop:~$

---

### Post by mickgoth on 2009-09-18
im having same problem, im pretty  sure ndiswrapper is installed but every time i try to modprobe it says that same thing about it needing to be .conf... i tried to change it to .conf but wouldent let me
im sure its something easy sorry im a noob lol but can someone help?

---

### Post by Divertech132 on 2009-09-22
guess no one is going to point us in the right direction.:confused:

---

### Post by rajeev1204 on 2009-09-22
> **Divertech132 said:**
> guess no one is going to point us in the right direction.:confused:

Its too early to make that comment.With a little patience and perseverance
you will be amazed at the helpful nature of these forums.

So did you check under main menu>system>administration>hardware drivers to install the drivers for the broadcom card?

Try the official methods first before using third party tools like ndiswrapper.


rajeev.

---

### Post by Divertech132 on 2009-09-22
your right.  ive just been banging my head against the wall trying to get this sorted out.  The official hardware tool is fwcutter.  What im trying to get work is An external wirless card by Asus wireless lan card bus adapter IEEE 802.11.  what im thinking is that when i did a fresh install on my Hp dv8000 the wireless works sort of without using any propietary drivers.  na d that to get my external wireless card to work all i had to do was blacklist the broadcom 4318 wirless board in my computer.  So then ubuntu would have no problem recognizing my external card.
:)

---

### Post by achase79 on 2009-09-22
you should have just had to extract the firmware from the wireless card using the b43-fwcutter package in synaptic package manager.

---

### Post by rajeev1204 on 2009-09-22
> **Divertech132 said:**
> your right.  ive just been banging my head against the wall trying to get this sorted out.  The official hardware tool is fwcutter.  What im trying to get work is An external wirless card by Asus wireless lan card bus adapter IEEE 802.11.  what im thinking is that when i did a fresh install on my Hp dv8000 the wireless works sort of without using any propietary drivers.  na d that to get my external wireless card to work all i had to do was blacklist the broadcom 4318 wirless board in my computer.  So then ubuntu would have no problem recognizing my external card.
:)

Maybe this helps [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

