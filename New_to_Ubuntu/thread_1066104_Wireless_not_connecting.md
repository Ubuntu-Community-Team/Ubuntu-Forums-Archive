---
title: "Wireless not connecting?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by PressureX on 2009-02-10
Hello everybody,

So my dad got Linux installed on his computer, and since I've had redhat before a couple of years ago, I figured Ill come back at it. Well, I chose Ubuntu Intrepid (8.10).

Now, I've been working on this since last night, and Im finally at the point where It finds the Wireless Networks, but everytime I want to connect to it, it wont connect.

I thought well maybe it s because of the WEP, so I took the key off, now it's unlocked, but it still wont connect. It will try, but always fails.

in sudo lshw -class network I get this for my wireless card:

```
*-network
description: Network Controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 8
bus info: pci@0000:01:08.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latentcy=32 module=ssb
```

Now I am VERY new to all of this, barely know anything, but im def. willing to learn.

Can anybody help me on how I can get it to connect?

P.S.: I can't try to get it connected through cable since I don't have a way of getting a cable up here. So I don't even know if it would work through cable.

Thank You very much!

---

### Post by JK3mp on 2009-02-10
Try 
1. Click on the network-manager icon, then on manual configuration.
2. Highlight Wireless connection, then click on properties.
3. Remove tick (roaming mode), and enter something you like in ESSID, password type, network password and set connection settings to match your needs (for me DHCP). Click OK.
4. Open a terminal and type
Koodi:
sudo /etc/init.d/networking restart

---

### Post by PressureX on 2009-02-10
> **JK3mp said:**
> Try 
1. Click on the network-manager icon, then on manual configuration.
2. Highlight Wireless connection, then click on properties.
3. Remove tick (roaming mode), and enter something you like in ESSID, password type, network password and set connection settings to match your needs (for me DHCP). Click OK.
4. Open a terminal and type
Koodi:
sudo /etc/init.d/networking restart

Thank You. I went to the Network Manager (I hope this is the one your talking about, this is a screenshot I found on the web [http://regmedia.co.uk/2008/11/03/ubuntu_network_manager_big.jpg](http://regmedia.co.uk/2008/11/03/ubuntu_network_manager_big.jpg)), highlighted my wireless network, and clicked edit.

1) There is no "roaming mode", the only things I can tick is Connect automatically and System setting.

2) there is a BSSID, but not a ESSID.

Well, after everything, it still doesn't connect, but it finds all the available networks and even shows signal strength, but it wont connect to any, not even if they dont even have a PW on it.

---

### Post by PressureX on 2009-02-10
Can anybody else help me? Please? Im about frustrated with this, lol. If I click on my network, it waits a while, then a "Authentication required by wireless network" dialog comes up and asks me to put in the Key again. Well, I already tried this like 15 times but it just keeps popping up.

And when I try to connect to a network that doesn't need a key, it will just say "trying to connect to xxx network" and then "Disconnected. The network connection has been disconnected"

---

### Post by Neural oD on 2009-02-10
make sure that your "wired" connection is not active. In the terminal type this: sudo ifconfig 
then look if you see your wired connection - it should be something like eth0. Then type in sudo ifdown eth0(or whatever yours is called)

---

### Post by PressureX on 2009-02-10
> **Neural oD said:**
> make sure that your "wired" connection is not active. In the terminal type this: sudo ifconfig 
then look if you see your wired connection - it should be something like eth0. Then type in sudo ifdown eth0(or whatever yours is called)

I got eth0, eth1, lo, wlan0, and wmaster0, when typing the command you gave me, it says:

ifdown: interface eth0 not configured

---

### Post by Neural oD on 2009-02-10
make sure that your eth1 is also down: sudo ifdown eth1

---

### Post by Neural oD on 2009-02-10
try this - as your network manager could be conflicting: 
sudo pkill NetworkManager
sudo ifdown eth0
sudo ifdown eth1
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "whatever it is - without quotes"
sudo iwconfig wlan0 channel "put your channel here"
sudo ifconfig wlan0 up
sudo dhclient wlan0

---

### Post by geroad on 2009-02-10
> **Neural oD said:**
> make sure that your eth1 is also down: sudo ifdown eth1
There have been a lot of problems with "Network Manager". I now use
"Wifi-radar". Its available in the Add/Remove Application and
Synaptic Package Manager.

---

### Post by PressureX on 2009-02-10
> **Neural oD said:**
> try this - as your network manager could be conflicting: 
sudo pkill NetworkManager
sudo ifdown eth0
sudo ifdown eth1
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "whatever it is - without quotes"
sudo iwconfig wlan0 channel "put your channel here"
sudo ifconfig wlan0 up
sudo dhclient wlan0

What is the "channel"? I don't think I've ever heard about "channel" ... essid I guess is my SSID (router name, network name, whatever you wanna call it), right?

---

### Post by PressureX on 2009-02-10
Ok, tried everything. As channel, I put in the wireless channel (which is 8 for me)

Here is what happened after the last command:

```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0f:66:1c:81:91
Sending on LPF/wlan0/00:0f:66:1c:81:91
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by PressureX on 2009-02-10
Anybody else able to help me?

---

### Post by PressureX on 2009-02-10
I just followed these directions:

[http://www.pci-il.com/support/showthread.php?t=64](http://www.pci-il.com/support/showthread.php?t=64)

Everything worked (well, beside the app-get commands, I got them manually on a flash drive and did it that way). But I still have the same problem ... I find all the wireless networks, but it won't connect to any of them .... help :(

---

### Post by Neural oD on 2009-02-11
Are you sure that there is no encryption on the link. Also make sure that your router is set as a dhcp server - that it can hand out addresses.

---

### Post by PressureX on 2009-02-11
> **Neural oD said:**
> Are you sure that there is no encryption on the link. Also make sure that your router is set as a dhcp server - that it can hand out addresses.

I don't really know what you mean by "Are you sure that there is no encryption on the link.". But yes, my Router (I just double checked) has DHCP Enabled.

---

### Post by PressureX on 2009-02-11
bump. Anybody? :(

---

### Post by ugm6hr on 2009-02-11
You do not need ndiswrapper.

You need the firmware for the b43 driver, which supports the bcm4306.  If you can't get online with wired, you won't have it.

Try this: [http://ubuntuforums.org/showpost.php?p=6658081&postcount=99](http://ubuntuforums.org/showpost.php?p=6658081&postcount=99)

---

### Post by KC1117 on 2009-02-11
I'm so new I can't help you, but if you don't get any responses in this thread I recommend posting your question again in the Networking and Wireless section where the experts on this look to help people.  Tell them your pc model, wireless hardware, linux version, etc. to get started.  They will probably ask for more information.

I was posting at the same time as ugm6hr, a staff member.  Please follow his/her advice first.

---

