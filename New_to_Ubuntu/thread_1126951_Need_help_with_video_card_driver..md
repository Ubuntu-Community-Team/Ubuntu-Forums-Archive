---
title: "Need help with video card driver."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by ricdtinsley on 2009-04-15
Need help with video card driver. I am using a 
 FEATURE    	  SPECIFICATION
Motherboard description 	

    * Manufacturer's name - TUW-LA
    * HP/Compaq name - Greenland

Motherboard supplier 	ASUS
System BIOS supplier 	ASUS Award
Form factor 	UATX
Processor brand 	Intel
Processor socket type 	Socket 370
Processor family 	Celeron
Maximum approved processor 	1.4 MHz Celeron
Processor front side bus frequency 	133/100/66 MHz
Chipset name 	Intel i810E
Chipset "North Bridge" 	GMCHE
Revision/Stepping 	A0
Chipset "South Bridge" 	ICH
Revision/Stepping 	B1
Super I/O 	SMsC LPC47M102
Revision/Stepping 	---------
Flash BIOS device 	FWH 4Mbit
Memory type 	SDRAM
Memory speed 	PC133 (runs @ PC100)
Memory sockets 	2 DIMM
Maximum memory 	512MB
Graphics supplier 	Intel
Graphics configuration 	Down, in chipset
Onboard graphics memory 	UMA (Intel DVT)
Graphics connector (AGP) 	None
TV-Out device 	Chrontel CH7007
TV-Out configuration 	Daughtercard
Audio 	AC97 Down 	
AC’97 CODEC device 	Crystal CS4299
Audio jacks (legend below) 	M, LI, LO, SO, M/G
M 	Microphone
LI 	Line In
LO 	Line out
SO 	Speaker
M/G 	Midi/Game
Ethernet 10/100 LAN supplier 	Realtek 8100
Ethernet configuration 	PCI, Down
IDE UDMA modes 	ATA-66/33
Expansion slots (AGP/PCI/Exten) 	3 PCI
USB ports 	4
USB front/back options 	2F + 2 B
Serial, parallel, floppy, PS2 Kbd and Mouse 	2S, 1P, 1F, PS2 K+M
Serial port front chassis option 	Yes
Available Mfg options (legend below) 	GLAS, TV Out
A 	Audio down on motherboard 	
C 	External L2 cache on motherboard
E 	1394 on motherboard
G 	Graphics down (on motherboard or in chipset)
L 	LAN on motherboard (Ethernet) P - PCMCIA slot
S 	S3 power management support
T 	TV-out on motherboard
U 	Graphics card (up, not on motherboard)

---

### Post by RedSingularity on 2009-04-15
What is the problem?

---

### Post by ricdtinsley on 2009-04-15
the video is not configured write I can't even see to update the os

---

### Post by RedSingularity on 2009-04-15
So all you see is a terminal prompt when you start the computer?  Try typing "startx" in there.

---

### Post by josecuervo86 on 2009-04-15
Che, que onda?? de repente se internacionalizo el foro....

---

### Post by ricdtinsley on 2009-04-15
the os comes up but part of the picture is missing and when I go to update the os or download a program a window pops up with no text in it friend told me I needed to install the drivers but the only drivers avalible are for windows xp.

---

### Post by ricdtinsley on 2009-04-15
and when I open the terminal a big white window pops up

---

### Post by RedSingularity on 2009-04-15
Go to System>Admin>Hardware drivers.  See if anything is in there to activate.

---

### Post by ricdtinsley on 2009-04-15
it says theres no drivers in use

---

### Post by RedSingularity on 2009-04-15
Do you know your video card you are using?  Type "lspci" in terminal and post the output.

---

### Post by ricdtinsley on 2009-04-15
when I open the terminal a big white window pops up. and the video card is intergraded the specs. from the manufaturer are in my first post

---

### Post by RedSingularity on 2009-04-15
Oh ok, press Ctl+Alt+F1 and then enter lspci in there.

---

### Post by ricdtinsley on 2009-04-16
when i hit Ctl+Alt+F1 the screen went black and froze up. If I was to buy a video card and reinstall the os would it auto configure?

---

### Post by RedSingularity on 2009-04-16
Yeah.  Why, you thinking about getting a newer one?

---

### Post by ricdtinsley on 2009-04-16
do you happen to know of one that is compatible with ubuntu the only problem is it would have to be a standard pci card

---

### Post by RedSingularity on 2009-04-16
Standard PCI hu?  Really any will do.  The thing is that right now you have a intergrated graphics card.  Thats the problem.  There probably is a way to get it working if you really want it.  But yeah, any modern card will be fine.  By NO means does it have to be top of the line either.

---

### Post by RedSingularity on 2009-04-16
Oh and personally i would go with Nvidia.  Its supported very well in linux.

---

### Post by ricdtinsley on 2009-04-16
ok thanks for your help:KS

---

### Post by NipplesAndLicks on 2009-05-01
this is what i got 


nipplesandlicks@nipplesandlicks-desktop:~$ lspci
.00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by RedSingularity on 2009-05-01
Whats the problem?  Same thing with the video driver?

---

### Post by NipplesAndLicks on 2009-05-01
yes and cant find a driver on the net.

---

### Post by RedSingularity on 2009-05-01
Did you go to System>Admin>Hardware Drivers and look in there?

---

### Post by NipplesAndLicks on 2009-05-01
yes found noting :(

---

### Post by RedSingularity on 2009-05-01
Ok try this in terminal, "sudo apt-get install xserver-xorg-video-i810"

---

### Post by NipplesAndLicks on 2009-05-01
got this



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-video-i810 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xserver-xorg-video-intel
E: Package xserver-xorg-video-i810 has no installation candidate

---

### Post by RedSingularity on 2009-05-01
Ok try this "sudo apt-get install xserver-xorg-video-intel"

---

### Post by NipplesAndLicks on 2009-05-01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


is that saying i had the driver this hole time?

---

### Post by RedSingularity on 2009-05-01
Yep......what makes you think you dont have it?  You having problems with your display?

---

### Post by NipplesAndLicks on 2009-05-01
trying to get linux beryl to work... and when i go to preferences->appearance->visual effects and click one i get this "Desktop effects could not be enabled"

---

### Post by RedSingularity on 2009-05-01
Ohh how old is that computer?

---

### Post by NipplesAndLicks on 2009-05-01
2003

---

### Post by RedSingularity on 2009-05-01
Download [THIS]("http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/8203/eng/i915Graphics.tar.gz&agr=&ProductID=1044&DwnldId=8203&strOSs=&OSFullName=&lang=eng") and extract the folder to your desktop.

---

### Post by RedSingularity on 2009-05-01
The extracted folder should be called dripkg correct?

---

### Post by NipplesAndLicks on 2009-05-01
yes... sorry it took so long

---

### Post by RedSingularity on 2009-05-01
No problem

In terminal type:
cd ~/Desktop/dripkg

then...

sudo sh install.sh

---

### Post by NipplesAndLicks on 2009-05-01
this is what i got 


/bin/ed
/usr/bin/awk
/usr/bin/sort
/usr/bin/md5sum
[: 1159: 6: unexpected operator
[: 1159: 6: unexpected operator
[: 1159: 6: unexpected operator
[: 1159: 6: unexpected operator
[: 1159: 1: unexpected operator

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver: 

Driver Name    : gdg
Description    : Intel 830M/845G/852GM/855GM/865G/915G Driver
Architecture   : I386
Build Date     : 20040604
Kernel Module  : gdg

Optional Information

Driver Version      :  
Special Description :  

Press ENTER to continue or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

Select from the following options:

  1. Install driver (default)
  2. Uninstall driver

Enter reponse [1-2], or CTRL-C to exit
1
get_osname()
[: 1248: 1: unexpected operator
[: 1361: 0: unexpected operator








DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the [: 1361: 0: unexpected operator
DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


[: 1361: 0: unexpected operator
[: 1361: unexpected operator

Compiling DRM module...install.sh: 1361: Syntax error: Bad fd number
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$

---

### Post by RedSingularity on 2009-05-01
Looks like that driver wont work either......

How is the screen resolution?  Is that correct for your monitor?

---

### Post by NipplesAndLicks on 2009-05-01
this is what i have for a pic.... this what your looking for?

i have a 16 inch monitor

[IMG]http://i27.photobucket.com/albums/c195/nipplesandlicks/Screenshot-DisplayPreferences.png[/IMG]

---

### Post by RedSingularity on 2009-05-01
Yeah that looks fine.  Maybe you cant enable Compiz.  

Try "sudo apt-get install compiz"

---

### Post by NipplesAndLicks on 2009-05-01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


hmmm

---

### Post by Trev2HI on 2009-05-01
Perhaps not the most desirable of workarounds, but the user in this thread ([http://ubuntuforums.org/showthread.php?t=383710]("http://ubuntuforums.org/showthread.php?t=383710")) had the same integrated controller and was able to get it to work by installing xubuntu, then ubuntu-dekstop on top of xubuntu.

---

### Post by RedSingularity on 2009-05-01
> **Trev2HI said:**
> Perhaps not the most desirable of workarounds, but the user in this thread ([http://ubuntuforums.org/showthread.php?t=383710](http://ubuntuforums.org/showthread.php?t=383710)) had the same integrated controller and was able to get it to work by installing xubuntu, then ubuntu-dekstop on top of xubuntu.


That is something you can definitely try.  I was looking at it earlier.

---

### Post by NipplesAndLicks on 2009-05-01
im lost lol....


i typed
sudo apt-get install xserver-xorg-video-i810
and my screen blinked and got this



nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ Reading package lists... Done

bash: Reading: command not found
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ Building dependency tree       
bash: Building: command not found
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ Reading state information... Done
bash: Reading: command not found
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ compiz is already the newest version.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bash: 0: command not found
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ Reading package lists... Donebash: Reading: command not found
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ Building dependency tree       
bash: Building: command not found
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ Reading state information... Done
bash: Reading: command not found
nipplesandlicks@nipplesandlicks-desktop:~/Desktop/dripkg$ compiz is already the newest version.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity

---

### Post by RedSingularity on 2009-05-01
You can try using Xubuntu.  Its another version of ubuntu made for slower graphics and memory.  Go to ubuntu website and download Xubuntu 9.04.  Desktop effects will work with that version.

---

### Post by NipplesAndLicks on 2009-05-01
> **Shadow121 said:**
> Did you go to System>Admin>Hardware Drivers and look in there?

> **Shadow121 said:**
> Ok try this in terminal, "sudo apt-get install xserver-xorg-video-i810"

> **Shadow121 said:**
> You can try using Xubuntu.  Its another version of ubuntu made for slower graphics and memory.  Go to ubuntu website and download Xubuntu 9.04.  Desktop effects will work with that version.

is that another lunix? i have 9 cd of lunix

---

### Post by Niniel on 2009-05-01
It's another version of Ubuntu, so not quite a totally different Linux. But it sounds like it comes with a driver that'll work with your graphics system.

---

### Post by RedSingularity on 2009-05-01
Its the same as ubuntu but with the Xfce desktop.  It is linux yes.

---

### Post by NipplesAndLicks on 2009-05-01
this is what CD i have would anyone one work that you know of

[http://cgi.ebay.com/NEW-5-PACK-LINUX-XP-2009-VERSION-OPERATING-SYSTEM-PLUS_W0QQitemZ200335612930QQcmdZViewItemQQptZUS_Software?hash=item200335612930&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1307|301%3A1|293%3A1|294%3A50](http://cgi.ebay.com/NEW-5-PACK-LINUX-XP-2009-VERSION-OPERATING-SYSTEM-PLUS_W0QQitemZ200335612930QQcmdZViewItemQQptZUS_Software?hash=item200335612930&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1307|301%3A1|293%3A1|294%3A50)

---

### Post by RedSingularity on 2009-05-01
Unfortunately none of those are it.  Do you have any blank CDs?

---

### Post by modmadmike on 2009-05-06
lol had the same problem with mine till I started using the server kernel [ODD AS HELL] :)
I also have it on my Eee PC 901 but it might work with 9.04 [never had the time to install it, for I remember 8.04 was a pain in the @$$ to get working on this pc].

---

### Post by halitech on 2009-05-06
if you have Ubuntu up and running, just open a terminal and run
```
sudo apt-get install xubuntu-desktop
```
and that will install the XFCE desktop that Xubuntu uses. You don't need to download and install fresh.

---

### Post by Culip on 2009-05-18
Has anyone succeeded?

I use Ubuntu 9.04 Jaunty on Intel 915 and has tried to connect with a sub monitor with the resolution of 1920x1200.

Honestly, I'm looking for any method other than installing xubuntu-desktop because my disk space is limited.

Also, I got the following message when I tried to install "dripkg."
```
[: 1361: 0: unexpected operator
[: 1361: unexpected operator

Compiling DRM module...install.sh: 1361: Syntax error: Bad fd number
```

Thanks.

---

### Post by xophelorak on 2009-09-05
I have this intel celeron mobo with integrated graphics card (the TUW-LA). It works fine in ubuntu server with standard ubuntu-desktop. My only problem with the video is that Quakelive isn't working on this box : \ So I was looking for maybe linux drivers for the video card to see if that would help make quakelive work.

---

