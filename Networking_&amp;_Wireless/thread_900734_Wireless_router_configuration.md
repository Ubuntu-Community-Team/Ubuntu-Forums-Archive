---
title: "Wireless router configuration"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by The-Russ on 2008-08-25
What's up Ubuntu people,

I was just given a wireless router and
I'm not sure how to configure it. I know a little about networking and I currently have it hooked up to a switch, which connects my computers to my cable modem. I would like to keep this physical configuration, and the wifi is working fine for my one wireless device, but I'd like to set up an encryption key and I can't seem to be able to figure out how to access the router's settings. I've configured routers before by typing the IP address into a browser, and I know I'm makinG myself sound like an idiot, but how do I even find the wireless router's IP address? And when I find it can I just type that into a browser like normal? Any help would be greatly appreciated. Thanks!

---

### Post by Ichido on 2008-08-25
In Terminal type *ifconfig*
This should give you some info.
Mine shows:

your pc's name:~$ ifconfig

**wlan0**     Link encap:Ethernet  HWaddr [MAC Address]  
               **inet addr:175.120.3.100**  Bcast:175.120.3.255  Mask:255.255.255.0
               inet6 addr: ad71::21f:6dhh:fea1:929b/64 Scope:Link
               UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
               RX packets:29306 errors:0 dropped:0 overruns:0 frame:0
               TX packets:23877 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000 
               RX bytes:35736050 (34.0 MB)  TX bytes:3582087 (3.4 MB)


The wlan0 shows my Router's internet address (I.P.) for controls.
(Note: the IP Listed is false, for security reasons.)

OR: Contact your Router's Manufacturer for your correct I.P. to login for the controls.

**_Web Sites everyone should check out!_**

wpa keys:
[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

check your security:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

hard disk wiping program:
[http://www.dban.org/](http://www.dban.org/)

[http://netsecurity.about.com/od/computersecurityglossary/Glossary_of_Terms_and_Definitions_Related_To_Computer_Network_Security.htm?nl=1](http://netsecurity.about.com/od/computersecurityglossary/Glossary_of_Terms_and_Definitions_Related_To_Computer_Network_Security.htm?nl=1)

---

### Post by caljohnsmith on 2008-08-25
> **Ichido said:**
> In Terminal type *ifconfig*
This should give you some info.
Mine shows:

your pc's name:~$ ifconfig

**wlan0**     Link encap:Ethernet  HWaddr [MAC Address]  
               **inet addr:175.120.3.100**  Bcast:175.120.3.255  Mask:255.255.255.0
               inet6 addr: ad71::21f:6dhh:fea1:929b/64 Scope:Link
               UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
               RX packets:29306 errors:0 dropped:0 overruns:0 frame:0
               TX packets:23877 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000 
               RX bytes:35736050 (34.0 MB)  TX bytes:3582087 (3.4 MB)


The wlan0 shows my Router's internet address (I.P.) for controls.

Actually, the "inet addr" that you highlighted above, Ichido, is the LAN address of your computer, not the router.

The-Russ, one way to find your router's LAN address is to do:
```
john@TECH5321:~$ [COLOR="Blue"]route -n[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         [COLOR="Blue"]192.168.1.1[/COLOR]     0.0.0.0         UG    100    0        0 wlan0

```
Look for the address next to the 0.0.0.0 entry, and that will be your gateway (i.e. your router). You can use that address in your web browser to access your router's settings.

---

### Post by Ichido on 2008-08-25
caljohnsmith,
Thanks for the correction :oops:

---

### Post by zamadatix on 2008-08-25
ive done some googlieing and that didnt help uch, how the heck am i supposed to figure out what my wireless driver is (i didnt see any restricted drivers) and how am i supposed to have this scan for networks???

---

### Post by Ichido on 2008-08-25
Try this in Terminal:

sudo lshw -C network

---

