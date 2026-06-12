---
title: "Wireless connection ok, but no internet"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by KARaidl on 2007-10-12
Hey, I've tried searching the forums but I can't find anything to settle my question.

I'm using a Linksys WMP54G v4, which connects to my unsecured wireless network ok, but there's no internet access. For the record, my router is a Linksys WRT54G v8. 

The real bitchy part about it is that I'm on a desktop, and can't get to an ethernet connection, so downloading and installing packages on Ubuntu out of the question for the moment. However, my connection and internet is working ok on XP.

Right now my network manager is set to roaming.

Any help?

---

### Post by stalker145 on 2007-10-12
> **KARaidl said:**
> I'm using a Linksys WMP54G v4, which connects to my unsecured wireless network ok, but there's no internet access. For the record, my router is a Linksys WRT54G v8. 

Have you inadvertently set up MAC filtering in your router. I believe it is under wireless and then security.

If there are any other computers on your network, can you ping them and can you ping your router? Can those computers get to the internet or is it just this one?

If roaming isn't working for you have you tried going with a static IP?

I'll try to think of anything else that might help. Let me know if this does or doesn't work.

---

### Post by KARaidl on 2007-10-12
I checked, and there's no MAC filtering.

Our computers aren't networked together. We just use the router to get internet access from one point. In fact, if I'm not mistaken, I think the WRT54G is only for wireless internet. Anyway, no, I can't ping the router. It tells me that there is no network connected, although I have all five bars at around 83%.

I tried static, too, to no avail.

---

### Post by kevdog on 2007-10-12
Set your router to use no encryption, no WEP/ no WPA (for testing purposes), and then follow the link in my signature so we can possibly debug your problem.  I dont know whats wrong right now! Did you install the drivers for your card or know if they were possibly installed by default

---

### Post by KARaidl on 2007-10-12
Ok, I followed your guide, but it didn't work. To answer your question, no, I did not install my driver, it was installed by default.

Just to let you know, my logical device came back as ra0, while my driver is RT61.

---

### Post by kevdog on 2007-10-12
Cool, good ra drive

Can you tell me what part didnt work, or did you not get any dhcp offers??

Can you see your network with iwlist scan?

Flippant answers with "it didnt work", dont allow me to help you much! How about volunteering a little bit information!

---

### Post by KARaidl on 2007-10-12
> Flippant answers with "it didnt work", dont allow me to help you much! How about volunteering a little bit information!

I wasn't trying to be rude. I had copied and pasted everything I did in the terminal to Geddit, but it was displaying weird in Notepad, so I had to reboot and try again. I just didn't realize you would respond so quickly. Anyway, here's a readout of what I did - 

> 
kyle@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: a
       bus info: pci@00:0a.0
       logical name: ra0
       version: 00
       serial: 00:18:39:14:63:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=32 multicast=yes wireless=RT61 Wireless
       resources: iomemory:fb000000-fb007fff irq:19
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:04:61:43:27:2d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:d800-d8ff iomemory:fb009000-fb0090ff irq:18
kyle@ubuntu:~$ sudo ifconfig ra0 down
Password:
kyle@ubuntu:~$ sudo dhclient -r ra0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:18:39:14:63:c1
Sending on   LPF/ra0/00:18:39:14:63:c1
Sending on   Socket/fallback
kyle@ubuntu:~$ sudo ifconfig ra0 up
kyle@ubuntu:~$ sudo iwconfig ra0 essid "raidl_net"
kyle@ubuntu:~$ sudo iwconfig ra0 mode managed
kyle@ubuntu:~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:18:39:14:63:c1
Sending on   LPF/ra0/00:18:39:14:63:c1
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
kyle@ubuntu:~$ 

Hope that helps - I'll be back in a few with an iwlist scan.

[EDIT] - Alright, I've got it. I'm trying to connect to "Raidl_Net"

> 
kyle@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:18:39:97:88:F2
                    ESSID:"Kindell"
                    Mode:Managed
                    Channel:1
                    Encryption key:off
                    Quality:62/100  Signal level:-70 dBm  Noise level:-256 dBm
          Cell 02 - Address: 00:1C:10:2E:EB:30
                    ESSID:"Raidl_Net"
                    Mode:Managed
                    Channel:6
                    Encryption key:off
                    Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
          Cell 03 - Address: 00:14:6C:05:74:62
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Quality:0/100  Signal level:-66 dBm  Noise level:-256 dBm

kyle@ubuntu:~$ 

---

### Post by KARaidl on 2007-10-12
Sigh... is there a way to get rid of the smileys?

Those :o's are supposed to be : o

---

### Post by kevdog on 2007-10-12
Look at this:
Quality:0/100 
This is for your router network.  

Are all those other router's yours??? I noticed that they were broadcasting on channels 1,6,11 -- I think this was designed by someone to avoid signal overlap purposefully.  Can you connect to Kindell?? I noticed that was unencrypted also.

---

### Post by KARaidl on 2007-10-13
The Kindell network is my neighbor's. I've "borrowed" it before during router troubles. Anyway, I tried connecting and basically the situation is the same. First, I tried the manual way through the terminal and it reads out like this - 

> 
kyle@ubuntu:~$ sudo ifconfig ra0 down 
Password: 
kyle@ubuntu:~$ sudo dhclient -r ra0 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/ra0/00:18:39:14:63:c1 
Sending on   LPF/ra0/00:18:39:14:63:c1 
Sending on   Socket/fallback 
kyle@ubuntu:~$ sudo ifconfig ra0 up 
kyle@ubuntu:~$ sudo iwconfig ra0 essid "kindell" 
kyle@ubuntu:~$ sudo iwconfig ra0 mode managed 
kyle@ubuntu:~$ sudo dhclient ra0 
There is already a pid file /var/run/dhclient.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/ra0/00:18:39:14:63:c1 
Sending on   LPF/ra0/00:18:39:14:63:c1 
Sending on   Socket/fallback 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
kyle@ubuntu:~$  

Then I tried a static IP, but that didn't work either, so I went into roaming mode, and finally got a connection, but there was still no internet, just like my router.

I dunno what the problem is, but it's the same deal with either router. (Except that Raid_Net quality is showing up as 0).

---

### Post by KARaidl on 2007-10-13
Son of a bitch! I told you something wrong. My WMP54G isn't a version 4, it's a 4.1

Sorry for the confusion.

---

### Post by kevdog on 2007-10-13
It doesnt matter.  

Hmm Im not sure what the problem is right now.  You have tried rebooting and then doing the manual steps again??  Something isnt right somewhere -- Ive never seen 2 routers with signal level 0 so that might be a problem. 

If it doesnt work after a reboot -- Do you want to update the driver to the most recent??  You will have to download one file for it to work -- or -- with the new Gutsy release the new version of the driver is included.  Installing the new driver isnt hard although you do have to compile from source -- but its only about 3 steps (maybe 5).  

I'll do anything you want since I know this device's problem can be solved!!

Also its
sudo iwconfig ra0 mode Managed

Not sure if that will make a difference but Managed needs to be capitalized.

---

### Post by KARaidl on 2007-10-13
Well I'm using Wubi right now, so I'll wait for it to offer Gutsy. I went with Wubi because I simply wanted to try Ubuntu, and if it went well, I'd create a partition for it.

I'd give the new driver a shot, sure, but I don't know if there even is one.

---

### Post by kevdog on 2007-10-13
OK you are using or want the rt61 driver!!

These instructions are for the rt73 driver:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

Read through the first post a few times.  Just use some common sense.  Where it lists rt73 you want rt61.  
Take your time installing it, and then try to connect from the command line.  Where it says WEP_KEY_OFF -- skip this line, you dont need it, since you are trying an unencrypted connection, not WEP.

Just go slowly and report back if you have problems. 
Good luck.

---

### Post by Haim on 2007-10-19
There's this how-to which may be better...

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

---

