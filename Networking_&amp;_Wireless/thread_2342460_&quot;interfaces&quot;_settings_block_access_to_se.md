---
title: "&quot;interfaces&quot; settings block access to server from internet"
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by TripleD on 2016-11-06
When I enable eth0 in my /etc/network/interfaces I am unable to connect to my server from the internet. If I disable it everything works just fine.

I have a Raspberry Pi (no-GUI Raspian) and a desktop (Ubuntu 16.04) connected to the internet via Wi-fi. The Pi has lighttpd running for a web server, dynu.com has given me a Dynamic DNS, which I have set up to work with my TomatoUSB router. Port forwarding has been enabled for port 80 and ssh to both of my machines.

Here's where the trouble happens. When I access the web server or attempt to ssh into the Pi from home (using either "192.168.1.X" or "myname.dynu.com") I am able to do both just fine. But if I switch to any other network and try to access "myname.dynu.com", I get a "server could not be found" message.

After a lot of troubleshooting I found the problem. My Pi is connected to my desktop via an ethernet cable. I wanted to use Wake-on-Lan with my desktop, but my router is not located in my home office. So instead I wrote a simple sniffing program on the Pi to detect WiFi magic packets, then use "wakeonlan" to send a magic packet to the desktop. The Pi is on two networks: eth0, where it acts as a gateway, and wlan0, where it is just a host. When I tried disabling eth0 in /etc/network/interfaces, and unplugging the ethernet cord, suddenly the server worked just fine.

Is there something wrong with the way I set up "eth0" in /etc/networks/interfaces? Is the setup I'm going for even possible? I'm weak in network configuration, so a lot of this is cobbled together from other sources. 
[B]
/etc/network/interfaces[/B]
```

# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

auto lo
iface lo inet loopback

allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
    wpa-ssid mynetwork
    wpa-psk mypassword

#####################
# Causing the Problem
#####################
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.255.255.0
gateway 10.0.0.1
broadcast 10.0.0.255
network 10.0.0.0
#####################

allow-hotplug wlan1
iface wlan1 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

---

### Post by ian-weisser on 2016-11-07
You must bridge or otherwise connect the 192.* network and the 10.* network, so machines on one network can see machines on the other network.

There are several ways to do it.
For example: You can have the router assign a 192.* address to the pi, and use the Ubuntu machine merely as a (temporary) pass through. This has an advantage of portability, but initial setup is more complex.

Another example: You can retain your existing setup, and create an Ubuntu IPTables rule to port-forward packets for the PI. This is simpler to set up, but you PI will require the Ubuntu system to act as gateway to the larger internet (limiting it's 'always-on' usefuness).

EDIT: Upon reflection, my comment above seems flat wrong. I misread the problem - the Pi is clearly already on the 198.*network.

---

### Post by TripleD on 2016-11-07
I don't think a bridge would help. The web server is on the Pi, which is connected to the router over Wi-fi. The Raspberry Pi only acts as a Gateway for the ethernet connection. The Desktop and Pi are both still connected to the WiFi. I have run ping tests on both; they can see each other fine on both their wired and wireless connections.

I checked the arp tables and discovered something curious. Any connection from outside the network has "eth0" listed as its interface when the Pi has its LAN cable plugged in. I suspect that any requests which are coming in the "wlan0" interface are being sent out on the "eth0" when it is available, essentially just dumping them. Thing is I'm not even sure how this is possible, let alone how to correct it.

---

