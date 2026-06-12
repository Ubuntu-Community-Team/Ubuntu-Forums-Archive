---
title: "Help!  I'm THIS CLOSE!"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Bezmotivnik on 2006-10-27
[terminal screens follow]

OK, I reinstalled 6.06 today.  At the time. I had a Zydas 1211 USB device plugged in and to my astonishment, at the end of the installation, I was online.  I was able to run Automatix and do all the installation of whatnot online with no problems.  It worked perfectly.

When I rebooted, however, I could no longer access my net.  Nothing.  Can't ping, can't reach the network.  I know I have to be THIS FREAKIN' CLOSE to beating this thing, but I can't figure out what I need to do.

Someone please help me with this monster!

Thanks for any help!

Here are the results from the terminal in the current dead-to-the-net mode.  "Cell 01" is the repeater I'm trying to access, BTW:
 
anonymous@x:~$ iwconfig

wlan0     802.11b/g NIC  
ESSID:""
Mode:Managed  
Frequency=2.462 GHz  
Access Point: Not-Associated
Bit Rate:1 Mb/s
Retry:off   
RTS thr=2432 B   
Fragment thr:off
Power Management:off
Link Quality=4/92  Signal level=13/154  Noise level=161/154
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anonymous@x:~$ iwlist scanning

wlan0     Scan completed :
Cell 01 - Address: 00:14:A5:8E:1C:35          
ESSID:"linksys"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality:72/92  Signal level=-202 dBm  Noise level=-256 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
   
Cell 02 - Address: 00:18:39:75:C1:AC
ESSID:"linksys"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality:88/92  Signal level=-241 dBm  Noise level=-256 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
  
Cell 03 - Address: 00:16:B6:D7:8F:AB
ESSID:"linksys"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality:100/92  Signal level=-240 dBm  Noise level=-256 dBm
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s

anonymous@x:~$ ifconfig wlan0

wlan0     
Link encap:Ethernet  HWaddr 00:0E:2E:71:77:A6
inet addr:192.168.1.93  Bcast:192.168.1.255  Mask:255.255.255.0
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by wieman01 on 2006-10-27
There are 3 networks (scan) around with the same network name ("linksys") on the same channel (6). I guess that creates a problem. Change the channel through the router's GUI.

---

### Post by wieman01 on 2006-10-27
To change the channel of your device:
> iwconfig wlan0 channel X
'X' stands for the channel.

_**EDIT:**_
To change your adapter's channel settings you can add this line to "etc/network/interfaces":
> wireless-channel **X** 

---

### Post by Bezmotivnik on 2006-10-28
> **wieman01 said:**
> There are 3 networks (scan) around with the same network name ("linksys") on the same channel (6). I guess that creates a problem. 
That's the AP and two repeaters.

Why isn't it a problem until I reboot?  It works even in "live" mode.  :-k

---

### Post by Bezmotivnik on 2006-10-28
> **wieman01 said:**
> 
To change your adapter's channel settings you can add this line to "etc/network/interfaces":
How will it work to change it from the AP/repeater's channel?  I don't understand that point.

---

### Post by wieman01 on 2006-10-28
I just don't know how the system reacts if there 3 three identical networks around (or repeaters). That's why I as suggesting to have each of them run on a separate channel. But then again, I don't know enough about repeaters.

Is is possible to test your network only with on repeater/router running? Just to see if your PC connects. If it does we may know the culprit...

---

### Post by Bezmotivnik on 2006-10-28
> **wieman01 said:**
> 
Is is possible to test your network only with on repeater/router running?
Only by physically blocking the two weakest signals from the AP and one repeater.  I haven't access to them. 

It appears that in its natural state, Ubuntu (as does XP) looks for the strongest "cell" and links to it.

> Just to see if your PC connects. If it does we may know the culprit...
It connects fine in live CD mode and immediately after a fresh HD install.  Something's being auto-trashed in the configuration upon reboot, apparently.

Some of the IPs look fishy in the ifconfig info:

net addr:192.168.1.93 [COLOR="Magenta"]Bcast:192.168.1.255[/COLOR] Mask:255.255.255.0

This looks wrong to me; I don't recognize "Bcast" there.

---

### Post by Daniel15 on 2006-10-28
Check the output of 'dmesg' and 'cat /var/log/messages' for anything related to the wireless card.

Try installing NetworkManager (find the package in Synaptic, if you still have Internet access on the PC), and see if you can connect to the wireless network using that.

> This looks wrong to me; I don't recognize "Bcast" there.
Bcast is the broadcast address. 192.168.1.255 is correct for a 192.168.1.xxx network.

---

### Post by Bezmotivnik on 2006-10-28
> **Daniel15 said:**
> Check the output of 'dmesg' and 'cat /var/log/messages' for anything related to the wireless card.
Will do when I fire it up tomorrow.

> Try installing NetworkManager (find the package in Synaptic, if you still have Internet access on the PC)

Unfortunately, I don't now that wireless is dead on the box.

> Bcast is the broadcast address. 192.168.1.255 is correct for a 192.168.1.xxx network.
OK, that's good.

BTW, I did a static IP for the box with the network connection GUI because the nearest repeater chokes on DHCP function for some mysterious reason with either OS and therefore the WiFi connects to the weaker signal directly from the AP, but this change made no difference in the outcome.

It's so weird that I can access the net in live mode or after a fresh install, but something misconfigures itself on reboot. :-k

---

### Post by wieman01 on 2006-10-28
The file that controls your network settings is this one (from command line):
> sudo gedit /etc/network/interfaces
Post the contents so that we know what's going on in there.

---

### Post by tturrisi on 2006-10-28
Make it easier to t-shoot...if one of those Linksys APs belongs to you then access the AP control center & change the SSID from Linksys to a unique name like Bezmotivnik or Bezwaninthelan or some name that you dig.

---

### Post by wieman01 on 2006-10-28
> **tturrisi said:**
> Make it easier to t-shoot...if one of those Linksys APs belongs to you then access the AP control center & change the SSID from Linksys to a unique name like Bezmotivnik or Bezwaninthelan or some name that you dig.
That's the point of this thread... He can't. He has got one network & several repeaters that belong to it. So that's why we see a number of network with the same ESSID & different MAC address.

---

### Post by psycosmyth on 2006-10-28
your routers are using default settings ie. "linksys", chan 6, these are so common, I'd change a name or two, Do you have to use XP for that?
I WARdrive so this IP and configuration is very familiar. I don't know why your live disk is different, I thought it only dumped language files.Who's your isp?

---

### Post by Bezmotivnik on 2006-10-29
> **psycosmyth said:**
>  I'd change a name or two, Do you have to use XP for that?

Can't be done.  

These cheap repeaters will reflect the AP's name only.  I have to tell this stuff apart from the MAC numbers. :rolleyes:  It's incredibly annoying.

> I don't know why your live disk is different...

Yes, let's not get too distracted here -- the thing works fine (1) in the "Live" CD mode and (2) after a fresh install.

It only fails after the first reboot on the new installation and never works again.  The problem isn't with the hardware or the net.  It's with Ubuntu changing its wireless configuration that worked into one that doesn't. :-k 

We need to figure that out.

Which are the relevant config files to view for this?  

As always, thanks for any help!:p

---

### Post by wieman01 on 2006-10-29
Alright, it seems we need to get our hands a bit dirty then. This file controls your network interfaces (as the name suggests):
> sudo gedit /etc/network/interfaces
Please post the contents.

---

### Post by Bezmotivnik on 2006-10-29
> **wieman01 said:**
> Alright, it seems we need to get our hands a bit dirty then. This file controls your network interfaces (as the name suggests):

Please post the contents.

OK, see bottom -- wlan0 looks fine to me -- but first...

After a long, bloody and totally unrelated hardware battle this AM, I now have the thing magically online at bootup, connected to the strongest repeater (that's its MAC in "Access Point:"):

anonymous@x:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"linksys"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:A5:8E:1C:35
          Bit Rate:54 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=56/92  Signal level=42/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
wireless-essid linksys
address 192.168.1.93
netmask 255.255.255.0
gateway 192.168.1.254

=====================================

I have a static IP for this as the cheap repeaters have trouble with DHCP.

I wonder if this will come back up on reboot. :-k

---

### Post by Bezmotivnik on 2006-10-29
Well...I did a full update of everything online, rebooted and I'm still up.

I have no idea how this chronic problem corrected itself.

However, I am now online.

Thanks for the help, and I'll keep you posted!  :-k

---

### Post by wieman01 on 2006-10-29
Great! Learned something new about repeaters. Good luck then & see you next time.

---

