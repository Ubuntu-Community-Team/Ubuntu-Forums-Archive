---
title: "Wireless bcm4318 need HELP!!"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by Blacktalon on 2006-10-19
Hello everyone, my wireless use to work for a few months, about 3 months ago then it stopped.  I wasn't using ndiswrapper at the time either, and had gotten rid of all traces of it and wifi-radar.  Now I'm trying to get it back, but so far when i do the " sudo ./ndiswrapper_setup" i get this problem

sam@Sam:~$ sudo ./ndiswrapper_setup
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ndiswrapper_setup, Copyright (C) 2006 Adam Blackburn
ndiswrapper_setup comes with ABSOLUTELY NO WARRANTY; for details
type please see the file gpl.txt in the same directory as this program.
This is free software, and you are welcome  to redistribute it
under certain conditions; type see the file gpl.txt in the same directory
as this program for details.
Installing ndiswrapper...
dpkg: error processing ndiswrapper.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper.deb
dpkg died with exit status 1
Extracting the drivers...
tar: wifidrivers.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Deleting temporary files...
rm: cannot remove `wifidrivers.tar.gz': No such file or directory
Changing driver permissions...
chmod: cannot access `drivers': No such file or directory
chmod: cannot access `ndiswrapper.deb': No such file or directory
Changing working directory...
./ndiswrapper_setup: line 53: cd: drivers: No such file or directory
Removing previous attempts to use ndiswrapper, if any...please ignore errors in this section...
ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1
Driver bcmwl5a is not installed.Use -l to list installed drivers
ndiswrapper died with exit status 1
Removing default driver...
ERROR: Module bcm43xx does not exist in /proc/modules
rmmod died with exit status 1
Installing driver through ndiswrapper...
couldn't copy ./bcmwl5.inf at /usr/sbin/ndiswrapper line 135.
Installing bcmwl5
ndiswrapper died with exit status 2
Installed ndis drivers:
bcmwl5  invalid driver!
ndiswrapper died with exit status 1
modprobe config already contains alias directive

Modprobing ndiswrapper...
FATAL: Could not open '/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
modprobe died with exit status 1
Moving back to original working directory...
Deleting more temporary files...
rm: cannot remove `ndiswrapper.deb': No such file or directory
Blacklisting bcm43xx...
Adding ndiswrapper to /etc/modules, so it should load on boot...
Removing excess entries from your network interfaces file...
Searching for a wifi point...
eth1      Interface doesn't support scanning.

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:36:36:94:3d
Sending on   LPF/eth0/00:16:36:36:94:3d
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 108334482 seconds.


can anyone help me please!!

Thanks,
~BT

---

### Post by Blacktalon on 2006-10-20
*bump*

---

### Post by compwiz18 on 2006-10-20
If you post to the thread you got the post to, people actively read that thread and might help you (I just found you through pure randomness).  Anyway, it appears that you didn't extract the entire archive.  I recommend downloading it again, then following the directions EXACTLY again.

---

### Post by Blacktalon on 2006-10-20
Thanks compwiz18, for your nice critasim.  And I DID read and follow the directions correct but you know let me point out where this main problem looks like it is : FATAL: Could not open '/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory .  Now I am not an expert on this, but I believe I need to know how to get this, and running.  In order for it possibly work, but I could be wrong.  And before you say extract again and retry, does already doing it 5 times work for redownloading and retrying.  obviously something isn't wring in my modules file.

---

### Post by compwiz18 on 2006-10-20
Sorry, that was kind of mean.  I'll try and help you here.

Someone else had this problem, and I don't really understand it.  You downloaded the .tar.gz file from my other post, correct?  You then extracted this file to the Desktop?

OK:  Here's what I need to know:

Follow the directions [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) to step 4.  After you're done with step 4, run **ls ~/Desktop** in the Terminal, and post the output.

---

### Post by Blacktalon on 2006-10-20
Ok, thank you.

Heres what the output is:
bcm4318-nm.targz
cs225
gpl.txt
ndiswrapper.deb
ndiswrapper_setup
wifidrivers.tar.gz
wifi-setup.log
wifisetup.log

---

### Post by compwiz18 on 2006-10-22
It should work.  Try it again.

But before running the instructions in the HOWTO, run **cd ~/Desktop**

---

### Post by Blacktalon on 2006-10-22
ok, i tried again and still the same result.  I believe the main problem is that it is not creating a module for ndiswrapper when i run the startup or even if i do a dpkg -i ndiswrapper.deb.  I need to figure out how to get one back in /proc/module, and /lib/modules/2.6.15-27-386/kernel/drivers/net/ .

---

### Post by Blacktalon on 2006-10-24
Ok, I got those modules back and now the ./ndiswrapper_setup doesn't throw any more errors at me, but I can't seen to connect to the internet still,  when it does or I do the dhclient is says:

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a5:7b:70:f9
Sending on   LPF/eth1/00:14:a5:7b:70:f9
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.2.7
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.2.6
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

any ideas on how to get this part fixed?

---

### Post by compwiz18 on 2006-10-24
Are you using network-manager?

That will help you connect to a network.

If you aren't, open Synaptic and find network-manager-gnome and install it.  Log out, and log back in.  Look in the system tray for a new icon, and click on it.  Select the wireless network you wish to connect to.

---

### Post by Blacktalon on 2006-10-25
Sorry it took me so long to respond, but yes I am using it and I still can't get a connection.  I am thinking on friday when the new version of ubuntu comes out, I'll just do a fresh install with that.

---

### Post by compwiz18 on 2006-10-26
You might also want to try wifi-radar, can be found in the package manager (Synaptic)

if you try this, make sure to uninstall network-manager-gnome first.

---

