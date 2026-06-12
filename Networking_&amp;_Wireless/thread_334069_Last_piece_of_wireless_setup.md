---
title: "Last piece of wireless setup"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by GolfGeek on 2007-01-08
I've been following the 201902 thread for the setup for my presario2100 laptop for wireless. It has the bcm4306 chipset. This is as far as I've gone. I blacklisted the bcm43xx, installed ndiswrapper-utils-1.8 and installed the bcmwl5 driver. When I do ndiswrapper -l I get the following:bcmwl5  driver installed  hardware present
I also did the sudo apt-get install network-manager-gnome

When I use gedit on /etc/network/interfaces I see l0,eth0,sit0 with no wireless extensions and eth1 with no scan results

When I run iwconfig
bcmwl5          driver installed, hardware present 
calibsys@calibsys-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:13 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

At this point, I'm not sure where to proceed next. I did also make the change in the /etc/iftab to change eth1 to wlan0. the other 2 references (ndiswrapper and interfaces) both had a listing for wlan0.

I feel I'm getting close to wireless connection. Very tired of wires running thru the kitchen!!
Thanks for any help. These forums are really great

---

### Post by revmc on 2007-01-08
you might want to check this thread out.  It worked for me.  I have the Dell Precision M60 with the bcm4306.

[http://ubuntuforums.org/showthread.php?p=1984965#post1984965](http://ubuntuforums.org/showthread.php?p=1984965#post1984965)

Revmc

---

### Post by GolfGeek on 2007-01-08
rev
Thanks for the link but I'm having a problem accessing it. It brings me back to this same page. I'll try searching for the thread # or accessing it another way. In the meantime, can you check the listing. Thanks

---

### Post by smitjel on 2007-01-08
Why does the iwconfig not give you an ESSID for the eth1 interface?  And you're obviously not connected to your router.  Are you sure the router is setup correctly?

Maybe try [this tip](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-2e426b202454e898950d58705107ed41c99dc25b) from the wireless troubleshooting guide?

Another [tip I learned](http://ubuntuforums.org/showthread.php?t=333731) is to start from the ground up and disable security first and build security into it after you've established a working connection with the router.  Good luck!

---

