---
title: "Getting 11.04 to install a Canon driver"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Edward in CT on 2011-05-17
Hello
I bought a Canon MF 4350d and couldn't get it to work on 11.04.  Looked on this forum and found that I had to do a few tricks to get the deb file (downloaded from Canon) to install.  It imported and was installed easily, but now 11.04 doesn't recognize the driver and when I search for it, I get no results.  How do actually tell the OS where the printer driver is and how to install it?  Where are the files stalled after I unpackage them?  

I'm a total novice.  I need simple instructions.

Thanks

Ed

---

### Post by ClientAlive on 2011-05-18
> **Edward in CT said:**
> Hello
I bought a Canon MF 4350d and couldn't get it to work on 11.04.  Looked on this forum and found that I had to do a few tricks to get the deb file (downloaded from Canon) to install.  It imported and was installed easily, but now 11.04 doesn't recognize the driver and when I search for it, I get no results.  How do actually tell the OS where the printer driver is and how to install it?  Where are the files stalled after I unpackage them?  

I'm a total novice.  I need simple instructions.

Thanks

Ed


I don't have a cannon printer and I have to get to bed right now but I'll check in on you in the morning if you're still around and do what I can to help. Hopefully someone else comes along that's dealt with it before.

Have a blessed night.

Jake
:)

---

### Post by Edward in CT on 2011-05-18
Thanks.  I'm hoping this is a straightforward fix.
I downloaded the driver from Canon and at first I couldn't install it with Package Manager but then I looked through the threads on this forum and someone else had had the same problem.  I implemented their fix and all went well.  Only I can't actually get 11.04 to find the installed driver.  I'd love any help you can spare.

Thanks

---

### Post by wep940 on 2011-05-18
If you can send the link to Canon's site where the drive is, I can take a look at it.  Also, what procedure did you follow to install the .deb file?

---

### Post by wep940 on 2011-05-18
I did find something I think should help, if it's not already what you have done. This link: [http://forums.linuxmint.com/viewtopic.php?f=51&t=62152]("http://http://forums.linuxmint.com/viewtopic.php?f=51&t=62152") gives info on making this work, albeit in 10.10. There is a link listed in the thread there for instructions, however you also need to read the last post in the thread as it explains somethings about packages having been renamed and how to get around that.

---

### Post by Edward in CT on 2011-05-18
I got the driver from here: [http://support-sg.canon-asia.com/contents/SG/EN/0100270807.html](http://support-sg.canon-asia.com/contents/SG/EN/0100270807.html) but initially couldn't install the .deb file so I followed the advice from this thread: [http://ubuntuforums.org/showthread.php?t=1745833](http://ubuntuforums.org/showthread.php?t=1745833)  on Ubuntu forums and it worked for intallation but when I plug the USB port attached to the printer into the computer, the OS can't find the driver.
 
Thanks again for any help.
 
Ed.

---

### Post by wep940 on 2011-05-18
Checked that thread - it doesn't include 1 step that seems to be in the one I posted, but it also includes an extra step that seems to be needed, so maybe it's a wash.
 
This is a dumb question, but did you get the driver that matched your ubuntu architecture - 32-bit for "normal" ubuntu, 64-bit for 64-bit ubuntu?  Remember it's the actual architecture of ubuntu you installed, not the hardware, that will determine the driver you need - but of course if your hardware isn't 64-bit you wouldn't be able to use 64-bit ubuntu anyway.
 
I would try plugging the device in again, and not doing anything else for a minute or so, then going into a terminal window and do the following:
 
dmesg 40 | tail
 
This will show the last 40 lines of the system log.  Perhaps there will be a message there as to the printer and why it isn't recognized.  If you're not sure, post the output in a reply here and we can go from there.
 
Be aware I don't have your printer, so I can't try things here first.  However, I'd like to help as much as I am able to.

---

### Post by spillage2 on 2011-05-18
I know with a canon ip90 the driver is under a diff model. I think it was the ip2000 for me.

Just go to printer and then add.

sorry I know its not much help but maybe worth a google search.

spill

---

### Post by ClientAlive on 2011-05-18
Glad you guys came along. I don't have that printer or know enough about Linux yet to be of much use. I think I'll leave it to the experts this time.

Peace out fellas

---

### Post by Edward in CT on 2011-05-18
Here is the output...

[  100.799868] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  102.889816] Intel AES-NI instructions are not detected.
[  103.123848] padlock_aes: VIA PadLock not detected.
[  110.976054] wlan0: no IPv6 routers present
[  423.008206] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  423.247683] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04A9 pid 0x26EE
[  423.252406] usblp1: USB Bidirectional printer dev 4 if 2 alt 0 proto 2 vid 0x04A9 pid 0x26EE
[  423.252511] usbcore: registered new interface driver usblp
[  424.455914] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[  424.459138] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1

don't know what to make of it.  Thanks

Ed

---

### Post by wep940 on 2011-05-18
Looks like it's picking up the printer - another dumb question:  have you gone to system/administration/printers, do an add and have it search for the printer?  I *think* that even if you install a driver you still have to add the printer.

---

### Post by Edward in CT on 2011-05-19
I do that and then it doesn't find the driver and then it gives me the list of Canon printers but the "image Class MF 4350d" isn't on the list.  Is it listed under another name?

---

### Post by wep940 on 2011-05-19
Ah, so can you possibly take a screenshot of what it shows for selections and post it here?  Perhaps we can find something that will work.  ;)

---

### Post by ClientAlive on 2011-05-20
I don't know if it's of any use but I have a link I'll post at the bottom of this post. What I've gotten to wondering is if there is some way to manually configure the thing through the command line. If one knew the config file or whatever it is and where it is located they could open it in a text editor and type in whatever needed be for the driver to be added to the list in the printers section of of the control panel or to just plain manually configure it.

Now I don't think what they are talking about at this link is your printer/ driver but maybe some part of what they are doing gives some fuel for how to go about something like that.

One of the things I was looking at at that link is some of the code they used near the end of the page. Specifically something they used under a heading called "Diagnostics". That code they ran is:

```

sudo ccpdadmin

```

I just tried to run that command on my machine here and it told me the command is not found. I'm running 10.04 though. Maybe it works with 11.04. I don't know.

I also noticed in that part of the page a path to that it called the "CUPS_ConfigPath". It was shown as:

```

/etc/cups/

```

I just went there on my machine using the cd command and looked at what is in that folder. Here is what is on my machine in that folder:

```

shine@lineNine:~$ cd /etc/cups/
shine@lineNine:/etc/cups$ ls
acroread.conf   cupsd.conf.default  **printers.conf.O**  ssl
classes.conf    pdftops.conf        raw.convs        subscriptions.conf
classes.conf.O  ppd                 raw.types        subscriptions.conf.O
cupsd.conf      printers.conf       snmp.conf

```

Do you see all the ones ending in ".conf" or containing it? Don't quote me on this but I think those are configuration files. Let's choose one to look at just to see what it's like ok?

Look at the item I bolded in the above (and please note that I only bolded it to indiacate that is the one I chose to open, not that it is necessarily the right one). That is the file I chose to open and look at. I had to log in as root to have the proper permission to open it but when I did - here is what is in there:

```

# Printer configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
[B]<Printer EPSON-WorkForce-520>
Info EPSON WorkForce 520
Location Work Office - USB
MakeModel Epson WorkForce 500 - CUPS+Gutenprint v5.2.5 Simplified
DeviceURI usb://EPSON/WorkForce%20520[/B]
State Stopped
StateMessage Unplugged or turned off
StateTime 1304961406
Reason paused
Type 8425484
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-raster 100 rastertogutenprint.5.2
Filter application/vnd.cups-command 33 commandtoepson
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
(END) 

```

The part I bolded above is an actual printer I have installed on this machine. It happens to be the printer at the place I work. I also have a printer at home which is a different brand (a Hewlett Packard) and it does not appear in that file.

This is the first time I've ever looked at these things - just now, tonight. But maybe it gives you some ideas or maybe more questions (questions can be good too if they lead you do solutions).

For what it's worth I just thought I'd show some things. If I find anything more concrete, and you haven't solved your problem already, I will post it here.

Also, a possibility that may help would be to make a thread in the Installation and Upgrades forum here: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333) asking something like "is there a way to manually configure my printer driver?" or something like that. Just a suggestion. And, one more thing, I noticed you didn't include any tags for this thread. I don't know if this is just a superstition on my part or what but I have always found that adding relevant tags seems to get me a faster response and responses from more people than not adding them.

This is the link I mentioned: [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

By the way, can you give the file name or name of the driver you need/ want to use?

Good luck. I'll do what I can to learn more about this and if I find anything that may be useful I'll post it.

---

### Post by ClientAlive on 2011-05-20
I just found files named after the other printer I have installed on this machine. Actually it looks like the Epson from where I work is also in there so that is all of them.

```

root@lineNine:/etc/cups# cd ppd
root@lineNine:/etc/cups/ppd# ls
EPSON-WorkForce-520.ppd        Officejet-J4680-series-Fax.ppd
HP-Officejet-J4680-series.ppd  Officejet-J4680-series.ppd

```

The full path/ way I got to it on 10.04 is:

```

cd /etc/cups/ppd/; ls

```

Here is what it looks like if I open the file named "HP-Officejet-J4680-series.ppd" Coincidentally I think (I think) that is the name of the driver as well.

Running the code:

```

less HP-Officejet-J4680-series.ppd

```

in order to open the file.

Here's what's inside:

```

*PPD-Adobe: "4.3"
*%%%% PPD file for HP Officejet j4680 Series hpijs with CUPS.
*%%%% Created by the CUPS PPD Compiler CUPS v1.4.3.
*% (c) 2004-2008 Copyright Hewlett-Packard Development Company, LP
*FormatVersion: "4.3"
*FileVersion: "hpijs 3.10.2"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*PCFileName: "hp-officejet_j4680_series-hpijs.ppd"
*Product: "(HP Deskjet f4280 All-in-one)"
*Product: "(HP Officejet j4680c All-in-one Printer)"
*Product: "(HP Officejet j4680 All-in-one Printer)"
*Manufacturer: "HP"
*ModelName: "HP Officejet j4680 Series hpijs"
*ShortNickName: "HP Officejet j4680 Series hpijs"
*NickName: "HP Officejet j4680 Series hpijs, 3.10.2"
*PSVersion: "(3010.000) 0"
*LanguageLevel: "3"
*ColorDevice: True
*DefaultColorSpace: RGB
*FileSystem: False
*Throughput: "1"
*LandscapeOrientation: Plus90
*TTRasterizer: Type42
*% Driver-defined attributes...
*DefaultResolution: 600dpi
*FoomaticRIPOptionSetting PageSize=Custom: " -dDEVICEWIDTHPOINTS=0 -dD&&
EVICEHEIGHTPOINTS=0"
*End
*FoomaticIDs: "HP-DeskJet_5650 hpijs"
*FoomaticRIPCommandLine: "gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPA&&
USE -sDEVICE=ijs -sIjsServer=hpijs%A%B%C -dIjsUseOutputFD%Z -sOutputFi&&
le=- -"
*End
*FoomaticRIPOption Model: "enum CmdLine A 100"
*FoomaticRIPOptionSetting Model=HP-DeskJet_5650: " -sDeviceManufacture&&
r=&quot;HEWLETT-PACKARD&quot; -sDeviceModel=&quot;deskjet 5600&quot;"
*End
*FoomaticRIPOption PrintoutMode: "enum Composite B"
*FoomaticRIPOptionSetting PrintoutMode=Draft: "Quality=300FastDraftCol&&
orCMYK"
*End
*FoomaticRIPOptionSetting PrintoutMode=Draft.Gray: "Quality=300FastDra&&
ftGrayscaleK"
*End
*FoomaticRIPOptionSetting PrintoutMode=Normal: "Quality=300ColorCMYK"
*FoomaticRIPOptionSetting PrintoutMode=Normal.Gray: "Quality=300Graysc&&
aleK"
*End
*FoomaticRIPOptionSetting PrintoutMode=High: "Quality=600ColorCMYK"
*FoomaticRIPOptionSetting PrintoutMode=High.Gray: "Quality=600Grayscal&&
eK"
*End
*FoomaticRIPOptionSetting PrintoutMode=Photo: "Quality=600PhotoCMYKFu&&
llBleed"
*End
*FoomaticRIPOption InputSlot: "enum CmdLine C"
*FoomaticRIPOptionSetting InputSlot=Default: ",PS:MediaPosition=7"
*FoomaticRIPOptionSetting InputSlot=PhotoTray: ",PS:MediaPosition=6"
*FoomaticRIPOptionSetting InputSlot=Upper: ",PS:MediaPosition=1"
*FoomaticRIPOptionSetting InputSlot=Lower: ",PS:MediaPosition=4"
*FoomaticRIPOptionSetting InputSlot=CDDVDTray: ",PS:MediaPosition=14"
*FoomaticRIPOptionSetting InputSlot=Envelope: ",PS:MediaPosition=3"
*FoomaticRIPOptionSetting InputSlot=LargeCapacity: ",PS:MediaPosition=&&
5"
*End
*FoomaticRIPOptionSetting InputSlot=Manual: ",PS:MediaPosition=2"
*FoomaticRIPOptionSetting InputSlot=MPTray: ",PS:MediaPosition=8"
*FoomaticRIPOption PageSize: "enum CmdLine A"
*FoomaticRIPOptionSetting PageSize=Letter: " -dDEVICEWIDTHPOINTS=612 -&&
dDEVICEHEIGHTPOINTS=792"
*End
*FoomaticRIPOptionSetting PageSize=A4: " -dDEVICEWIDTHPOINTS=595 -dDEV&&
ICEHEIGHTPOINTS=842"
*End
*FoomaticRIPOptionSetting PageSize=Photo: " -dDEVICEWIDTHPOINTS=288 -d&&
DEVICEHEIGHTPOINTS=432"
*End
*FoomaticRIPOptionSetting PageSize=Photo5x7: " -dDEVICEWIDTHPOINTS=360&&
 -dDEVICEHEIGHTPOINTS=504"
*End
*FoomaticRIPOptionSetting PageSize=PhotoTearOff: " -dDEVICEWIDTHPOINTS&&
=288 -dDEVICEHEIGHTPOINTS=432"
*End
*FoomaticRIPOptionSetting PageSize=3x5: " -dDEVICEWIDTHPOINTS=216 -dDE&&
VICEHEIGHTPOINTS=360"
*End
*FoomaticRIPOptionSetting PageSize=5x8: " -dDEVICEWIDTHPOINTS=360 -dDE&&
VICEHEIGHTPOINTS=576"
*End
*FoomaticRIPOptionSetting PageSize=A5: " -dDEVICEWIDTHPOINTS=420 -dDEV&&
ICEHEIGHTPOINTS=595"
*End
*FoomaticRIPOptionSetting PageSize=A6: " -dDEVICEWIDTHPOINTS=297 -dDEV&&
ICEHEIGHTPOINTS=420"
*End
*FoomaticRIPOptionSetting PageSize=A6TearOff: " -dDEVICEWIDTHPOINTS=29&&
7 -dDEVICEHEIGHTPOINTS=420"
*End
*FoomaticRIPOptionSetting PageSize=B5JIS: " -dDEVICEWIDTHPOINTS=516 -d&&
DEVICEHEIGHTPOINTS=729"
*End
*FoomaticRIPOptionSetting PageSize=CDDVD80: " -dDEVICEWIDTHPOINTS=237 &&
-dDEVICEHEIGHTPOINTS=237"
*End
*FoomaticRIPOptionSetting PageSize=CDDVD120: " -dDEVICEWIDTHPOINTS=360&&
 -dDEVICEHEIGHTPOINTS=360"
*End
*FoomaticRIPOptionSetting PageSize=Env10: " -dDEVICEWIDTHPOINTS=297 -d&&
DEVICEHEIGHTPOINTS=684"
*End
*FoomaticRIPOptionSetting PageSize=EnvC5: " -dDEVICEWIDTHPOINTS=459 -d&&
DEVICEHEIGHTPOINTS=649"
*End
*FoomaticRIPOptionSetting PageSize=EnvC6: " -dDEVICEWIDTHPOINTS=323 -d&&
DEVICEHEIGHTPOINTS=459"
*End
*FoomaticRIPOptionSetting PageSize=EnvDL: " -dDEVICEWIDTHPOINTS=312 -d&&
DEVICEHEIGHTPOINTS=624"
*End
*FoomaticRIPOptionSetting PageSize=EnvISOB5: " -dDEVICEWIDTHPOINTS=499&&
 -dDEVICEHEIGHTPOINTS=709"
*End
*FoomaticRIPOptionSetting PageSize=EnvMonarch: " -dDEVICEWIDTHPOINTS=2&&
79 -dDEVICEHEIGHTPOINTS=540"
*End
*FoomaticRIPOptionSetting PageSize=Executive: " -dDEVICEWIDTHPOINTS=52&&
2 -dDEVICEHEIGHTPOINTS=756
*End
*FoomaticRIPOptionSetting PageSize=FLSA: " -dDEVICEWIDTHPOINTS=612 -dD&&
EVICEHEIGHTPOINTS=936"
*End
*FoomaticRIPOptionSetting PageSize=Hagaki: " -dDEVICEWIDTHPOINTS=283 -&&
dDEVICEHEIGHTPOINTS=420"
*End
*FoomaticRIPOptionSetting PageSize=Legal: " -dDEVICEWIDTHPOINTS=612 -d&&
DEVICEHEIGHTPOINTS=1008"
*End
*FoomaticRIPOptionSetting PageSize=Oufuku: " -dDEVICEWIDTHPOINTS=567 -&&
dDEVICEHEIGHTPOINTS=420"
*End
*FoomaticRIPOptionSetting PageSize=w558h774: " -dDEVICEWIDTHPOINTS=558&&
 -dDEVICEHEIGHTPOINTS=774"
*End
*FoomaticRIPOptionSetting PageSize=w612h935: " -dDEVICEWIDTHPOINTS=612&&
 -dDEVICEHEIGHTPOINTS=935"
*End
*FoomaticRIPOptionSetting PageSize=B4JIS: " -dDEVICEWIDTHPOINTS=729 -d&&
DEVICEHEIGHTPOINTS=1033"
*End
*FoomaticRIPOptionSetting PageSize=Ledger: " -dDEVICEWIDTHPOINTS=792 -&&
dDEVICEHEIGHTPOINTS=1224"
*End
*FoomaticRIPOptionSetting PageSize=SuperB: " -dDEVICEWIDTHPOINTS=936 -&&
dDEVICEHEIGHTPOINTS=1368"
*End
*FoomaticRIPOptionSetting PageSize=w774h1116: " -dDEVICEWIDTHPOINTS=77&&
4 -dDEVICEHEIGHTPOINTS=1116"
*End
*FoomaticRIPOptionSetting PageSize=A3: " -dDEVICEWIDTHPOINTS=842 -dDEV&&
ICEHEIGHTPOINTS=1190"
*End
*FoomaticRIPOption Duplex: "enum CmdLine A"
*FoomaticRIPOptionSetting Duplex=DuplexNoTumble: " -dDuplex=true -dTum&&
ble=false"
*End
*FoomaticRIPOptionSetting Duplex=DuplexTumble: " -dDuplex=true -dTumbl&&
e=true"
*End
*FoomaticRIPOptionSetting Duplex=None: " -dDuplex=false"
*FoomaticRIPOption DryTime: "enum CmdLine B"
*FoomaticRIPOptionSetting DryTime=Zero: ""
*FoomaticRIPOptionSetting DryTime=Five: ",DryTime=5"
*FoomaticRIPOptionSetting DryTime=Ten: ",DryTime=10"
*FoomaticRIPOptionSetting DryTime=Fifteen: ",DryTime=15"
*FoomaticRIPOptionSetting DryTime=Twenty: ",DryTime=20"
*FoomaticRIPOptionSetting DryTime=TwentyFive: ",DryTime=25"
*FoomaticRIPOptionSetting DryTime=Thirty: ",DryTime=30"
*FoomaticRIPOption Quality: "enum CmdLine B"
*FoomaticRIPOptionSetting Quality=300ColorCMYK: " -r300 -sIjsParams=Qu&&
ality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet&&
=2"
*End
*FoomaticRIPOptionSetting Quality=300ColorCMYKFullBleed: " -r300 -sIjs&&
Params=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2,Quality:FullBleed=1"
*End
*FoomaticRIPOptionSetting Quality=300DraftColorCMYK: " -r300 -sIjsPara&&
ms=Quality:Quality=1,Quality:ColorMode=2,Quality:MediaType=0,Quality:P&&
enSet=2"
*End
*FoomaticRIPOptionSetting Quality=300DraftGrayscaleK: " -r300 -sIjs&&
Params=Quality:Quality=1,Quality:ColorMode=0,Quality:MediaType=0,Quali&&
ty:PenSet=2"
*End
*FoomaticRIPOptionSetting Quality=300FastDraftColorCMYK: " -r300 -sIjs&&
Params=Quality:Quality=4,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2,Quality:SpeedMech=1"
*End
*FoomaticRIPOptionSetting Quality=300FastDraftGrayscaleK: " -r300 -&&
sIjsParams=Quality:Quality=4,Quality:ColorMode=0,Quality:MediaType=0,Q&&
uality:PenSet=2,Quality:SpeedMech=1"
*End
*FoomaticRIPOptionSetting Quality=300GrayscaleK: " -r300 -sIjsParam&&
s=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:Pe&&
nSet=2"
*End
*FoomaticRIPOptionSetting Quality=600ColorCMYK: " -r600 -sIjsParams=Qu&&
ality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet&&
=2"
*End
*FoomaticRIPOptionSetting Quality=600ColorCMYKFullBleed: " -r600 -sIjs&&
Params=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quali&&
ty:PenSet=2,Quality:FullBleed=1"
*End
*FoomaticRIPOptionSetting Quality=600GrayscaleK: " -r600 -sIjsParam&&
s=Quality:Quality=0,Quality:ColorMode=0,Quality:MediaType=0,Quality:Pe&&
nSet=2"
*End
*FoomaticRIPOptionSetting Quality=600PhotoCMYK: " -r600 -sIjsParams=&&
Quality:Quality=2,Quality:ColorMode=2,Quality:MediaType=2,Quality:PenS&&
et=2"
*End
*FoomaticRIPOptionSetting Quality=600PhotoCMYKFullBleed: " -r600 -sI&&
jsParams=Quality:Quality=2,Quality:ColorMode=2,Quality:MediaType=2,Qua&&
lity:PenSet=2,Quality:FullBleed=1"
*End
*1284DeviceID: "MFG:HP;MDL:officejet j4680 series;DES:officejet j4680 series;"
*cupsVersion: 1.4
*cupsModelNumber: 0
*cupsManualCopies: True
*cupsFilter: "application/vnd.cups-postscript 100 foomatic-rip"
*cupsFilter: "application/vnd.cups-pdf 0 foomatic-rip"
*cupsLanguages: "en"
*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize Letter/Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*PageSize A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*PageSize Photo/Photo or 4x6 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo"
*PageSize Photo5x7/Photo or 5x7 inch index card: "%% FoomaticRIPOptionSetting: P
ageSize=Photo5x7"
*PageSize PhotoTearOff/Photo with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=PhotoTearOff"
*PageSize 3x5/3x5 inch index card: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*PageSize 5x8/5x8 inch index card: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*PageSize A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*PageSize A6/A6: "%% FoomaticRIPOptionSetting: PageSize=A6"
*PageSize A6TearOff/A6 with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=A6TearOff"
*PageSize B5JIS/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5JIS"
*PageSize CDDVD80/CD or DVD 80 mm: "%% FoomaticRIPOptionSetting: PageSize=CDDVD80"
*PageSize CDDVD120/CD or DVD 120 mm: "%% FoomaticRIPOptionSetting: PageSize=CDDVD120"
*PageSize Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*PageSize EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*PageSize EnvC6/Envelope C6: "%% FoomaticRIPOptionSetting: PageSize=EnvC6"
*PageSize EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*PageSize EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*PageSize EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*PageSize Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*PageSize FLSA/American Foolscap: "%% FoomaticRIPOptionSetting: PageSize=FLSA"
*PageSize Hagaki/Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Hagaki"
*PageSize Legal/Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*PageSize Oufuku/Oufuku-Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Oufuku"
*PageSize w558h774/16K: "%% FoomaticRIPOptionSetting: PageSize=w558h774"
*PageSize w612h935/Executive (JIS): "%% FoomaticRIPOptionSetting: PageSize=w612h935"
*CloseUI: *PageSize
*OpenUI *PageRegion/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: Letter
*PageRegion Letter/Letter: "%% FoomaticRIPOptionSetting: PageSize=Letter"
*PageRegion A4/A4: "%% FoomaticRIPOptionSetting: PageSize=A4"
*PageRegion Photo/Photo or 4x6 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo"
*PageRegion Photo5x7/Photo or 5x7 inch index card: "%% FoomaticRIPOptionSetting: PageSize=Photo5x7"
*PageRegion PhotoTearOff/Photo with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=PhotoTearOff"
*PageRegion 3x5/3x5 inch index card: "%% FoomaticRIPOptionSetting: PageSize=3x5"
*PageRegion 5x8/5x8 inch index card: "%% FoomaticRIPOptionSetting: PageSize=5x8"
*PageRegion A5/A5: "%% FoomaticRIPOptionSetting: PageSize=A5"
*PageRegion A6/A6: "%% FoomaticRIPOptionSetting: PageSize=A6"
*PageRegion A6TearOff/A6 with tear-off tab: "%% FoomaticRIPOptionSetting: PageSize=A6TearOff"
*PageRegion B5JIS/B5 (JIS): "%% FoomaticRIPOptionSetting: PageSize=B5JIS"
*PageRegion CDDVD80/CD or DVD 80 mm: "%% FoomaticRIPOptionSetting: PageSize=CDDVD80"
*PageRegion CDDVD120/CD or DVD 120 mm: "%% FoomaticRIPOptionSetting: PageSize=CDDVD120"
*PageRegion Env10/Envelope #10: "%% FoomaticRIPOptionSetting: PageSize=Env10"
*PageRegion EnvC5/Envelope C5: "%% FoomaticRIPOptionSetting: PageSize=EnvC5"
*PageRegion EnvC6/Envelope C6: "%% FoomaticRIPOptionSetting: PageSize=EnvC6"
*PageRegion EnvDL/Envelope DL: "%% FoomaticRIPOptionSetting: PageSize=EnvDL"
*PageRegion EnvISOB5/Envelope B5: "%% FoomaticRIPOptionSetting: PageSize=EnvISOB5"
*PageRegion EnvMonarch/Envelope Monarch: "%% FoomaticRIPOptionSetting: PageSize=EnvMonarch"
*PageRegion Executive/Executive: "%% FoomaticRIPOptionSetting: PageSize=Executive"
*PageRegion FLSA/American Foolscap: "%% FoomaticRIPOptionSetting: PageSize=FLSA"
*PageRegion Hagaki/Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Hagaki"
*PageRegion Legal/Legal: "%% FoomaticRIPOptionSetting: PageSize=Legal"
*PageRegion Oufuku/Oufuku-Hagaki: "%% FoomaticRIPOptionSetting: PageSize=Oufuku"
*PageRegion w558h774/16K: "%% FoomaticRIPOptionSetting: PageSize=w558h774"
*PageRegion w612h935/Executive (JIS): "%% FoomaticRIPOptionSetting: PageSize=w612h935"
*CloseUI: *PageRegion
*DefaultImageableArea: Letter
*ImageableArea Letter/Letter: "18 36 594 783"
*ImageableArea A4/A4: "9.720000267029 36 585.279999732971 833"
*ImageableArea Photo/Photo or 4x6 inch index card: "0 36 288 432"
*ImageableArea Photo5x7/Photo or 5x7 inch index card: "0 36 360 504"
*ImageableArea PhotoTearOff/Photo with tear-off tab: "0 0 288 432"
*ImageableArea 3x5/3x5 inch index card: "0 36 216 360"
*ImageableArea 5x8/5x8 inch index card: "0 36 360 576"
*ImageableArea A5/A5: "9 36 411 586"
*ImageableArea A6/A6: "0 36 297 420"
*ImageableArea A6TearOff/A6 with tear-off tab: "0 0 297 420"
*ImageableArea B5JIS/B5 (JIS): "18 36 498 720"
*ImageableArea CDDVD80/CD or DVD 80 mm: "0 36 237 237"
*ImageableArea CDDVD120/CD or DVD 120 mm: "0 36 360 360"
*ImageableArea Env10/Envelope #10: "0 36 297 684"
*ImageableArea EnvC5/Envelope C5: "18 36 441 640"
*ImageableArea EnvC6/Envelope C6: "0 36 323 459"
*ImageableArea EnvDL/Envelope DL: "0 36 312 624"
*ImageableArea EnvISOB5/Envelope B5: "18 36 481 700"
*ImageableArea EnvMonarch/Envelope Monarch: "0 36 279 540"
*ImageableArea Executive/Executive: "18 36 504 747"
*ImageableArea FLSA/American Foolscap: "18 36 594 927"
*ImageableArea Hagaki/Hagaki: "0 36 283 420"
*ImageableArea Legal/Legal: "18 36 594 999"
*ImageableArea Oufuku/Oufuku-Hagaki: "0 36 567 420"
*ImageableArea w558h774/16K: "18 36 540 765"
*ImageableArea w612h935/Executive (JIS): "18 36 594 926"
*DefaultPaperDimension: Letter
*PaperDimension Letter/Letter: "612 792"
*PaperDimension A4/A4: "595 842"
*PaperDimension Photo/Photo or 4x6 inch index card: "288 432"
*PaperDimension Photo5x7/Photo or 5x7 inch index card: "360 504"
*PaperDimension PhotoTearOff/Photo with tear-off tab: "288 432"
*PaperDimension 3x5/3x5 inch index card: "216 360"
*PaperDimension 5x8/5x8 inch index card: "360 576"
*PaperDimension A5/A5: "420 595"
*PaperDimension A6/A6: "297 420"
*PaperDimension A6TearOff/A6 with tear-off tab: "297 420"
*PaperDimension B5JIS/B5 (JIS): "516 729"
*PaperDimension CDDVD80/CD or DVD 80 mm: "237 237"
*PaperDimension CDDVD120/CD or DVD 120 mm: "360 360"
*PaperDimension Env10/Envelope #10: "297 684"
*PaperDimension EnvC5/Envelope C5: "459 649"
*PaperDimension EnvC6/Envelope C6: "323 459"
*PaperDimension EnvDL/Envelope DL: "312 624"
*PaperDimension EnvISOB5/Envelope B5: "499 709"
*PaperDimension EnvMonarch/Envelope Monarch: "279 540"
*PaperDimension Executive/Executive: "522 756"
*PaperDimension FLSA/American Foolscap: "612 936"
*PaperDimension Hagaki/Hagaki: "283 420"
*PaperDimension Legal/Legal: "612 1008"
*PaperDimension Oufuku/Oufuku-Hagaki: "567 420"
*PaperDimension w558h774/16K: "558 774"
*PaperDimension w612h935/Executive (JIS): "612 935"
*MaxMediaWidth: "936"
*MaxMediaHeight: "1368"
*HWMargins: 18 36 18 9
*CustomPageSize True: "pop pop pop <</PageSize[5 -2 roll]/ImagingBBox null>>setpagedevice"
*ParamCustomPageSize Width: 1 points 72 936
*ParamCustomPageSize Height: 2 points 288 1368
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 0 0
*OpenUI *PrintoutMode/Printout Mode: PickOne
*OrderDependency: 10 AnySetup *PrintoutMode
*DefaultPrintoutMode: Normal
*PrintoutMode Draft/Draft (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft"
*PrintoutMode Draft.Gray/Draft Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft.Gray"
*PrintoutMode Normal/Normal (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal"
*PrintoutMode Normal.Gray/Normal Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal.Gray"
*PrintoutMode High/High Quality (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High"
*PrintoutMode High.Gray/High Quality Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High.Gray"
*PrintoutMode Photo/Photo (on photo paper): "%% FoomaticRIPOptionSetting: PrintoutMode=Photo"
*CloseUI: *PrintoutMode
*OpenUI *InputSlot/Media Source: PickOne
*OrderDependency: 100 AnySetup *InputSlot
*DefaultInputSlot: Default
*InputSlot Default/Printer default: "%% FoomaticRIPOptionSetting: InputSlot=Default"
*InputSlot PhotoTray/Photo Tray: "%% FoomaticRIPOptionSetting: InputSlot=PhotoTray"
*InputSlot Upper/Upper Tray: "%% FoomaticRIPOptionSetting: InputSlot=Upper"
*InputSlot Lower/Lower Tray: "%% FoomaticRIPOptionSetting: InputSlot=Lower"
*InputSlot CDDVDTray/CD or DVD Tray: "%% FoomaticRIPOptionSetting: InputSlot=CDDVDTray"
*InputSlot Envelope/Envelope Feeder: "%% FoomaticRIPOptionSetting: InputSlot=Envelope"
*InputSlot LargeCapacity/Large Capacity Tray: "%% FoomaticRIPOptionSetting: InputSlot=LargeCapacity"
*InputSlot Manual/Manual Feeder: "%% FoomaticRIPOptionSetting: InputSlot=Manual"
*InputSlot MPTray/Multi Purpose Tray: "%% FoomaticRIPOptionSetting: InputSlot=MPTray"
*CloseUI: *InputSlot
*OpenUI *Duplex/Double-Sided Printing: PickOne
*OrderDependency: 120 AnySetup *Duplex
*DefaultDuplex: None
*Duplex DuplexNoTumble/Long Edge (Standard): "%% FoomaticRIPOptionSetting: Duplex=DuplexNoTumble"
*Duplex DuplexTumble/Short Edge (Flip): "%% FoomaticRIPOptionSetting: Duplex=DuplexTumble"
*Duplex None/Off: "%% FoomaticRIPOptionSetting: Duplex=None"
*CloseUI: *Duplex
*OpenUI *DryTime/Additional Dry Time: PickOne
*OrderDependency: 120 AnySetup *DryTime
*DefaultDryTime: Zero
*DryTime Zero/Printer Default: "%% FoomaticRIPOptionSetting: DryTime=Zero"
*DryTime Five/5 Seconds: "%% FoomaticRIPOptionSetting: DryTime=Five"
*DryTime Ten/10 Seconds: "%% FoomaticRIPOptionSetting: DryTime=Ten"
*DryTime Fifteen/15 Seconds: "%% FoomaticRIPOptionSetting: DryTime=Fifteen"
*DryTime Twenty/20 Seconds: "%% FoomaticRIPOptionSetting: DryTime=Twenty"
*DryTime TwentyFive/25 Seconds: "%% FoomaticRIPOptionSetting: DryTime=TwentyFive
"
*DryTime Thirty/30 Seconds: "%% FoomaticRIPOptionSetting: DryTime=Thirty"
*CloseUI: *DryTime
*OpenGroup: PrintoutMode/Printout Mode
*OpenUI *Quality/Resolution, Quality, Ink Type, Media Type: PickOne
*OrderDependency: 100 AnySetup *Quality
*DefaultQuality: FromPrintoutMode
*Quality FromPrintoutMode/Controlled by 'Printout Mode': "%% FoomaticRIPOptionSetting: Quality=@PrintoutMode"
*Quality 300ColorCMYK/300 dpi, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300ColorCMYK"
*Quality 300ColorCMYKFullBleed/300 dpi, Color, Full Bleed, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300ColorCMYKFullBleed"
*Quality 300DraftColorCMYK/300 dpi, Draft, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300DraftColorCMYK"
*Quality 300DraftGrayscaleK/300 dpi, Draft, Grayscale, Black Cartr.: "%% FoomaticRIPOptionSetting: Quality=300DraftGrayscaleK"
*Quality 300FastDraftColorCMYK/300 dpi, FastDraft, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=300FastDraftColorCMYK"
*Quality 300FastDraftGrayscaleK/300 dpi, FastDraft, Grayscale, Black Cartr.: "%% FoomaticRIPOptionSetting: Quality=300FastDraftGrayscaleK"
*Quality 300GrayscaleK/300 dpi, Grayscale, Black Cartr.: "%% FoomaticRIPOptionSetting: Quality=300GrayscaleK"
*Quality 600ColorCMYK/600 dpi, Color, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600ColorCMYK"
*Quality 600ColorCMYKFullBleed/600 dpi, Color, Full Bleed, Black + Color Cartr.: "%% FoomaticRIPOptionSetting: Quality=600ColorCMYKFullBleed"
*Quality 600GrayscaleK/600 dpi, Grayscale, Black Cartr.: "%% FoomaticRIPOptionSetting: Quality=600GrayscaleK"
*Quality 600PhotoCMYK/600 dpi, Photo, Black + Color Cartr., Photo Paper: "%% FoomaticRIPOptionSetting: Quality=600PhotoCMYK"
*Quality 600PhotoCMYKFullBleed/600 dpi, Photo, Full Bleed, Black + Color Cartr., Photo Paper: "%% FoomaticRIPOptionSetting: Quality=600PhotoCMYKFullBleed"
*CloseUI: *Quality
*CloseGroup: PrintoutMode
*DefaultFont: Courier
*Font AvantGarde-Book: Standard "(1.05)" Standard ROM
*Font AvantGarde-BookOblique: Standard "(1.05)" Standard ROM
*Font AvantGarde-Demi: Standard "(1.05)" Standard ROM
*Font AvantGarde-DemiOblique: Standard "(1.05)" Standard ROM
*Font Bookman-Demi: Standard "(1.05)" Standard ROM
*Font Bookman-DemiItalic: Standard "(1.05)" Standard ROM
*Font Bookman-Light: Standard "(1.05)" Standard ROM
*Font Bookman-LightItalic: Standard "(1.05)" Standard ROM
*Font Courier: Standard "(1.05)" Standard ROM
*Font Courier-Bold: Standard "(1.05)" Standard ROM
*Font Courier-BoldOblique: Standard "(1.05)" Standard ROM
*Font Courier-Oblique: Standard "(1.05)" Standard ROM
*Font Helvetica: Standard "(1.05)" Standard ROM
*Font Helvetica-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Oblique: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(1.05)" Standard ROM
*Font Palatino-Bold: Standard "(1.05)" Standard ROM
*Font Palatino-BoldItalic: Standard "(1.05)" Standard ROM
*Font Palatino-Italic: Standard "(1.05)" Standard ROM
*Font Helvetica-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Bold: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Narrow-Oblique: Standard "(1.05)" Standard ROM
*Font Helvetica-Oblique: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Bold: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Italic: Standard "(1.05)" Standard ROM
*Font NewCenturySchlbk-Roman: Standard "(1.05)" Standard ROM
*Font Palatino-Bold: Standard "(1.05)" Standard ROM
*Font Palatino-BoldItalic: Standard "(1.05)" Standard ROM
*Font Palatino-Italic: Standard "(1.05)" Standard ROM
*Font Palatino-Roman: Standard "(1.05)" Standard ROM
*Font Symbol: Special "(001.005)" Special ROM
*Font Times-Bold: Standard "(1.05)" Standard ROM
*Font Times-BoldItalic: Standard "(1.05)" Standard ROM
*Font Times-Italic: Standard "(1.05)" Standard ROM
*Font Times-Roman: Standard "(1.05)" Standard ROM
*Font ZapfChancery-MediumItalic: Standard "(1.05)" Standard ROM
*Font ZapfDingbats: Special "(001.005)" Special ROM
*% End of hp-officejet_j4680_series-hpijs.ppd, 23183 bytes.

```

Looking at what's in there, maybe this _is_ the driver. If that were the case then it is what will be referenced to in some other configuration file? I don't know.

---

