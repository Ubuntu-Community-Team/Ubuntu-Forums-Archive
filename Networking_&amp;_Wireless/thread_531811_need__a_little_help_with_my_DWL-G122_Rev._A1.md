---
title: "need  a little help with my DWL-G122 Rev. A1"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by Cardload on 2007-08-22
I just switched over from openSUSE where I had the DWL-G122 A1 usb dongle working with ndiswrapper.  Things seem to be very close to working, but I cannot connect to my router.  I can see it in the list of wireless networks, and it appears to connect, but I can't surf the web or even access the router via [http://192.168.1.1](http://192.168.1.1)

Ubuntu did load some modules (prism54usb, which apparently needs prism54common, which apparently needs mac80211, which apparently needs cfg80211), but I removed all of them with rmmod, before I modprobed ndiswrapper.  When I did that, the lights on the dongle went on (both act and link) and flickered.

Here is the output from iwlist scanning:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:27:4D:80
                    ESSID:"<neighbors router>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
          Cell 02 - Address: 00:09:5B:EB:6E:A4
                    ESSID:"<router I want to conect to>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK


any suggestions?  could I be on the wrong channel or something?  how does one check or change that?

Thanks in advance.

---

### Post by Cardload on 2007-08-22
another note:

If I switch to manual configuration using the network applet deal on the top right corner of the screen (sorry, dont' know what it's called... the icon with two monitors), instead of checking "enable roaming", it only lists WEP (hexidecimal) and WEP (ascii) as options for the key.  Is there a reason why WPA isn't listed?  I tried both entering my passphrase with the WEP (ascii) mode and entering the output from wpa_passphrase <essid> <passphrase> with the WEP (hexidecimal), but neither got me connected to the router.

Thanks... as always, any help at all is appreciated.

---

### Post by Gage_AB on 2007-08-23
Hi,

Could you send me your exact instructions on how you did your set-up? You got alot further then me.

Thx!!

---

### Post by Cardload on 2007-08-23
sure,

Download the rev a1 driver from d-link's website. (click support, then downloads, select dwl and then g122)

Extract the zip file to a directory you will remember.

Install ndiswrapper if you haven't.

Now, type:

lsmod

in a terminal and look to see if prism54usb is listed.  If it is, then I think it should be removed with rmmod:

sudo rmmod prism54usb

now, I'm not sure if you need to or not, but prism54usb uses mac80211 which uses cfg80211 as well, so I removed all of those in a similar way.  Anyway, I think you want to get rid of these because they are the drivers that ubuntu installed automatically because it thought it was the correct driver for the device.

When you've done that, type lsmod again and make sure they aren't listed... If they are, unplug the usb dongle and repeat the rmmod commands.  Plug it back in and check if they are loaded again.  I don't really know how these things work in linux, but I think since this is a usb device, the modules are loaded any time the device is plugged in.  Anyway, if you mess around a little, you'll be able to remove those modules at some point. 

When lsmod no longer shows those modules, and the dongle is plugged in, do the following

sudo ndiswrapper -i /<directory where PRISM2A.inf is located>/PRISM2A.inf

check that it works with 

sudo ndiswrapper -l 

that should say that the driver is installed and device is present, etc.

Then, 

sudo  modprobe ndiswrapper 

The lights on the dongle should come on at this point.  

use:

iwlist scanning 

and see if it lists any wireless netwoks 

That's as far as I got.  I didn't try to blacklist the modules that were removed in the earlier steps, because I never got connected.  If you do, then I think you will want to figure out how to make sure those modules don't load everytime linux boots up, and how to make sure ndiswrapper does ( I think thats:  sudo ndiswrapper -m ... but I'm not entirely sure) otherwise, you'll have to redo all of this when you reboot

also, don't forget... I'm a noob.

let me know if  you end up being able to connect.

---

### Post by Gage_AB on 2007-08-23
Hey are you sure about the driver? prism2a? I find a primsa02.inf

---

### Post by psyburn on 2007-08-24
> **Cardload said:**
> another note:

If I switch to manual configuration using the network applet deal on the top right corner of the screen (sorry, dont' know what it's called... the icon with two monitors), instead of checking "enable roaming", it only lists WEP (hexidecimal) and WEP (ascii) as options for the key.  Is there a reason why WPA isn't listed?  I tried both entering my passphrase with the WEP (ascii) mode and entering the output from wpa_passphrase <essid> <passphrase> with the WEP (hexidecimal), but neither got me connected to the router.

Thanks... as always, any help at all is appreciated.

the prism54 drivers do not have native support for WPA

see this [post]("http://ubuntuforums.org/showpost.php?p=3243843&postcount=20") for how I got it to work without using ndiswrapper including config files.
[http://ubuntuforums.org/showpost.php?p=3243843&postcount=20]("http://ubuntuforums.org/showpost.php?p=3243843&postcount=20")

---

### Post by Gage_AB on 2007-08-24
I haven't had any success yet, I tried using the Ubuntu wireless tool installed the driver prisma02.inf but it reports back hardware present: No
Not sure where to go from here but I do get when I run ndiswrapper -l device presnt (alternate driver prim54usb)???

---

### Post by Gage_AB on 2007-08-26
Hey this worked for me on DWL-G122 A1

It sounds like a lot of people are having trouble getting the DWL-G120 revision b1 usb wireless card to work. I was able to get it working fairly easily with the help of these two guides:
[http://www.linuxforums.org/forum/361063-post1.html](http://www.linuxforums.org/forum/361063-post1.html)
[http://www.linuxquestions.org/questions/showthread](http://www.linuxquestions.org/questions/showthread) ..php?p=1170631#post1170631

If you have a windows parition, that's great. Otherwise, this guide should still work. I installed the card using my windows partition, but I put the files I used on a website for those of you that don't have xp installed. These will probably work, but no guarantees. I believe you can get to the same files by clicking on the first link.

Step 1
If possible, install the card on a Windows XP partition.

Step 2
Install ndiswrapper via synaptic. The two packages I had installed were ndiswrapper-common and ndiswrapper-utils-1.9.

Step 3
Now look in your windows partition for prisma02.inf. I did a file search for this, mine was located in /../windows/inf/prisma02.inf. Enter the directory that the file is in and run the command
Code: 
 ndiswrapper  -i  prisma02.inf 
For me, this created the directory /etc/ndiswrapper/prisma02 which had 4 files in it: 045E:00C2.F.conf, 2001:3701.F.conf, 09AA:1000.F.conf, prisma02.inf. Some people may only have 2 files: 2001:3701.F.conf, prisma02.inf.

Note: If you don't have a windows partition, try using the files from the first link or the files I used here. No guarantees on these though. I suspect it would only work for the B1 revision of the card. If your not sure of your revision, check the back of your card for where it says H/W Ver. Any feedback on if these work would be appreciated, they may even make a few other steps unnecessary.

Step 4
When you run the ndiswrapper command, it does not find 2 of the files. Add 2 copies of each of these files to the directory /etc/ndiswrapper/prisma02; one copy with all lowercase and one copy with all uppercase letters (except for the extension). The first file is prisma02.sys (mine was in /../windows/system32/drivers/) and the second is prismapi.dll (mine was in /..windows/system32/).

The directory /etc/ndiswrapper/prisma02/ should now have the following files in it 
Code: 
dan@dan-deskbook:/etc/ndiswrapper/prisma02$ ls 
045E:00C2.F.conf  2001:3701.F.conf  prisma02.sys  
09AA:1000.F.conf  prisma02.inf      PRISMA02.sys  
Note: Again, if you don't have a windows partition try the files I uploaded or the ones from the first link.

Step 5
Now, we need to disable the original ubuntu drivers that didn't work. To do this, open up the blacklist in gedit 
Code: 
sudo gedit /etc/modprobe.d/blacklist 
Add the following lines to the file 
Code: 
blacklist islsmusb 
blacklist islsm 
blacklist islsm-usb 
blacklist prism54usb 
Step 6
Plug in, reboot, and you should be good to go.

---

### Post by Cardload on 2007-08-28
Gage,

Glad it worked for you.  Are you using WPA or WEP?  

Also, I don't understand why you need to blacklist islsm_usb... those modules aren't loaded for my card, just the prism54usb.  My guess is that the islsm* stuff is for the g120...

Anyway, I unfortunately gave up and just bought the WDA 1320.  It works "out of the box".  I figured I'd just stop messing around with the 3 cards I have that hassle me everytime I reinstall.  For those interested, you can get it at newegg right now for $30 and there is a $10 rebate.  easy peasy

---

