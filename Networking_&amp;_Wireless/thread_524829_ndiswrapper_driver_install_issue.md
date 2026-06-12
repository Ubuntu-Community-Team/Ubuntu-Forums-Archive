---
title: "ndiswrapper driver install issue"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by EdTheUniqueGeek on 2007-08-13
Would there be a reason why when I install the drivers I need for my wireless that it would list as invalid?

**ed@c400ubuntu:~/ndiswrapper-1.47$ ndiswrapper -l**
wldel48b : invalid driver!

I noticed that when I go to the ndiswrapper directory under /etc that there is a sub-folder there by that same name with the .inf file in there and nothing else. Could this be the problem?
Is the driver just not installing completely?
Thanks ahead of time for your assistance.

---

### Post by EdTheUniqueGeek on 2007-08-14
Any ndiswrapper experts out there that could answer this question?

---

### Post by kevdog on 2007-08-14
Im guessing when you installed the driver the .inf and .sys files were not in the same folder.  The .sys file is actually the driver, but the program reads the .inf file for the instruction on how to install the driver.  

Either remove the driver of give the command:
sudo /etc/ndiswrapper -rf *

Then reinstall driver ensuring .sys and .inf files are located in the same folder where you give the command:

sudo ndiswrapper -i *****.inf

---

### Post by EdTheUniqueGeek on 2007-08-14
That's just it, they are in the same folder.
I'm trying to use the newest Dell drivers that are supposed to make my card WPA capable. All that I did was extract the compress file in Windows to the typical Dell folder that holds all the driver files, copy that entire folder from a USB thumb drive over to the Ubuntu build and then installed the driver using the ndiswrapper switch to reference that folder.
I guess I can try it again. Maybe this time I'll just copy all the driver files from that folder over to the ndiswrapper folder then install?

---

### Post by kevdog on 2007-08-14
If it doesnt work, please type the exact command that you used.  Make sure the size of the .inf and .sys files are not empty (meaning they are not "blank" files).  If you get in a bind, you can open up the .inf file and read it (its a txt file).  Somewhere in the file it should reference the name of the exact .sys file.  Hopefully it will match the name of the .sys file that you have.  If you really really get in a bind, you can simply put the .inf and .sys files in the folder:

/etc/ndiswrapper/<folder name -- dont know what this will be>/

---

### Post by EdTheUniqueGeek on 2007-08-14
I tried everything.
I removed and reinstalled the drivers. It creates the subfolder, as always, under /etc/ndiswrapper but still only puts an .inf file. I did confirm that there is a .sys file and that the .inf references the .sys file.
I even tried just simply copying the files to that subfolder but it still list as an invalid driver.
I've seen other people state that they have had issues with Dell drivers. I beginning to think this might be the issue, these are Dell drivers.

---

### Post by EdTheUniqueGeek on 2007-08-14
Here is the message I get when I attempt to install:

**ed@c400ubuntu:~$ sudo ndiswrapper -i WLDEL48B.INF**
installing wldel48b ...
couldn't open WLDEL48B.INF: No such file or directory at /usr/sbin/ndiswrapper line 217.

Here is line 217 in /usr/sbin/ndiswrapper

  * open(INF, $filename) or die "couldn't open $filename: $!";*

I would almost interpret that ndiswrapper just has an issue with the Dell .inf file.

---

### Post by kevdog on 2007-08-14
You are right about that.  The inf file is referencing the name of a .sys file, which it cant seem to find.  Where did you get your drivers?  Did you check the ndiswrapper website for a possible alternative driver???

---

### Post by EdTheUniqueGeek on 2007-08-14
I got the driver from Dell's site:

[Dell driver link]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R69905&SystemID=LAT_PNT_P3_C400&servicetag=&os=WW1&osl=en&deviceid=2491&devlib=0&typecnt=0&vercnt=2&catid=5&impid=-1&formatcnt=1&libid=5&fileid=90951")

I looked on for alternatives on ndiswrapper's site but could not find any.
I think I am running out of luck.

---

### Post by kevdog on 2007-08-14
Couple of things if you are in a bind.  Read the inf file and see if anywhere up at the top the actual name of the sys file is mentioned as a global variable.  Is the name of the sys and inf file the same??

Are you using the xp drivers??

---

### Post by EdTheUniqueGeek on 2007-08-14
Yes, these are Windows XP drivers (see the link in my previous post).
The .inf and .sys file are the same name. Also, the .inf file does reference the sys.

See attached files.

However, I just noticed for the first time while uploading the two files that the files are all upper case. The .inf file references a .sys file that is lower case. Could this be causing the problem in ndiswrapper and Ubuntu since Linux is case sensitive?

Edit:
I just tried to attach the files but they did not upload. Here is the .inf:

[PHP];
; Copyright 2003, Agere Systems Inc
;

[Version]
Signature="$Windows NT$"
Class=Net
Provider=%DELL%
DriverVer=09/26/2003, 7.86.15.638
ClassGUID={4d36e972-e325-11ce-bfc1-08002be10318}
Catalogfile=wldel48b.cat

;****************************************************************************
; Manufacturer Section
;****************************************************************************
[Manufacturer]
%Dell%               = "Dell Corporation"

;****************************************************************************
; ControlFlags Section
;****************************************************************************
[ControlFlags]
ExcludeFromSelect = *

;****************************************************************************
; Install Section
;****************************************************************************
[Dell Corporation]
%Wldel01.DeviceDesc%=Wldel01.Install, PCMCIA\Dell-TrueMobile_1150_Series_PC_Card-34F2
%Wldel02.DeviceDesc%=Wldel02.Install, PCMCIA\Dell-TrueMobile_1150_Series_PC_Card-C043

;****************************************************************************
; Install section Dell TrueMobile 1150 Series Card
;****************************************************************************
[Wldel01.Install]
AddReg          = Wldel.Addreg.Cards, Wldel.Addreg.Card01
DelReg          = Wldel.Delreg.Advanced
CopyFiles       = Wldel.CopyFiles, Wldel.CopyFiles.Cfg
Characteristics = 0x84
BusType         = 8
DriverVer=09/26/2003, 7.86.15.638

[Wldel01.Install.Services]
AddService      = wldel48b, 2, Wldel.Service, Wldel.EventLog

[Wldel01.Install.CoInstallers]
CopyFiles       = Wldel.CoInst.Files
AddReg          = Wldel.CoInst.Reg

[Wldel.Addreg.Card01]
HKR,,VendorDescription,,"Dell TrueMobile 1150 Series Card"

;****************************************************************************
; Install section Dell TrueMobile 1150 Series Mini PCI Card
;****************************************************************************
[Wldel02.Install]
AddReg          = Wldel.Addreg.Cards, Wldel.Addreg.Card02
DelReg          = Wldel.Delreg.Advanced
CopyFiles       = Wldel.CopyFiles, Wldel.CopyFiles.Cfg
Characteristics = 0x84
BusType         = 8
DriverVer=09/26/2003, 7.86.15.638

[Wldel02.Install.Services]
AddService      = wldel48b, 2, Wldel.Service, Wldel.EventLog

[Wldel02.Install.CoInstallers]
CopyFiles       = Wldel.CoInst.Files
AddReg          = Wldel.CoInst.Reg

[Wldel.Addreg.Card02]
HKR,,VendorDescription,,"Dell TrueMobile 1150 Series Mini PCI Card"
HKR,,miniPCI,,"1"

;****************************************************************************
; Default NDI Section
;****************************************************************************
[Wldel.Addreg.Cards]
HKR,Ndi\Interfaces,UpperRange,0,"ndis5"
HKR,Ndi\Interfaces,LowerRange,0,"ethernet"
HKR,Ndi,Service,0,"wldel48b"

HKR,,OSType,,"32"
HKR,,DriverVariant,,"2"
HKR,,DriverMajor,,"7"
HKR,,DriverMinor,,"86"
HKR,,DriverEnable,,"1"
HKR,,Configured,,"1"
HKR,,NDT,,"1"
HKR,,DesiredSSID,," "

; OwnChannel
;
HKR,Ndi\params\OwnChannel,          ParamDesc,  0, %CHANNEL%
HKR,Ndi\params\OwnChannel,          Type,       0, enum
HKR,Ndi\params\OwnChannel,          Default,    0, 0
HKR,Ndi\params\OwnChannel\enum,     0,          0, %UD%
HKR,Ndi\params\OwnChannel\enum,1,0,"01"
HKR,Ndi\params\OwnChannel\enum,2,0,"02"
HKR,Ndi\params\OwnChannel\enum,3,0,"03"
HKR,Ndi\params\OwnChannel\enum,4,0,"04"
HKR,Ndi\params\OwnChannel\enum,5,0,"05"
HKR,Ndi\params\OwnChannel\enum,6,0,"06"
HKR,Ndi\params\OwnChannel\enum,7,0,"07"
HKR,Ndi\params\OwnChannel\enum,8,0,"08"
HKR,Ndi\params\OwnChannel\enum,9,0,"09"
HKR,Ndi\params\OwnChannel\enum,10,0,"10"
HKR,Ndi\params\OwnChannel\enum,11,0,"11"

;
; Power Management
;
HKR,Ndi\params\PowerMode,           ParamDesc,  0, %POWERMANAGEMENT%
HKR,Ndi\params\PowerMode,           Type,       0, enum
HKR,Ndi\params\PowerMode,           Default,    0, 0
HKR,Ndi\params\PowerMode\enum,      2,          0, %AUTO%
HKR,Ndi\params\PowerMode\enum,      1,          0, %ON%
HKR,Ndi\params\PowerMode\enum,      0,          0, %OFF%

;****************************************************************************
; CopyFiles Section
;****************************************************************************
[Wldel.Copyfiles]
wldel48b.sys

;****************************************************************************
; CopyFiles.Cfg Section
;****************************************************************************
[Wldel.Copyfiles.Cfg]
wcdel48b.exe
wadel48b.dll
wndel48b.cpl
wndel.hlp
wndel.cnt

;****************************************************************************
; CoInstaller Section
;****************************************************************************
[Wldel.CoInst.Reg]
HKR,,CoInstallers32,0x00010000,"wddel48b.dll,WLDeviceCoInstaller"

[Wldel.CoInst.Files]
wddel48b.dll

;****************************************************************************
; Delete old values is the AdvanceTab of the Properties screen
;****************************************************************************
[Wldel.Delreg.Advanced]
HKR,Ndi\params

;****************************************************************************
; Service Section Dell TrueMobile 1150 Series PCCard Driver
;****************************************************************************
[Wldel.Service]
DisplayName     = %Wldel.Service.DispName%
ServiceType     = 1 ;%SERVICE_KERNEL_DRIVER%
StartType       = 3 ;%SERVICE_DEMAND_START%
ErrorControl    = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\wldel48b.sys
LoadOrderGroup  = NDIS

[Wldel.EventLog]
AddReg = Wldel.AddReg.EventLog

[Wldel.AddReg.EventLog]
HKR, , EventMessageFile, 0x00020000,"%%SystemRoot%%\System32\netevent.dll;%%SystemRoot%%\System32\drivers\wldel48b.sys"
HKR, , TypesSupported,   0x00010001, 7

;****************************************************************************
; Destination Directories
;****************************************************************************
[DestinationDirs]
DefaultDestDir          = 11
Wldel.CopyFiles         = 12
Wldel.Copyfiles.Cfg     = 11
Wldel.CoInst.Files      = 11

;****************************************************************************
; Source Disk Names
;****************************************************************************
[SourceDisksNames]
1 = %DISKID%,,,

;****************************************************************************
; Source Disk Files
;****************************************************************************
[SourceDisksFiles]
wldel48b.sys=1
wcdel48b.exe=1
wadel48b.dll=1
wddel48b.dll=1
wndel48b.cpl=1
wndel.hlp=1
wndel.cnt=1

;****************************************************************************
; Localizable Strings
;****************************************************************************
[Strings]
CHANNEL                     = "1. Channel"
POWERMANAGEMENT             = "2. Card Power Management"
UD                          = "Use default channel"
OFF                         = "Off"
ON                          = "On"
AUTO                        = "Auto"
DISKID                      = "TrueMobile 1150 Disk"

Dell                        = "Dell Corporation"

; Dell
Wldel01.DeviceDesc="Dell TrueMobile 1150 Series Card"
Wldel02.DeviceDesc="Dell TrueMobile 1150 Series Mini PCI Card"

Wldel.Service.DispName="Dell TrueMobile 1150 Series PCCard Driver"
[/PHP]

---

### Post by EdTheUniqueGeek on 2007-08-14
Well, I tried renaming all the files to lowercase and installing the drivers again but that didn't help.
I'm still getting the following:


***couldn't open WLDEL48B.INF: No such file or directory at /usr/sbin/ndiswrapper line 217***

In which line 217 states:

*** open(INF, $filename) or die "couldn't open $filename: $!";***

Again it's just probably having issues with the Dell driver or it's a poorly written driver.

---

### Post by kevdog on 2007-08-14
Is your /etc/ndiswrapper directory empty??? 

Also what are the read write permissions on the .inf and .sys files?  Are you in the same directory where these files are located when doing the command below?

I assume you are typing
sudo ndiswrapper -i *****.inf

Are the .inf and .sys file read/write/executable (My permissions on mine are 644)?

Last thing, since Im not sure what is causing the problem

Manually edit the /usr/sbin/ndiswrapper file and at line 217 (just before the problem line) add the following:

print "Inf filename = %filename\n";

Hopefully this will print out what this filename is.  For some reason it seems to be choking on find the name of the .inf file, not the name of the .sys file

Possible try

sudo ndiswrapper -i  <full path to .inf file>

---

### Post by bmartin on 2007-08-14
I downloaded your drivers and installed them myself. I changed the case of the files and they came up invalid, which I'm guessing means you can't use that Windows driver with ndiswrapper for whatever reason.

What is the output of **lspci | grep Network**? If there isn't any information output about your wireless, what's the full output of **lspci**?

---

### Post by bmartin on 2007-08-14
I believe the chipset in question is a Hermes chipset. There appears to be a built-in module to support your wireless device. Try entering **sudo modprobe orinoco** into a terminal. If that doesn't work, try **sudo modprobe orinoco_pci**. Other than that, I'm out of ideas.

---

### Post by EdTheUniqueGeek on 2007-08-15
> Is your /etc/ndiswrapper directory empty???

It is not. It has only a subfolder that is the name of the .inf file.

/etc/ndiswrapper/wldel48b

In this subfolder is only one file, the .inf file.

/etc/ndiswrapper/wldel48b/wldel48b.inf

> Also what are the read write permissions on the .inf and .sys files? Are you in the same directory where these files are located when doing the command below?

I assume you are typing
sudo ndiswrapper -i *****.inf

Are the .inf and .sys file read/write/executable (My permissions on mine are 644)?

Yeah, when I first saw that error referring to 217, I check the permissions. The .inf and .sys file I assigned as read/write/execute. All the other driver files in the folder are read/write.
I am typing that exact command.

> Last thing, since Im not sure what is causing the problem

Manually edit the /usr/sbin/ndiswrapper file and at line 217 (just before the problem line) add the following:

print "Inf filename = %filename\n";

Hopefully this will print out what this filename is. For some reason it seems to be choking on find the name of the .inf file, not the name of the .sys file

Place that line before or after?
Either way I tried it and got the following returned when I tried to install the driver:

[I]installing wldel48b ...
INF filename = %filename[/I]

> Possible try

sudo ndiswrapper -i <full path to .inf file>

Yeah. I tried that too with the same results.

> I believe the chipset in question is a Hermes chipset. There appears to be a built-in module to support your wireless device. Try entering sudo modprobe orinoco into a terminal. If that doesn't work, try sudo modprobe orinoco_pci. Other than that, I'm out of ideas.

Thanks, bmartin.
Yeah, I realize I have built in wireless support for my card with the orinoco drivers but I was trying to install those specific Dell drivers so that I can have WPA capability.
You can following my other troubleshooting steps in this thread:

[http://ubuntuforums.org/showthread.php?t=519223]("http://ubuntuforums.org/showthread.php?t=519223")

I realize it's four pages but what I came down to is that I can't connect to any secured access point, WEP or WPA. I tried all methods on my Apple Airport Extreme - WEP with passphrase, WPA1, WPA2, and so forth - but with no success. I even tried these methods on a Cisco access port at my work with the same result.
So, what it comes down to is that the default install of Feisty for my Truemobile 1150 is that I can't use it on a secure network. But, because of my technical background (I'm a systems engineer in a Windows world wanting to learn more about Linux and use it on my laptop), I realize that WPA is extremely important and want to keep that implemented. Shoot, I would even be happy with WEP passphrase with MAC filtering if I could.

---

### Post by kevdog on 2007-08-15
Oops 

Just learning perl,

Try this instead
```
print "Inf filename = $filename\n";
```

---

### Post by bmartin on 2007-08-15
Why not use the Orinoco drivers with **wicd** and let wicd handle your WPA issues? It has built-in support.

---

### Post by EdTheUniqueGeek on 2007-08-16
kevdog,
I changed it. I have it still after the problem line, line 217. Here is the return:

[I]installing wldel48b ...
Inf filename = /home/ed/R69905/wldel48b.inf[/I]

When I list the drivers in ndiswrapper I still get invalid driver. It continues to create the wldel48b folder under /etc/ndiswrapper with just the .inf file, no .sys file.

bmartin,
I previously tried wicd before attempting to install the Dell drivers with ndiswrapper but I could never connect. I had the option in the drop-down for WPA and it allowed me to enter the passphrase but it would never connect to any WPA with passphrase I attempted to connect to. It would go through the cycle of authenticating, attempt to get an IP but never connect. Even assigning a static IP and not relying on DHCP would never allow me to connect to WPA.
I don't think the default orinoco drivers are WPA capable at all. I have yet to find record anywhere that anyone using the Truemobile 1150 card in the default install of Feisty able to connect with WPA.

---

### Post by kevdog on 2007-08-16
Please post

lspci -nn
lshw -C network

This will help me find drivers so that I can see if I can install them on my computer to see if I get the same error,

---

### Post by EdTheUniqueGeek on 2007-08-16
This is the odd thing that I have seen before that the lspci doesn't even see the mini-pci NIC even though it works and can connect to open access points:
[B]
ed@c400ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577] (rev 04)
00:02.1 Display controller [0380]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78 )
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
02:03.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)[/B]

[B]
ed@c400ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:09:9b:ec
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.129.17.130 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 1
       resources: irq:5
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:bd:1e:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=yes multicast=yes wireless=IEEE 802.11b[/B]

---

### Post by kevdog on 2007-08-16
I think your card is already associated with the orinoco driver, as would be suggested by your output

Two things, can you post the following
modinfo orinoco
lsmod | grep orino

---

### Post by kevdog on 2007-08-16
See these posts:

[http://ubuntuforums.org/showthread.php?t=472912](http://ubuntuforums.org/showthread.php?t=472912)
[http://ubuntuforums.org/showthread.php?p=2837784](http://ubuntuforums.org/showthread.php?p=2837784)

Bail on ndiswrapper - search system logs (logs located in /var/log)

---

### Post by EdTheUniqueGeek on 2007-08-16
I'll check out those links.
Check this out:

[B]ed@c400ubuntu:~$ modinfo orinoco
filename:       /lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/orinoco.ko
license:        Dual MPL/GPL
description:    Driver for Lucent Orinoco, Prism II based and similar wireless cards
author:         Pavel Roskin <proski@gnu.org> & David Gibson <hermes@gibson.dropbear.id.au>
srcversion:     B437119D3B3907777DC4D77
depends:        hermes
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           suppress_linkstatus:Don't log link status changes (bool)
parm:           ignore_disconnect:Don't report lost link to the network layer (int)
parm:           force_monitor:Allow monitor mode for all firmware versions (int)[/B]

[B]ed@c400ubuntu:~$ lsmod | grep orino
orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  1 orinoco_cs
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic[/B]

What are we looking at and what are we looking for with these commands?

---

### Post by kevdog on 2007-08-16
Post this please also:

lsmod | egrep '(orinoco|hostap|prism2)'

---

### Post by EdTheUniqueGeek on 2007-08-16
[B]ed@c400ubuntu:~$ lsmod | egrep '(orinoco|hostap|prism2)'
orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  1 orinoco_cs
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic[/B]

---

### Post by kevdog on 2007-08-16
It looks like drivers (orinoco) are associated with your card.  No need for ndiswrapper.  What exactly is the problem??

What is the result of the following
iwlist scan
ifconfig

---

### Post by EdTheUniqueGeek on 2007-08-16
As stated before to bmartin, the default install of Feisty and build (Orinoco driver) for the wireless works fine for open networks, but I can't connect to secure connections, particularly to WPA.
I wanted to load the Dell drivers, the specific one listed in the link of previous post, because that particular drive makes the card WPA capable.

---

### Post by kevdog on 2007-08-16
OK -- got it :).  I think the problem we are running into is that there does not seem to be a ndiswrapper driver that is going to work.  I consulted the ndiswrapper website on the list of known devices at it was not shown as being compatible -- that doesnt necessarily mean its not compatible either.

What did you try to get WPA up and running?? And do you have a link or some documentation that WPA will not work with your driver??  I just dont know.
We can try configuring configuring wpa strictly from the command line if you want to generate some debugging input to either confirm or deny this assumption.

Here is what I would do
Please post the following:
iwlist scan
ifconfig

We can then try "manual" wpa configuration if you want.  Unfortunately I think ndiswrapper is dead in the water!

***Edit 
Think I answered my own question -- orinoco drivers do not support WPA
Ill keep looking for a solution.

---

### Post by EdTheUniqueGeek on 2007-08-16
I think I have come to the conclusion that there may not, possibly, be a solution until the next kernel update or Ubuntu build...or never.
Thanks for all your help. I really do appreciate it.

---

### Post by kevdog on 2007-08-16
No the answer is prism54 drivers -- specifically the hostap driver.  I think this is developed by prism54.org.  Google around or search the forums for hostap driver.  Ill do the same.

---

### Post by EdTheUniqueGeek on 2007-08-16
I found this.

[http://hostap.epitest.fi/]("http://hostap.epitest.fi/")

However it states under the download section:

*"Note! Host AP driver was added into the main kernel tree in Linux v2.6.14. The version in the kernel tree should be used instead of this external hostap-driver package. The external releases are only for older kernel versions and all the future development will be in the main kernel tree."*

I'm not sure what kernel I am using (what's the bash command?), but I would think that I would have the latest that is compatible with Feisty. And, if so, the Host AP driver would be included.
No?

---

### Post by EdTheUniqueGeek on 2007-08-16
I found the command.
I have kernel version 2.6.20-16-generic.

---

### Post by kevdog on 2007-08-16
Take a look at this thread (its about 1 year old)

[http://ubuntuforums.org/archive/index.php/t-192050.html](http://ubuntuforums.org/archive/index.php/t-192050.html)

Also try starting another thread -- entitled Orinico/Hostap Fiesty -- Need help installing drivers
of something like that

Ill keep with you, but Im navigating uncharted waters at this point.

---

### Post by EdTheUniqueGeek on 2007-08-16
Good find.
Yeah, I'll do that, start another thread to see if someone can help with the Host AP.
Thanks again. You've been a wonderful support.

---

