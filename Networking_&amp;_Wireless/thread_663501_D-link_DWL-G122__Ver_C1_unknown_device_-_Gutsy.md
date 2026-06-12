---
title: "D-link DWL-G122  Ver: C1 unknown device - Gutsy"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by dsluser on 2008-01-10
Hi All,

I hope I'm not posting asking about something that has already been solved but I've spent about an hour looking through the forums and any posts I've found regarding this can either already detect the usb adaptor or are for an older version of Ubuntu.

I've just installed 7.10 and the network tools shows loopback, wired, wireless and unknown usb which I assume is the Dlink adaptor.

I checked "lsusb -v | less" and it picks up the usb but with no real info,  I'm assuming that's because the driver isn't loaded. I've seen posts referring to ndiswrapper but I'm not sure what this is or how it works.

I'm a software support technician for Windows but I have very little experience with Unix/Linux. Could someone explain to me where to find the drivers, how to install them and how to set the pc up to use WPA - PSK?

I would appreciate if someone would explain the commands instead of just listing them but I know this is a community forum and everyone is busy, I'll just be happy to get this up and running so I can start leaving Windows behind :)

Many thanks in advance

---

### Post by dsluser on 2008-01-11
Ok I've spent about 10 hours trying to get the dlink or my belkin f5d7051 usb adapters to work. Here's what I tried so far(for the Belkin, I've pretty much given up on the Dlink -

[http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/](http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/)  

When I ran the script initially I received a "could not receive exclusive lock" error message. I added in the Multiverse and Universe repositories which seemed to fix that but whenever the script runs I see error messages such as "could not find file or directory /etc/sbin/ndiswrapper line 181" (I'm sorry I'm going off memory here as I only have one wired connection and I'm currently on XP)

I eventually gave up on this method and used Add/Remove programs to install ndisgtk. I downloaded and extracted the Belkin drivers and renamed the 5 files mentioned in the above link to lower case. When I load a driver using ndisgtk it says "invalid driver".

Next I tried "sudo ndiswrapper -i bcmrndis.inf" which told me it was already installed.

"sudo ndiswrapper -r bcmrndis.inf" gave me the same error message as I saw when running the above script - could not find file or folder with a mention of ndiswrapper1.9 or something similiar and again the line exception.

Next I used ndisgtk to remove the invalid driver which worked fine. I then tried to run "sudo ndiswrapper -i bcmrndis.inf" again but again the same error.

Guessing at what the error meant I moved the 5 required files to the directory that was constantly pointed to with the "file not found" error. I tried to install from the terminal again which said the driver was already installed. When I checked ndisgtk it showed every file I had copied to that folder as an invalid driver which had been installed.

I'm running out of ideas here, I've checked the sourceforge wiki for ndiswrapper which says my Belkin should install fine and I then have to copy two files manually.

I'm sorry the paths are sketchy but I'm hoping this is a common enough problem. If anyone would like more detail in order to help me please let me know and I can boot up the linux machine and connect to the net.

---

