---
title: "Wifi card not working with Ubuntu"
date: 2005-09-30
forum: Networking &amp; Wireless
---

### Post by HIGHLIFE on 2005-09-30
I have a D-link DWL-G510 card and im not sure how to set it up in Ubuntu.  This is my only source of internet and i cant get it to work, some one please help.:(  


bare with me ive only had linux for a few days:(

---

### Post by mlomker on 2005-09-30
[Start here.]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+how-to")

---

### Post by tymek666 on 2005-10-01
Well, if you don't have any internet connection under linux better install ubntu from dvd, many packages that usually you have to download using internet are on dvd. And you'll need many of them to setup wifi card...

---

### Post by cesiel1990 on 2005-10-06
Actoully my .inf file is NetA3AB.inf not bcmwl5.inf.  Would I just replace tell it to get the NetA3AB file instead of the bcmwl file from the desktop.

---

### Post by mlomker on 2005-10-06
[QUOTE=cesiel1990]Actoully my .inf file is NetA3AB.inf not bcmwl5.inf.  Would I just replace tell it to get the NetA3AB file instead of the bcmwl file from the desktop.[/QUOTE]

Yes, there isn't a different how-to for every card.

---

### Post by HIGHLIFE on 2005-10-08
Ok I did everything it siad in the guide.  The card shows up in the network settings and I'm under a encrypted wireless network so I added the WEP key, but when I set the card as the default gateway there's no connection. :???:

---

### Post by mlomker on 2005-10-08
Post the output of these:

```

ndiswrapper -l
iwconfig wlan0
ifconfig wlan0
route -n
cat /etc/network/interfaces

```

---

### Post by HIGHLIFE on 2005-10-08
Installed ndis drivers:
bcmwl5  invalid driver!
neta3ab driver present, hardware present
cesiel1990@Davids-Room-Room-Computer-on-Linux:~$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"Waldo"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:27/100  Signal level:-86 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cesiel1990@Davids-Room-Room-Computer-on-Linux:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:11:95:93:70:6D
          inet6 addr: fe80::211:95ff:fe93:706d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:cffe0000-cffeffff

cesiel1990@Davids-Room-Room-Computer-on-Linux:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by mlomker on 2005-10-08
Yeah, it looks like it isn't taking the WEP key.  What does the interfaces file look like?  Can you disable WEP for a while to test your setup?

---

### Post by HIGHLIFE on 2005-10-08
How do i find the interface file?  and im not sure how to disable the WEP i didnt set up the router, but if you need me to I could probably figure it out.

---

### Post by mlomker on 2005-10-08
[QUOTE=HIGHLIFE]How do i find the interface file?[/QUOTE]

```

cat /etc/network/interfaces

```

There's usually a web interface for the router...you just open a browser and type in the IP address.

---

### Post by HIGHLIFE on 2005-10-08
Ok I disabled the WEP, but its still not working.  :(

---

### Post by mlomker on 2005-10-08
Post the output of **iwconfig**.  

Do you have any other security enabled on the router, such as MAC address security?  You've used this same wireless card with that access point from Windows?  If all else fails you can try to hunt down a different Windows driver...sometimes one driver will work and another one won't.

The all-zero's in the hardware address usually means that it's a security problem.

---

### Post by HIGHLIFE on 2005-10-08
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Waldo"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:37/100  Signal level:-71 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.




I dont think there is any Mac security, and yes the card works when i boot in windows.  If this doesnt work what other driver could I use?

---

### Post by mlomker on 2005-10-08
> If this doesnt work what other driver could I use?

I don't know what kind of card it is.  You'd either have to try the manufacturer's website or search Google to find one.

What is the contents of your /etc/network/interfaces file right now?

---

### Post by HIGHLIFE on 2005-10-08
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        network 192.168.0.0
        broadcast 192.168.0.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1



iface wlan0 inet dhcp
wireless-essid Waldo

auto wlan0



auto eth0

---

### Post by mlomker on 2005-10-08
Your file looks fine.  The only thing that I can think of is finding a different driver to try.

---

