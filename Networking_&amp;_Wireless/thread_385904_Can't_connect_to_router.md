---
title: "Can't connect to router"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by mysulf on 2007-03-16
Ok, i've seen alot of posts like these but none seems to adress my problems. I have a wireless router which I can connect to, on the top of my screen there are nice green bars that indicates that i am connected to my router. I have my wireless card sat to dhcp but it seems as though i can't get the right settings from the router. I tried with cable and it didn't work, but a cabled direct connection to the modem works fine.

With iwconfig I get this:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1   IEEE 802.11g  ESSID:"spanien"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:BF:0D:2D:C1   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-14 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:537  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1



route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth1

When I ping the router I get:

PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.

and nothing happens.

Please help me with this, i've searched everywhere.

Btw, i'm new to Ubuntu :roll:

---

### Post by spd106 on 2007-03-16
You seem to getting invalid crypt packets, so it might be worth double checking the encryption key.

---

### Post by mysulf on 2007-03-16
Thx for replying, 
It seems to be correct. With the wrong key i wouldn't be able to 'connect' to the router at all? And it doesn't work with cable either, so something with dhcp-settings?

---

### Post by chili555 on 2007-03-16
I do not believe you are actually *connected* to your router. I think your wireless card *sees* the router, but seeing and connecting are two different things, as I learned with that cute blonde at the pub.

Unless you can ping the router and get a response, you are flirting but not kissing. I am suspicious of your router's IP address above: 192.168.1.2. Are you sure your router is not 192.168.1.1? When the route command didn't come back with a gateway address, it's further evidence you are not *connected.* Here is my route for comparison: ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```

> With the wrong key i wouldn't be able to 'connect' to the router at all? Exactly correct! That's the purpose of encryption: no key, no entry.

Please recheck your encryption key. Here is a post that will help: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

If you are not using WEP, all bets are off. Please search the forum for WPA and there are plenty of gurus who set up WPA.

---

### Post by mysulf on 2007-03-16
Ok, I turned off encryption an tried with the router completely open, no success. And the ip IS 192.168.1.2, i can connect from an XP-machine, the key works from there. And i should be able to connect via cable shouldn't i? Can't ping that way either. 

Tried to go static but no.

It fizzles.

Drivers maybe?

---

### Post by dbott67 on 2007-03-16
There are a number of ways to ease the wireless networking blues, but the best one that I've found is installing this app:

```
 sudo apt-get install network-manager-gnome
```

Read on for details:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

-Dave

---

### Post by spd106 on 2007-03-16
[QUOTE=mysulf]Drivers maybe?[/QUOTE]
I was trying to go for easiest solution first, but you might be right to suspect a driver issue. Which card do you have and which driver are you using?

---

