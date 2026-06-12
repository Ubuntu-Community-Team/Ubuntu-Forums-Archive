---
title: "Madwifi driver for atheros ar5007eg / Site offline"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by TheCount85 on 2008-11-10
Hi!
I installed the WLAN driver for my atheros ar5007eg last week (Ubuntu 8.04) and it worked fine, both with WEP and WPA. Then I made some stupid mistake so that I've to reinstall the driver. Problem is, I know how to do it, but the Madwifi driver isn't online any more, I used the following driver:
[http://snapshots.madwifi-project.orgspecial/madwifi-ng-r2756+ar5007.tar.gz]("http://snapshots.madwifi-project.orgspecial/madwifi-ng-r2756+ar5007.tar.gz"). I already downloaded the madwifi-hal-0.10.5.6, but it didn't work for me!
I hope to find anybody who can send me the old driver! 
Thanks a lot!

---

### Post by rynyeager on 2008-11-10
I am having the same issue! Have spent days trying to figure this one out, thought I got dumb or something....


running 32bit hardy heron on acer aspire 7520 AMD 64 athlon alongside vista

Any help would be great.....

---

### Post by raiwo on 2008-11-10
use [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

---

### Post by TheCount85 on 2008-11-10
I used madwifi-hal-0.10.5.6, but it didn't work!

---

### Post by rynyeager on 2008-11-10
Again I must agree! here is a screen shot 

ryan@ryan-laptop:~$ wget [http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-current.tar.gz)
--22:36:57--  [http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-current.tar.gz)
           => `madwifi-hal-0.10.5.6-current.tar.gz'
Resolving snapshots.madwifi-project.org... 217.24.1.134
Connecting to snapshots.madwifi-project.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:36:57 ERROR 404: Not Found.

ryan@ryan-laptop:~$ wget [http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz)
--22:37:41--  [http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz)
           => `madwifi-hal-0.10.5.6-r3875-20081105.tar.gz'
Resolving snapshots.madwifi-project.org... 217.24.1.134
Connecting to snapshots.madwifi-project.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:37:41 ERROR 404: Not Found.

It is getting hard to make the change to Ubuntu if i have to keep bringing my laptop over to my desktop to use the internet to learn about it

Again any help would be great. I have used all the tutorials I could find to no avail. Of course, I am not smart enough yet to use ndiswrapper. please help

---

### Post by acreech on 2008-11-11
This is the information about my system and how I got my wireless card to work. I am using a 32 bit system. The following codes worked for Ubuntu 8.04 and 8.10. 

> lshw -C network 

> 

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:04:bd:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,05/02/2007,5.3.0.45 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:04:70:52:24:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


> 
sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*
wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
(remove the space between ftp &:, i.e. [ftp://)](ftp://))

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 


Then reboot and the card should work.

---

### Post by porchrat on 2008-11-12
I've seen a few people with a similar issue and they say that apparently the madwifi site is now closed for direct connections using "wget" but they could still get the driver using a browser.  Maybe that is still an issue?

---

### Post by enigmageek on 2008-11-13
TheCount85. Hello, I have the old driver you said you used. Also I would install DKMS to rebuild the driver whenever you update/upgrade. Let me know if you want me to post/send it.

---

### Post by rynyeager on 2008-11-14
Acreech:

This had my card up and running right away. I am running an Acer Aspire 7520 with ar5007eg chipset ar242x Os's Vista Home Premium and 8.10

---

### Post by TheCount85 on 2008-11-14
> **enigmageek said:**
> TheCount85. Hello, I have the old driver you said you used. Also I would install DKMS to rebuild the driver whenever you update/upgrade. Let me know if you want me to post/send it.

Hi! Would be very nice if you could post it! Hope this will help me get my card running.

---

### Post by enigmageek on 2008-11-14
TheCount85. Hello. I'm waiting for an answer from the moderators about posting a file to this forum. Then I've got to figure out how to do it once I get clearance. I could just email it though. I had used the old driver you mention and thought I still had it on my external drive, but it seems I didn't back it up. The Madwifi site doesn't have it anymore. When I downloaded the file it had just a note inside saying they don't have it anymore and to use the latest madwifi-hal. I did some research and found a version that's supposed to work. It's the one I use now. You must first uninstall ndiswrapper if you have it, and all other instances of wireless driver. Also make sure you uncheck the Atheros card support and Hal support in System/Administration/Hardware Drivers Manager. Also blacklist ath5k in /etc/modprobe.d/blacklist. Make sure you have the build-essential package as well. Good luck I hope this helps and I hope I can post the file. If not I could email it.

---

### Post by JeffoOfMetal on 2009-02-19
Dude, just post it. We all need it.

---

### Post by racie on 2009-02-19
I also have the AR5007 card.  With Ubuntu version 8.04 (Hardy Heron) I couldn't get it worked.  I've tried countless times and nothing worked.  Wouldn't you know it, I switched to 8.10 and found an easy little solution.  So, I'd suggest switching to Intrepid Ibex.  You can get it working MUCH easier that way.  =P

---

### Post by JeffoOfMetal on 2009-02-22
Well, that wouldn't help because I <i>am</i> running Intrepid. I need to know, what can I do? I don't see a point in replacing the Madwifi snapshot if it works already and this new one doesn't.

---

