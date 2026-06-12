---
title: "Connecting to a wifi router to see it's Admin page"
date: 2018-02-14
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2018-02-14
I have a wifi router and I want to connect it to my Ubuntu OS computer.

I have tried to create a second Network Connection using the Network Manager.

I gave an IP address of 192.168.1.22 to this network and ran a cable from the WAN (internet) port of the router to the ethernet port on this computer. 

In fact I tried several addresses at the Network Manager, such as: 192.168.1.1, 2.1.

This is a known to be working device.

FWIW, the router is a TP-Link Archer C7 v2 wifi router. Admin is: [http://tplinkwifi.net](http://tplinkwifi.net)

---

### Post by SeijiSensei on 2018-02-14
You need to be connected to the LAN side of the router to see its admin page.  You'll need to let the router's DHCP server give your client machine an address as well.

Exposing the admin page on the WAN side of the connection would create a security hole, especially if that side were connected to the Internet.

---

### Post by chili555 on 2018-02-14
May we assume that you want to connect to the router to administer it; that is, change its settings, wireless channel, SSID name, WPA2 password, etc.?

I own and use a TP-Link Archer C7, although mine is a version 1. To connect to it to do administrative tasks, I simply type its IP address into my browser's address bar. In the case of my version 1, the address is 192.168.0.1.

Once you are connected to it and have an address, confirm the address with the terminal command:```
route -n
```My machine reports:```
Kernel IP routing table
Destination     [COLOR="#FF0000"]Gateway [/COLOR]        Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [COLOR="#FF0000"]192.168.0.1[/COLOR]     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

```My Archer requires a password for administration and so when you log on, beyond viewing (but not changing) a few basic details, you will need to know and provide the password.

If you are unable to connect until you administer the router, you may be able to conect the ethernet and then ask the router for an address by DHCP:```
sudo dhclient enpXsY
```...wher enpXsY is your ethernet interface; check:```
ifconfig
```My results as an example:```
chili@T440p:~$ ifconfig
[COLOR="#FF0000"]enp0s25[/COLOR]: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether xx:f7:28:ae:83:xx  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xe0600000-e0620000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 37288  bytes 2749412 (2.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 37288  bytes 2749412 (2.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by Mark_in_Hollywood on 2018-02-14
This router (TP-Link Archer C7 v.2) will eventually sit behind the modem (AT&T Arris NVG599) and have OpenWRT and OpenVPN in use. At the moment, I do not want this device connected for internet. I only want to be able to access the Admin page in order to install the OpenWRT (flash the) firmware. 

Quoting Mr. SeijiSensei:
"You'll need to let the router's DHCP server give your client machine an address as well."

Is this true when the only Ethernet cable connection is from the LAN or WAN to the computer?

-----

For chili555

As you quote Dr. Sheldon Cooper, I thought it only appropriate to return to the Lone Gunmen (X-Files) and say: Frohike has to admit that Langly&#8217;s &#8220;kung fu is the best.&#8221; (I'm not worthy).

---

### Post by lisati on 2018-02-14
If I have read this thread correctly, the WAN port won't actually be connected directly to the internet, but to another device (e.g. switch, router, etc) on your LAN. Is this your plan? Talk of using the WAN port might have some of our number worrying that you might want to access the device via the internet.

On network devices I've configured, I've generally done the initial setup by connecting my laptop directly to one of the regular ethernet/LAN ports, and then navigating to the admin page, usually with an address something like 192.168.1.254.

---

### Post by Mark_in_Hollywood on 2018-02-15
"If I have read this thread correctly, the WAN port won't actually be connected directly to the internet".

I don't know how to respond to this. For the purpose of using the router's Administration page I understand that I should connect a cable between the router's WAN (labeled internet and yellow in color) port and my computer's ethernet port. Getting the device networked or usable for it's intended purpose comes after installing (flashing) the firmware with open source software.

---

### Post by chili555 on 2018-02-15
It only takes one minute to try either method.

Please check page 9 of the manual here: [https://static.tp-link.com/res/down/doc/Archer_C7_V2_UG.pdf](https://static.tp-link.com/res/down/doc/Archer_C7_V2_UG.pdf)

> The default IP address of the router is 192.168.0.1 and the default Subnet Mask is 255.255.255.0.
These values can be changed as you desire. In this guide, we use all the default values for
description.
Connect the local PC to the Ethernet ports of the router and then you can configure the IP address
for your PC by the following method: Set up the TCP/IP Protocol in "Obtain an IP address
automatically" mode on your PC. My very strong suspicion is that, in less time that it took me to write this post, you can plug in the router, hook the ethernet cable to the LAN port as described in the manual and see if Network Manager connects. Open your browser and enter:```
http://192.168.0.1
```I believe the admin page will open. Done.

---

### Post by Mark_in_Hollywood on 2018-02-15
I made a new "Ethernet Connection 1" then connected the router to the 'puter's port. Warmbooted. Called Opera browser. Tried to open Admin page. Fail. Called Google's Chrome, used [http://tplinkwifi.net](http://tplinkwifi.net) to login. Admin page comes up. Using default Admin/Admin Chrome denies access saying site is insecure. Screenshot attached with some info.

Ethernet Connection 1 is an extra, default created by Ubuntu, using Add in Conn Mgr.

---

### Post by chili555 on 2018-02-15
I don't understand. The manual says the default address is 192.168.0.1 and that it is the suggested way to connect.

You, instead, set up 10.0.1.100 and try to connect to [http://tplinkwifi.net/](http://tplinkwifi.net/).

I'm confused.

---

### Post by Mark_in_Hollywood on 2018-02-15
Bought used. Original owner had configged as you saw. Apologies. Upon button reset Admin page is reachable.

---

### Post by Mark_in_Hollywood on 2018-02-15
Thank you, Ubuntu Community.

---

