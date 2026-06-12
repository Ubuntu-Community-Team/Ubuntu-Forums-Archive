---
title: "Network Manager - Wireless not Displayed"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by drewcoll on 2007-03-18
NetworkManager will not display any wireless networks.

I have removed all of the entries other than lo in interfaces, and have had success in getting networkmanager to run, but after restarting it won't and the process is not repeatable.

I am using a AWLL 3026 with the driver zd1211.

ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:09:6B:90:E2:BA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5548 (5.4 KiB)  TX bytes:5548 (5.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:A3:03:A2:F7  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe03:a2f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1535 errors:83 dropped:0 overruns:0 frame:83
          TX packets:1566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1133635 (1.0 MiB)  TX bytes:290842 (284.0 KiB)


wlan0 is my problem, since it's connections are not showing up in NetworkManager.

Using iwconfig the adapter is completely functional - scan, connections, etc. but I would like the GUI and scanning/WPA abilites of NetworkManager or a similar program.

I did get Knetworkmanager to work but after a restart it didn't display any wireless connections - as I understand it is an alternate GUI basically for NetworkManager.  I was testing with it and it asked about Kwallet and I just disregarded it and decided to install the network-manager-gnome package since that was made for my desktop environment, and I like it better.

any ideas on what to do?

---

### Post by briar on 2007-03-18
I am having the same problem, but mine has worked in the past.  It was something that changed in a recent update (I'm not sure which, did 200mb of 'em a couple days ago) - it turned my wireless into a wired and I can't get it to turn back. I also can't figure out how to un-update, if that might fix it.  
briar

---

### Post by Floppyjoe on 2007-03-18
Disable all your network interfaces in System/Administration/Networking.

---

### Post by drewcoll on 2007-03-18
I tried that - no luck.

I disabled them, then restarted, but still only "wired network" was an option and it was greyed out.

---

### Post by Floppyjoe on 2007-03-18
Did you comment out all but the lo interface in /etc/network/interfaces by putting a # in front of each line except for the lo interface lines?

---

### Post by drewcoll on 2007-03-18
Yes, I tried that too.

But looking around in the forums I found Wicd Manager, and I've got that working now :).

Now its time to restart and try my luck!

---

### Post by drewcoll on 2007-03-18
Right on!

Here's what worked for me:

1. Enable network controllers in Administration -> Networking
2. Install Wicd from [http://compwiz18.blackhole.cx/wicd/wb/]("http://compwiz18.blackhole.cx/wicd/wb/") using version 1.1.0 deb package
3. Open Wicd then scan for networks and input security information (it doesn't automatically detect the type like NM:( )
4. Add /opt/wicd/tray-edgy.py to Preferences -> Sessions startup tab
5. Restart and Voila!

An alternative to NM for all kinds of secured wireless networks!

---

