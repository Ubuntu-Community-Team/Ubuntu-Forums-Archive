---
title: "Need help fixing monitor (resolution) in 9.1 Karmic. Absolute Newbie"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by keinad on 2009-11-02
I just started using ubuntu a few days ago (Latest release, 9.10 Karmic Koala?) ..installed it on this old laptop (Toshiba Tecra 8200 (Pentium III 850 MHz, 384 RAM, 20 GB HDD, video card is built in. dunno it's specs.:( )) as a replacement for XP. I've got no experience at all with this OS, or any command line diagnostics..:(

Anyway, here is my problem, when the computer started up I noticed a black border around the desktop. I learned that the OS was only giving me an 800x600 resolution when in fact the LCD can handle 1024x768. When I go to the display settings I don't see any other resolutions. How can I add others?

I tried to find the xorg.conf file in /etc/X11 (as said in other forums)... but it does not seem to exist.So again I get lost.
I got lost using xrandr cause I don't know what I'm doing.:(
Isn't there a gui based program that can help with this? 

I think I just need help with the codes..just guessing that this ain't a hardware problem.
Thanks in advance.:)

I also plan to use a Dell EP172FPb monitor with this and set up a dual screen.. do you think it's possible? I tried setting it up, but only one screen would be used, either the built in LCD or the external..not both at the same time (needed to restart in order to change between both). In the external monitor however, I don't get a black screen border (unlike that I described earlier)...but still the resolution is stuck at 800x600. :(

- Newbie who wants to love ubuntu.:)

---

### Post by sledge73 on 2009-11-02
go to

 system>administration>restricted drivers

 & see if there are any available if there is install them if not open a terminal under

applications>accessories>terminal & type

lspci

copy & paste output into forum

---

### Post by keinad on 2009-11-02
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:07.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)

oooh..this shows the hardware?

---

### Post by sledge73 on 2009-11-02
ya that's how you see what hardware you have. I'm not familiar with that card maybe someone else in the forums might be able to help.

---

### Post by LewRockwell on 2009-11-02
[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

this is a 2ghz box with similar guts and it refused to play nicely with attempts to drive the internal and external screens at different resolutions

your box is older and you'll probably be better served by a lighter distro

.

---

### Post by keinad on 2009-11-03
> **sledge73 said:**
> ya that's how you see what hardware you have. I'm not familiar with that card maybe someone else in the forums might be able to help.
found help.:)
was able to make a xorg.conf file
then
used gksudo gedit /etc/x11/xorg.conf
then pasted
[http://ubuntuforums.org/showpost.php?p=5039883&postcount=12](http://ubuntuforums.org/showpost.php?p=5039883&postcount=12)
seems to work fine for now

---

### Post by joe2005 on 2009-11-03
having the same problem except my driver is intel g35 chipset driver.how did you make xorg.conf.please explain as to a newbie.thanks

---

### Post by AndyBon on 2009-11-04
I have the same problem, (the system does not recognize the external monitor and do not allow to change resolution), which seems a general problem for many. I had the same problem in 8.10, which was magically solved when I upgraded to 9.4 with the laptop connected to the external monitor. I do not know how.
It would be nice if someone could tell:
1. where info about monitors is stored and by which application. I've found an interesting file on .config in the home directory (monitors.xml), mut failed to change it successfully
2. why xorg.conf seems to be rewritten once edited manually (or just not considered)
3. why the Display utility under System->Preferences (which seems in charge of managing these aspects) does not work: the correct resolutions are not available, if you turn off and on a display the correct resolutions appear, but when I've selcted it I've got both the laptop and external screens black, with some problems to recover since xorg.conf was untouched.

Thanks a lot!

---

### Post by peterbe on 2009-11-16
Before about Ubuntu 7.x or 8.x, the live CDs provided an option for setting the display resolution, in case automatic resolution detection failed. This often happens with displays that don't report their resolution in a known way. Usually the resolution choices fall back to 800x600 and below, but sometimes higher resolutions are chosen, like 1600x1200. And sometimes the system never finds a working resolution, so the system effectively freezes, or comes up in text mode only.

The situation where the screen resolution chosen is bigger than the actual screen size can be particularly annoying, since menus for changing the resolution downward may be off the screen, as with Kubuntu.

I recently tried booting the OpenSUSE 11.2 live CD - it does provide a boot-time option for setting resolution - I hope Ubuntu goes back to providing that option in their next release! It would solve a lot of headaches. People just should not have to create and edit an xorg.conf file 'by hand'.

---

### Post by windguy on 2010-01-11
I'm hoping someone can help me out. Luckily I have two monitors or else I wouldn't be posting this. I recently made the jump from windows, finally fed up. I have a 42" Sony Bravia and I cannot get this system to work on the tv. I have a MSI GeForce 8400GS with DVItoHDMI video card sitting on my shelf and I am unable to install it. I tried for two days and it kept booting to normal view. I tried the onboard video which is nvidia i think (below, somewhere) and I still can't get a view on the tv. Only normal view. I have a smaller 17" right now and it works just fine. If anyone can help me out, I would appreciate it very much! Good luck!

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

---

### Post by ernieball on 2010-03-17
Yeah, hi.

I'll just add my own grievance..

Just upgraded to 9.1 from 8 (something..:redface:). I had two monitors in dual screen working perfectly, but after upgrade, I can only mirror. If I try to expand the desktop, both monitors go black :(

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

(may need to add; my second monitor (1st is laptop) is widescreen  which resolution (used 1280x768 ) have given me some trouble with some older vga-cards before, but as I said, worked fine in 8 :))

any help appreciated!:P

---

