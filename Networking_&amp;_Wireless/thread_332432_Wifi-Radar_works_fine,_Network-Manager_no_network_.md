---
title: "Wifi-Radar works fine, Network-Manager no network devices"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by uzd4ce on 2007-01-06
I'm running Edgy on a Dell D410.  I installed Network-Manager first, but it just tells me "No network devices have been found".  

So I did some research, found and installed Wifi Radar.  With that, I can see and connect to my home network without any problem.  

Any ideas why the one sees my card but the other doesn't?

I'm curious to get Network-Manager working because I'm currently unable to connect to the 802.11B network at work.  Wifi Radar sees the network, but it fails to acquire an IP address.  I'm wondering if using Network-Manager would make any difference.

Lspci shows: 
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).   

In other posts I've seen it listed as 802.11b/g.  Is it somehow set up to not have B support?

Below is some more information.  I appreciate any replies.

Thanks

bill@notebook:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 


bill@notebook:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Kennedy"  Nickname:"Kennedy"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:68:30:8C   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-43 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by sirozha on 2007-01-30
You have to make sure you have installed the following packages: 

wpasupplicant
network-manager-gnome

Then, edit the "/etc/default/wpasupplicant" file and make sure ENABLED=0 is there. 

Reboot your laptop, and you should be able to use the Network Management icon to connect to wireless network.

---

### Post by zeifertstc on 2007-01-30
Please refer to this post [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

Purge anything you've installed to NDISwrapper and follow poster's directions 100% I have this chipset on my wireless card on this laptop. The Broadcom 4318 (aka 43xx in driver terms) is the most stubborn wireless card out on the market today.

One tip to make sure your installation goes off without a hitch is to make sure that you have the latest version of NDISwrapper installed. The version supplied by Automatix2 works just fine.

([http://www.getautomatix.com](http://www.getautomatix.com)) Go with the installation method suiting your installation (dapper or edgy and proc x86 or x86_64) using apt-get to make sure all dependencies are resolved prior to installation.

---

### Post by cam_tram on 2007-03-13
You need to comment out the lines refering to your wireless card in /etc/network/interfaces

---

