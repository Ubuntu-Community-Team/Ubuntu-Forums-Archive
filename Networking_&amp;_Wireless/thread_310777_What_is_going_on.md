---
title: "What is going on?"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by klittzzer on 2006-12-01
I have a problem with connecting to the net though Ubuntu Edgy kernel 2.6.17-10, 2.6.17-10-generic. I am using a Sagem fast 800 USB modem and have been through dozens of walkthroughs to get my modem operationl and thus log on to my ISP (Tiscali UK).

These are some of the methods I have tried,#

[http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem](http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem)

[http://forum.eagle-usb.org/viewtopic.php?t=4499](http://forum.eagle-usb.org/viewtopic.php?t=4499)

[http://www.mail-archive.com/ueagleatm-dev@gna.org/msg00480.html](http://www.mail-archive.com/ueagleatm-dev@gna.org/msg00480.html)

[http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.eagle-usb.org/viewtopic.php%3Fp%3D24367%26sid%3Dfe8eb84a335de94df26140e0e94798d0&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3DInstall%2Bueagle-atm-1.3%26hl%3Den%26lr%3D%26sa%3DG](http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.eagle-usb.org/viewtopic.php%3Fp%3D24367%26sid%3Dfe8eb84a335de94df26140e0e94798d0&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3DInstall%2Bueagle-atm-1.3%26hl%3Den%26lr%3D%26sa%3DG)

Just some, and I have been through them all several times.

I have installed the headers and build essential requirements, 
everything goes well until I enter

sudo modprobe ueagle-atm

No lights blink, they just stay on.

and when I enter

dmesg|grep ueagle

I always get

[1717959.39600] [ueagle-atm]driver ueagle-gna 1.3 loaded
[1717959.39600] usb2-1 : [ueagle-atm] ADSL device founded vid (ox1110) pid (ox9032) 

: eagle III
[1717959.468000] [usb2-1 : [ueagle-atm] pre firmware device, uploading firmware
[1717959.468000] usb2-1 :[ueagle.atm] loading firmware ueagle-atm/eagle III.fw
[1717959.468000] usbcore : registred new driver ueagle-atm

Not 'modem is operational.
What am I doing wrong? I have tried installing the Eagle data and utils in synaptic through my live cd but non of it makes any difference. I simply cannot connect to the net.

I have posted my problem elsewhere yet no one has repilied. Even if it is to say, you cannot log on through the kernel I have, at least I will know.

I would really appreciate it if someone could have a look at this and get back to me. It seems like others with the same modem and ISP can get on line?

Please help

Cheers

Klittz:confused: :confused: :confused:

---

### Post by ciscosurfer on 2006-12-02
whoops

---

### Post by fugative on 2006-12-15
klittzzer
I had the same problem mate, two weeks of sleepless nights and a usually understanding wife getting prickly. 
Do yourself a favour and go back to aces howto but make sure you delete the eagle files properly. I'm a newbie and I cut and paste his commands into the terminal ... misstake! don't want to tell you how to suck eggs but where it says 'uname -r' are you putting your kernel version, I didn't at least 4 times. go through the files computer - files - lib - modules and see what the folder is called. Make sure you unplug the modem (it clears the memory) then plug it back in . Do you have a LAN network attached, i did and when i plug in the lan the internet falls off. 
I feel for you, i'm no expert but it worked for me and i didn't even understand what i was doing.

Be strong and wisdom will come

---

