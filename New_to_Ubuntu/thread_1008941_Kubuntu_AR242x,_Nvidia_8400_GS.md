---
title: "Kubuntu AR242x, Nvidia 8400 GS?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by kamssada on 2008-12-12
OK, this is my day 6 in Kubuntu.  I figured out how to set up my wireless card, from [URL="http://ubuntuforums.org/showthread.php?t=743299& highlight=atheros+ar5007"]http://ubuntuforums.org/showthread.php?t=743299&
highlight=atheros+ar5007[/URL]

It works just fine, the only problem i have is i need to execute this modules every time i start up. Is anyone capable of giving me "detailed" instructions on how to make this modules permanent. I came across some not so useful posts in previous threads. 

```
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```

Second question, i was able to set up my nVidia Corporation GeForce 8400M GS card, and i could visibly see the difference in graphics from when it wasn't set up, only problem is my screen is trailing. [(click here to see a screen shot)]("http://lh6.ggpht.com/_WwWzUS6wsGY/SUIKSegqUfI/AAAAAAAABx8/ZUyYTSGWQvk/s800/ke.jpeg") when i minimize my screen and bring it back up, it takes a hell of a time just to display things normally? got any tips for me... Again please be specific...

I'm a personalization freak on XP/Vista/MAC, i will love to add the cube, set my background change themes, and do all that in my Kubuntu, i found on the [Kubuntu guide]("http://www.kubuntuguide.org/Intrepid")  Compiz, i installed it, edited the settings, but the cube won't even rotate? go tips

third question, is it only me, or Linux is designed to tell people how not so smart they are.. Even with my extensive JAVA, C++, a little of web design and years and years of fixing machines troubleshooting... After using Kubuntu for the first time it felt i was DUMB!:confused:

How can  i make my Kubuntu run at its best and fast? I already alocated 80gb of my HD for this partition, how do i make it use more of my 3gb ram, because right now its slow like a 512

Finally, what other tips could you you give me, no matter how random it is, i'm much eager to master this system, and make it my premier, instead of XP. 

just in case here is my ls... 

```
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

and 

```
-Computer-
Processor		: 2x AMD Turion(tm) 64 X2 Mobile Technology TL-62
Memory		        : 3111MB (525MB used)
Operating System		: Ubuntu 8.10
User Name		: administrator (Administrator)
Date/Time		: Fri 12 Dec 2008 02:18:28 AM EST
-Display-
Resolution		: 1280x800 pixels
OpenGL Renderer		: Unknown
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA NVidia
-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Power Button (FF)
 Lid Switch
 Power Button (CM)
 Sleep Button (CM)
 Video Bus
 Video Bus
 PC Speaker
 HP Webcam
 SynPS/2 Synaptics TouchPad
-Printers-
No printers found
-IDE Disks-
-SCSI Disks-
TSSTcorp CDDVDW TS-L632N
ATA WDC WD2500BEVS-6

```

or

[HTML]Devices
  Processor
  Processors
  AMD Turion(tm) 64 X2 Mobile Technology TL-62  800.00MHz
  AMD Turion(tm) 64 X2 Mobile Technology TL-62  800.00MHz
  Memory
  Memory
  Total Memory  3111612 kB
  Free Memory  1681300 kB
  Buffers  49268 kB
  Cached  907536 kB
  Cached Swap  0 kB
  Active  710636 kB
  Inactive  627108 kB
  High Memory  2227584 kB
  Free High Memory  921444 kB
  Low Memory  884028 kB
  Free Low Memory  759856 kB
  Virtual Memory  3437868 kB
  Free Virtual Memory  3437868 kB
  Dirty  64 kB
  Writeback  0 kB
  AnonPages  380940 kB
  Mapped  100924 kB
  Slab  61776 kB
  SReclaimable  42452 kB
  SUnreclaim  19324 kB
  PageTables  3736 kB
  NFS_Unstable  0 kB
  Bounce  0 kB
  WritebackTmp  0 kB
  CommitLimit  4993672 kB
  Committed_AS  671196 kB
  VmallocTotal  110584 kB
  VmallocUsed  13496 kB
  VmallocChunk  92408 kB
  HugePages_Total  0
  HugePages_Free  0
  HugePages_Rsvd  0
  HugePages_Surp  0
  Hugepagesize  4096 kB
  DirectMap4k  8192 kB
  DirectMap4M  909312 kB
  PCI Devices
  PCI Devices
  RAM memory  nVidia Corporation MCP65 Memory Controller 
  ISA bridge  nVidia Corporation MCP65 LPC Bridge 
  SMBus  nVidia Corporation MCP65 SMBus 
  Co-processor  nVidia Corporation MCP65 SMU 
  USB Controller  nVidia Corporation MCP65 USB Controller 
  USB Controller  nVidia Corporation MCP65 USB Controller 
  Ethernet controller  nVidia Corporation MCP65 Ethernet 
  Audio device  nVidia Corporation MCP65 High Definition Audio 
  PCI bridge  nVidia Corporation MCP65 PCI bridge 
  IDE interface  nVidia Corporation MCP65 IDE 
  IDE interface  nVidia Corporation MCP65 SATA Controller 
  PCI bridge  nVidia Corporation Device 045b 
  PCI bridge  nVidia Corporation MCP65 PCI Express bridge 
  PCI bridge  nVidia Corporation MCP65 PCI Express bridge 
  PCI bridge  nVidia Corporation MCP65 PCI Express bridge 
  Host bridge  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
  Host bridge  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
  Host bridge  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
  Host bridge  Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
  Ethernet controller  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter 
  VGA compatible controller  nVidia Corporation GeForce 8400M GS 
  FireWire (IEEE 1394)  Ricoh Co Ltd R5C832 IEEE 1394 Controller 
  SD Host controller  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter 
  System peripheral  Ricoh Co Ltd R5C843 MMC Host Controller 
  System peripheral  Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter 
  System peripheral  Ricoh Co Ltd xD-Picture Card Controller 
  USB Devices
  Printers
  Printers
  No printers found
  Battery
  Battery: BAT0
  State  charged (load: unknown)
  Capacity  3488 mAh / 6000 mAh (58.13%)
  Battery Technology  rechargeable (LION)
  Model Number  Primary
  Serial Number
  Sensors
  Cooling Fans
  Temperatures
  temp1  48.00°C
  temp2  46.00°C
  temp3  50.00°C
  temp4  44.00°C
  Voltage Values
  Input Devices
  Input Devices
   Macintosh mouse button emulation
   AT Translated Set 2 keyboard
   Power Button (FF)
   Lid Switch
   Power Button (CM)
   Sleep Button (CM)
   Video Bus
   Video Bus
   PC Speaker
   HP Webcam
   SynPS/2 Synaptics TouchPad
  Storage
  IDE Disks
  SCSI Disks
  TSSTcorp CDDVDW TS-L632N
  ATA WDC WD2500BEVS-6[/HTML]

thanks\\:D/

---

### Post by kamssada on 2008-12-12
So far, I got no resp, but its ait... 
I figured out how to make compiz work, by enabling my video card 177, then by looking into enabling repositories, that helped me get the latest updates for my video card... occasionally, the taskbar icons look weird, but except from that, i haven't had any major issue... 

the kubuntu guide is helpful. Still don't know how to make the modules autostart. but i'm working on it... 

[IMG]http://lh5.ggpht.com/_WwWzUS6wsGY/SUL8YDeupGI/AAAAAAAABy0/nLvzn8KbuTA/s800/3.jpeg[/IMG]

ask for the speed, everything is working not like i would like, but ok, the only problem is firefox is damn slow, but Konqueror really earned its name. 

i'm looking for docks and also ways i could integrate text on my desktop, will be helful if someone could at least hint somewhere to look. Ksmoothdock didn't work for me, it came with ubuntu files that ought to make my kubunutu look like ubuntu.. HELL NO!!...  Kdock also didn't work for me. I'm looking into plasmoids.

---

### Post by tomtom1982 on 2008-12-13
Well, could it be that your PC is to slow because of your 800MHz CPU?

KDE 4 is eating performance.

You could try gnome or xfce because compiz works at this, too.

For docks:
Try Avant Window Manager (AWM). It's the best linux dock at the moment (for me).

Just open a console and type

```
sudo apt-get install avant-window-navigator
```

(it's in universe repository) or install via Synaptic.

After this it will look like this:
[http://www.youtube.com/watch?v=B69aW2Pikjo](http://www.youtube.com/watch?v=B69aW2Pikjo)

Edit: You could also look for emerald. 

```
sudo apt-get install emerald
```

That's an window decorator. You can change a lot with it. With compiz, emerald and AWM you also can make looking your linux like Leopard. I've a very detailed description for do this.
But not here. I'm not at home until monday. If you want to have it, simply read in into this thread. I only have to change it to english (it's in german ;-I).

---

### Post by kamssada on 2008-12-13
> **tomtom1982 said:**
> Well, could it be that your PC is to slow because of your 800MHz CPU?

KDE 4 is eating performance.

You could try gnome or xfce because compiz works at this, too.

For docks:
Try Avant Window Manager (AWM). It's the best linux dock at the moment (for me).

Just open a console and type

```
sudo apt-get install avant-window-navigator
```

(it's in universe repository) or install via Synaptic.

After this it will look like this:
[http://www.youtube.com/watch?v=B69aW2Pikjo](http://www.youtube.com/watch?v=B69aW2Pikjo)

Edit: You could also look for emerald. 

```
sudo apt-get install emerald
```

That's an window decorator. You can change a lot with it. With compiz, emerald and AWM you also can make looking your linux like Leopard. I've a very detailed description for do this.
But not here. I'm not at home until monday. If you want to have it, simply read in into this thread. I only have to change it to english (it's in german ;-I).

lol thanks for your input, i am using emerald already, the problem with AWN is that it downloads all this files that makes my Kubuntu look like ubuntu, and i had to unistall it the other time. 

Ask for my processor, its actually a 800 mhz X 4 = 2.3 GHz, but now its working fine, please do send me all you can, anything will be helpfull.. thank you...

---

### Post by kamssada on 2008-12-13
I have been trying different things to make my modprobes permanent, i tried this, please tell me if i am doing something wrong? 

this code is to create an autostart script, i think. 
```

echo "sudo modprobe wlan_scan_stasudo modprobe ath_pci" > ~/.kde/Autostart/startwifi.sh
```

it seems like this code give it the permission to execute
```
chmod +x ~/.kde/Autostart/startwifi.sh
```

this brings up kate to edit the script, then i 
```

sudo kate ~/.kde/Autostart/startwifi.sh
```

and then i insert this into kate
```
sudo modprobe ath_pci
 sudo modprobe wlan_scan_sta

```

but it doesn't work :confused:, i did something similar, with 
```

compiz --replace &
``` and it worked... suggestions to make those two commands permanant.

---

### Post by tomtom1982 on 2008-12-18
Sorry, but I´ve had 12-h-working-days so I didn´t had time to reply.

Here is the instruction to make looking the Ibex like the Leopard:

Making your Ubuntu-desktop look like Mac OSX (requires an installed gnome-desktop):

At first you have to download the current version of the Mac4Lin-project. That´s a pool of components which let your gnome-desktop looks like OSX. It contents themes, pictures and layouts for the login-screen. You´ll find it at [HTML]http://sourceforge.net/porjects/mac4lin[/HTML]. Current version is 1.0RC. After download unpack the archive in any folder. 

Only if emerald is currently not installed:
For later installation you have to install emerald via sudo apt-get install emerald. After this you have to start and close emerald. It will make a new folder in your home folder. 

Now open a terminal and change folder with

```
cd <path> 
```

(please insert the folder were you saved mac4lin instead of <path>, /home/user/documents/ for example)

Now you type the following into terminal:

```
./Mac4Lin_Install_v.10_RC.sh
```

This will start the installation script.

During the installation, you will be asked for your password. Please type Y and Enter, after this insert your pass. The first changes will appear on your desktop. The wallpaper and the window-designs will change.

If nothing is changed, you have to activate it by opening „System->Preferences->Appearance“. There you change to „theme“. Here you see the themes „Mac4Lin_Aqua“ and „Mac4Lin_Graphite“. You´ll activate a theme by clicking it. You also can install the themes manually by clicking „install“ and choosing into the folder you downloaded the files. There you go to folder „GTK“ and choose the theme-archive „Mac4Lin_GTK_v1.0_RC.tar.gz“.

Now you have to change fonts. Open „System->Preferences->Appearance“ and change to register „fonts“. Change the fonts from top to bottom like this:
„Bitstream Vera Sans Roman“ 		Size 10
„Aquabase“				Size   9
„Trebuchet MS Standard“			Size   9
„Lucida Grande Bold“			Size   9
„Bitstream Vera Sans Mono Roman“	Size 10

After this click on „close“.

On your screen you have a Mac OS X-Wallpaper. For more wallpapers please visit [HTML]http://sourceforge.net/projects/mac4lin[/HTML] and download the file „Leopard Wallpapers“ from section „Downloads->Additional Files“. Please unpack the downloaded file into any folder. Open „System->Preferences->Appearance“, go to „Background“ and open these folder to choose another Mac OS X-Wallpaper.

Please install AWN via 

```
sudo apt-get install avant-window-navigator
```

Now open „System->Preferences->Awn Manager“. Go to „Themes“ and click on „“.Choose the folder you´ve download the Mac4Lin-files, go to folder „AWN“ and choose the only archive in this directory. After this click on „Apply“.

Change Log-In-Screen:
Open „System->Administration->Login Window“ and go to register „Local“. Click on the box in front of „Mac4Lin GDM v1.0 RC“ and make it the only active box. After this, click on „Background color“ and type into „Color name“: #E5E5E5

After this you will get a new login screen after restarting ubuntu.

You also can install screenlets with

```
sudo apt-get install screenlets compizconfig-settings-manager
```.

That´all.

Sorry for my English, it´s not my native language, only what I learned at school ;-)

---

### Post by beausoleilm on 2008-12-30
Did you fix you trailing problem ? I have the same here and I don't find any information about that.

Thanks !

---

