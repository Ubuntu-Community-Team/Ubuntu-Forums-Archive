---
title: "Wireless card (w200) is on but can't connect to wireless."
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by Idrive on 2007-04-06
I used these directions: [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200) 
to get my w200 to work with Ubuntu 6.1.  I got the green light to come on but I don't know how to setup the rest to get wireless working.  Here is my iwconfig if it helps:
> dustin@dustin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"NETGEAR"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:5.5 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=3/92  Signal level=-77 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:4
          Tx excessive retries:16  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

dustin@dustin-laptop:~$ 
How do I go about configuring the wireless?  Currently I am plugged directly into my netgear router.

---

### Post by Idrive on 2007-04-06
bump for some help

---

### Post by Idrive on 2007-04-06
Can anyone help me?  This is very frustrating.  Here is some more info that may help??
> dustin@dustin-laptop:~$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
dustin@dustin-laptop:~$ sudo wifi-radar -d
dhclient3 --version 2>&1
Error : unrecognised wireless request "&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;"
There is already a pid file /var/run/dhclient.eth1.pid with pid 29385
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0b:cd:8d:23:27
Sending on   LPF/eth1/00:0b:cd:8d:23:27
Listening on LPF/eth0/00:02:a5:c0:ce:84
Sending on   LPF/eth0/00:02:a5:c0:ce:84
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Stale pid file.  Removing
SIOCSIFNETMASK: Cannot assign requested address
SIOCADDRT: Invalid argument


---

### Post by Idrive on 2007-04-10
I really thought this forum would be more helpful.  I guess its time to go back to windows xp...at least it works with wireless.

-d

---

### Post by josephus on 2007-04-10
not sure why you didn't get any help sooner, maybe you bumped it too soon and people assumed someone was already helping you.

anyway if you still want help, I can give it a shot.

how is your router configured? is there any passwords (WEP/WPA), if so it's usually helpful to turn them off until we can actually connect to the network.

try 
```
sudo ifdown eth1
sudo ifup eth1
```

---

### Post by Idrive on 2007-04-10
Well my network actually started working last night and then....

I decided to do the 160 some updates and bam...no more wireless...this is so beyond annoying.  Maybe I will try another open source distro.  I just don't understand with this being open source and ubuntu being out for as long as it has that the wireless issues are still so bad...very disapointing.

-d

---

### Post by Graes on 2007-04-10
You will need to recompile the adapter every time the installed Linux kernel changes even slightly, i.e. once you've rebooted after a linux-kernel update. Go through the steps  in "Installing the driver" (make, sudo make install), then reboot.

---

