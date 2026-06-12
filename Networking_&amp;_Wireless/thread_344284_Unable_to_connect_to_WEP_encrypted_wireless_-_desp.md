---
title: "Unable to connect to WEP encrypted wireless - despite being able to before?"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Ted_Smith on 2007-01-22
Hi

I have a Sony Vaio laptop with Dapper Drake installed that's about 4 years old so it's wireless card only supports WEP. So I have my router encryption set as WEP, set an SSID name, hex encryption key etc. My Windows laptop connects fine, and prior to having to reinstall Ubuntu for various reasons my Sony worked fine too so I know the router is OK.

But since I re-installed Ubuntu (Dapper Drake), I can no longer get it to connect. I have used network manager to configure the connection, entered the SSID, got DHCP enabled, password etc. Same as before. But I cannot get it to connect - or even detect - the wireless network. It just seems to think it does not exists.

I can connect via ethernet and used that to update\patch my Dapper install with all the latest updates, and also installed wlassistant, but still no connection. 

Can anyone offer any advice or help?

Summary - WEP encryption, D-LINK G604T Router, Windows laptop connects fine, Ubuntu does not (but used to). 

Thanks

Ted

---

### Post by rmartz on 2007-01-24
Not sure if this will help, but have you tried Wifi-radar? I had a similar problem and found it would handle my settings and allow me to connect to several different types of networks and remember each.

Just a thought.

---

### Post by Ted_Smith on 2007-01-26
I have indeed, and wireless-assistant. 

Since the post above, I baselined my laptop and started from scratch with a fresh install of Dapper Drake. As soon as it rebooted I configured eth1 with the wireless settings (DHCP, encryption key etc). A few seconds later, it connected and I was online. Out of curiotsity I ran iwlist and noted that there was a hex entry where it says 'Access Point', This differed from before because it used to say 'none'. Hoorah, I thought, problem solved. Until I rebooted and now all it ever does is find the signal but doesn't connect!! When I try and use the two tools mentioned they just say 'Cannot connect'. 

So, I started tweaking about with iwlist as follows : 

iwlist eth1 scan
iwlist eth1 ap
iwlist eth1 access point

and various others. And noted that it now says 'Access Point : None'. 

Output of iwlist eth1 scanning :

```

Cell01 - address 'mac address values'
ESSID 'My ESSID'
Mode : Master
Frequency : 2.42 (Channel 3)
Signal Level : 70dBm Noise level :- 96 dBM
Encryption key : on

```

Output of iwconfig :

```

eth1  IEEE 802.11b  ESSID "My Network Name" Nickname "Same as ESSID"

Mode : Managed    Frequency : 2.422Ghz   **Access Point : None**
Bit Rate : 2 Mb/s  Sensitivity : 1/3
Retry limit : 4    RTS thr : off     Fragment thr : off
Power Management : off
Link Quality=24/92  Signal LEvel=70dBm  Noise LEvel = 95dBm
Then a few favlues all equal 0

```

So, by the looks of it, for some weird reason, it knows the wireless signal is there, it has all the correct settings to connect to it, but doesn't know where to? A bit like a homeowner being told "You have to get into the house through the front door using this key" but the homeowner not understanding what is the front door.

Any help appreciated. Note that this is being written with my other laptop running WinXp connected to the same wireless network using DHCP. So I know the router is fine, and the settings.

Ted

---

