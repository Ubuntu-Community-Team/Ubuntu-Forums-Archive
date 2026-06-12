---
title: "[SOLVED] Help With Broadcom 4306!!!"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by arashiko28 on 2007-06-25
I have a HP Pavilion ze2000 laptop, the wireless is a Broadcom 4306. I have tried with every existing version of the ndiswrapper. The last one, is supposedly running but can't get to connect to the wireless. I can't know even if its working since none of the 2 leds that indicates connection has ever turned on use ubuntu. when i'm on windows don't have that problem.
On ubuntu it recognizes the device and everything seems to be ok, but can't get a conection! PLEASE HELP!!! I totally depend on the internet!!! without it, I can't continue to use Ubuntu!!!:cry::cry::cry:

---

### Post by Ayuthia on 2007-06-25
Just to get some initial information, what does ndiswrapper -l show?  Also, which set of drivers are you using and where did you get it from?  Also, are you using the 32-bit or 64-bit version of Ubuntu and do you have Windows on a different partition (If so, which version of Windows)?

---

### Post by Elotero on 2007-06-25
I had the same problem till a day ago.. i foud the right instructions ... after using all the info i restarted and my LED came back on for wireless.. big progress...i can see my network now.. downside to that is i cant connect to it... the directions on how to cure your problem are in here on one of my other posts... i will try and find the link.. stay tuned..

---

### Post by kevdog on 2007-06-25
Just for starters, tell us about your networking card (usb,pci,pcmcia).  Sounds like you have ndiswrapper installed, lets just check and see if the installation is OK.  Please post:
lspci
lsusb
ndiswrapper -v
ndiswrapper -l

32 vs 64 bit??

---

### Post by Kobalt on 2007-06-25
Sometimes you need to remove the avahi deamon in order to get the bcm4306 running with Ndiswrapper : ```
sudo update-rc.d -f avahi-daemon remove
```

---

### Post by arashiko28 on 2007-06-25
Ok, ok! I'll answer all the questions. 
This is an HP Pavilion ze2000 laptop, 32-bit
Now this are the responses terminal gave me:
I downloaded the ndiswrapper from sourceforge and the wireless card drivers from the HP home page. But the ndiswrapper that it's installed came with the ubuntu cd, since i'm just learning to use linux and don't know how to work as root, as the installation instructions asks.
Please help!!! I totally depend on data show presentations!!! and the system is wireless. Also can't connect to the projector trough the analog-rgb cable, but one step at the time. Here's the info you asked for:

~$ lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller

03:00.0 Ethernet controller: D-Link System Inc DFE-690TXD CardBus PC Card (rev 10)


lsusb

Bus 004 Device 003: ID 045e:00e1 Microsoft Corp. 

Bus 004 Device 002: ID 2001:f103 D-Link Corp. [hex] 

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 001: ID 0000:0000  

ndiswrapper -v

module version is too old!

utils version: '1.9', utils version needed by module: '0'

module details:

filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko

version:        1.38

vermagic:       2.6.20-16-generic SMP mod_unload 586 



You may need to upgrade driver and/or utils to latest versions available at

[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)


ndiswrapper -l

sp30379a : invalid driver!


Can you help me???

Oh! I almost forgot! This disc only have the ubuntu OS, Windows is on another disc. Fisically.

---

### Post by kevdog on 2007-06-25
You have to choices for your card to install drivers.  The easy way is the bcm43xx-fwcutter approach. The harder way is ndiswrapper.  As you can see from the above, the ndiswrapper package is not installed properly:

> 
ndiswrapper -v

module version is too old!

utils version: '1.9', utils version needed by module: '0'


Ill help you with either you want
Here are the pro's/cons
1. bcm43xx - Way easier to install. Downside (at current time -- likely not in future) - max transfer speed 11Mb/sec
2. Ndiswrapper - Way more tempermental installation - max transfer speed 54 Mb/sec

Ive done both and elected to go with #2 because I thought 54 sounds a heck of a lot better than 11 Mb/sec, however in the end have failed to really see a difference.

What ever you do uninstall ndiswrapper. If you used synaptic or whatever method, use it to reverse the steps and uninstall the package.  If you elect to go with method #2, we are going to have to install ndiswrapper from source.

---

### Post by arashiko28 on 2007-06-26
I preffer ndiswrapper in this case since I had both options using windows, trust me, the difference does exist when you are doing more than mail checking;).
Ok, I updated ndiswrapper, now my new problem is that i installed a driver that I donwloaded from the HP page, it seems that is not for my card, it says that is invalid. I now have the one that originally comes in the installation CD that brings the laptop (couldn't find it, that's why didn't used it before:oops:). But can't manage to uninstall the previous driver i'm trying with what I know, which is: sudo apt-get remove "driver"
I've tried it even inside the SWSetup folder that is inside of drive_c that is inside of .wine
The answer is that couldn't find package.
How do i remove that and install the new one?](*,)](*,)](*,)#-o

Forget all about that of removing old driver, already found out, now, NONE of the drivers seems to be the one!!!! HELP!!! is a BCM4306... :s

---

### Post by kevdog on 2007-06-26
Two things.

One lets just check ndiswrapper installation one more time:
ndiswrapper -v
ndiswrapper -l


If you get no errors with the -v statement (this is a major stumbling block for many - no utils module!!)
do the following
cd /etc/ndiswrapper
sudo rm -R *
then make sure the above directory is empty.

You then need to change into the directory where your wireless driver file is located (where both the .sys and .inf files are located), and then "wrap" the driver inside ndiswrapper
sudo ndiswrapper -l *****.inf <------Put name of file

Check "wrapping" by:
ndiswrapper -l
You should get no errors at this point

---

### Post by arashiko28 on 2007-06-26
ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
sp29361a : invalid driver!

All I need is a working driver, i have the original CD that came with the laptop, but it doesn't have quite clear wich one is the one of my card, since it has two folders, one named WLAN and WLAN2, the one with WLAN has the bcmwl5a.inf file, but i'm a bit unsure about where to put it or how to "wrapp it" with the ndiswrapper, right now, i'll try to install it using wine directly from the CD and see how it turns out.[-o<
This is officially my third week using Ubuntu/Linux, I love it, bot desperately need this wireless working! (I have resisted the temptation of using the windows OS) \\:D/

UPDATE!!!! THIS IS AS FAR AS I'VE GONE UNTIL NOW
No chance to test it until tonight, but i think i'm on the track
:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 
s:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by alexmoon on 2007-06-26
I'm having the same problem with a Dell D800 I got second-hand.

When I type in 'ndiswrapper -v' I get:

utils Error: no version specified!
driver version: 1.38
vermagic: 2.6.20-generic SMP mod-unload 586


Also, the 'wireless' option has completely disappeared from system -> administration -> network, possibly because of something I did wrong trying to follow instructions here:
[http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+4306)
or here:
[http://ubuntuforums.org/showthread.php?t=291088&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=291088&highlight=broadcom+4306)

No idea what I've done wrong or where to go from here...I'm still very new at linux (and general computer fiddling).

Any advice greatly appreciated.

---

### Post by arashiko28 on 2007-07-03
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) follwing this post's directions, I now have wireless!!!

---

