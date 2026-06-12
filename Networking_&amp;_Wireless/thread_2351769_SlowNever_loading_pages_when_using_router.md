---
title: "Slow/Never loading pages when using router"
date: 2017-02-06
forum: Networking &amp; Wireless
---

### Post by Parapan on 2017-02-06
Hello,


I am using Ubuntu 16.04 and some websites and network requests have very slow load times until a timeout occurs.


**Hardware setup :**
PC > cat5 cable > 2 Port Router (Tried both ports)
Router(WAN Port) > cat5 cable > ADSL Modem


**These changes didn't work :**
Uninstalling Network Manager
Changing settings in /etc/network/interfaces (static / dhcp / static with google DNS servers)
Commenting out / Uncommenting dnsmasq in /etc/resolv.conf
Changing the router's DNS settings to auto/manual
Using a wireless USB adapter and disconnecting the cat5 cable from the PC
Rebooting Ubuntu after each of the above changes


**What works :**
Using the above hardware setup with Windows 10
Connecting the PC to the ADSL modem directly and running any combination of (Running/Disabling network manager, using static or dhcp with DNS entries)


Thanks for reading

---

### Post by The Cog on 2017-02-06
You say some web sites. Do others load OK then?
Can you name one that works OK and one that doesn't?
Can you post the output of the command **ifconfig** ?

---

### Post by Parapan on 2017-02-06
Entire sites not loading was rare, one that I can think of now is eBay.in... Most other websites that I use seem to load OK.. 

My main concern was when I was running a Fileupload in a cPanel while using my hosting account with a2hosting.com.. The zip files that I tried to upload always got stuck at 2% after trying many times. On Firefox and chrome. 

I've mostly experienced it for certain sections of sites that involve some ajax calls, or other sections that cause the page to be incompletely rendered as it times out. 

When I tried to make my previous post or reply to yours, the firefox tab stopped responding as soon as I pressed the submit button. On chrome, I couldn't make it past the login into the forums. Had to make a direct connection to the ADSL modem for this..


ifconfig (While connected to the router using a cable):

```
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:54:8e:4e  
          inet addr:192.168.1.9  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19285338 (19.2 MB)  TX bytes:5874238 (5.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:158827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158827 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:11691943 (11.6 MB)  TX bytes:11691943 (11.6 MB)

```

---

### Post by The Cog on 2017-02-07
Hmm. Not got IPv6. You are using NAT in the router. All that looks normal. 
Just a thought - maybe it's an MTU issue. Try this command to drop the MTU from 1500 to 1450:
```
sudo ifconfig eth0 mtu 1450
```
It's only temporary, until you reboot (or reconfigure it back again). 
Equally, try disabling TCP window scaling (again until reboot)
```
sudo sysctl -w net.ipv4.tcp_window_scaling=0
```
That's all I can think of.

---

### Post by Parapan on 2017-02-07
> **The Cog said:**
> Hmm. Not got IPv6. You are using NAT in the router. All that looks normal. 
Just a thought - maybe it's an MTU issue. Try this command to drop the MTU from 1500 to 1450:
```
sudo ifconfig eth0 mtu 1450
```



The mtu change works great! I've changed the mtu from 1500 to 1492 in the router. I will check the IPv6 status as well.. Thanks a ton The Cog! Been trying to figure this out for months..

---

