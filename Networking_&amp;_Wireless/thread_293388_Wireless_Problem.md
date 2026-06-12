---
title: "Wireless Problem"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by MOSFET_MOSFET on 2006-11-05
I have just installed Ubuntu for the first time on my PC. I used dual-boot just in-case, and I am having some confusing internet problems.

Ubuntu did not find my wireless card to begin with, but ndiswrapper   seemed to solve that, however it will still not connect to the internet!

I have entered my BSSID key and my WEP key, however when I try to use Firefox, nothing !

I have tried all sorts but nothing seems to work, and I missing something right in my face here ?

Thanks to all who help.

---

### Post by FrodoB on 2006-11-05
Open a terminal window and type the iwconfig command and it will show you the status of your wireless devices. Go to the menu pick:

Applications -> Accessories -> Terminal

Then type:

$ iwconfig

And you should see something like:

wlan0     802.11b/g NIC  ESSID:"My ESSID"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate:11 Mb/s   
          Retry: off   RTS thr=2432 B   Fragment thr: off
          Power Management: off
          Link Quality=96/100  Signal level=98/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:10
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you see a wireless device and it has your ESSID in it and if the Access Point has the MAC address of your access point and the frequency matches your access points channel then you are connected.

To see the routing information type:

$ netstat -rn

You should see something like this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.10.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.10.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         10.10.0.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         10.10.0.1     0.0.0.0         UG        0 0          0 eth0

showing that each network device has a route to the correct gateway.

---

