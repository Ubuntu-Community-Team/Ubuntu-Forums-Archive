---
title: "TCP/IP settings"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Drez on 2007-07-10
I´ve been trying to figure out how to set my TCP/IP settings through the terminal in ubuntu. I´m trying to configure a static IP.  Any help would be appreciated.  Thanks in advance.

---

### Post by Mr. C. on 2007-07-10
The **ifconfig** utility sets the IP, broadcast, mask and will set a default route.

The **/etc/resolv.conf** file is where you configure your system to query a DNS server.

There are scripts that bring the network up / down, based upon config files.  How do you want to manage your interface ?

If you have the GUI setup, the Network Manager will be attempting to "help" you manage the network.  Be sure to disable the "auto" entry in /etc/network/interfaces for the interface in question.

MrC

---

### Post by kevdog on 2007-07-11
Here is what I was able to find from a reference source:
[http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

iwconfig [interface] mode managed key [WEP key] (128 bit WEP use 26 hex characters, 64 bit WEP uses 10)

iwconfig essid "[ESSID]"

ifconfig [interface] [IP address] netmask [subnetmask]

route add default gw [IP of default gateway] (Configure your default gateway; usually the IP of the Access Point)

So I would try the following at command line assuming your wireless is wlan0

```

sudo ifconfig wlan0 down
sudo iwconfig mode managed
sudo iwconfig key ****** <---(Need this line only if using WEP, see above)
sudo iwconfig essid ROUTER_NAME
sudo ifconfig wlan0 192.168.1.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1

```

Check everything with
ifconfig

---

### Post by Drez on 2007-07-11
That helps some but I'm still lost.  I tried fooling around with it and of course lost my connection to the internet.  I'm on a different computer right now.

Truthfully, I'm a windows guy and for the last 4 or so days have been stumbling my way through the installation and setup of a linux server.

Could you please give me a step-by-step guide (or maybe just an example) to getting these settings.

Settings for interface eth0:
IP: 192.168.1.215
SubMask: 255.255.255.0
Gateway: 192.168.1.1
DNS 1: 192.168.1.1

Thanks for any help you can give me.

---

### Post by kevdog on 2007-07-11
See above -- substitute appropriate IP addresses, gateway addresses as needed

---

### Post by Drez on 2007-07-11
That somewhat helps but I have a wired connection not a wireless one.

---

### Post by Mr. C. on 2007-07-11
Drez,

Part of the problem is that you're not providing enough information.  Wired?  Wireless ?  Why are you choosing to use the command line to configure your interface vs. the GUI or other ?

We need a little more info to help you help yourself.

MrC

---

### Post by Drez on 2007-07-11
> **Mr. C. said:**
> Drez,

Part of the problem is that you're not providing enough information.  Wired?  Wireless ?  Why are you choosing to use the command line to configure your interface vs. the GUI or other ?

We need a little more info to help you help yourself.

MrC

Yeah your right sorry.

I guess i could use a GUI if there is one.  My interface is iceWM.  I looked for interface settings but couldn't find any.

I have a Ethernet wired connection hooked into a router that goes out to the internet (comcast if you care).  I'm trying to set up ca static IP to the settings mentioned above.

If you need anymore info just ask.

---

### Post by kevdog on 2007-07-11
Sorry my brain is so in tune with wireless -- thats about 99% of the people I help

Try the following assuming eth0 is you interface name:

```

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1

```

Check with  
ifconfig

Again substitute numbers that are appropriate for you

---

### Post by Drez on 2007-07-11
Thank you.  I´m back on the linux computer with the new settings in place and they seem to be working perfectly.  I´ll post again if something isn´t right.  (hopefully I won´t have to post.)

Thanks again!!!!

---

### Post by Mr. C. on 2007-07-11
Excellent.

Note: your settings disappear upon reboot.  Configure a method to reinstate them upon network startup.

MrC

---

### Post by kevdog on 2007-07-11
If you dont want to configure these on the command line everytime you boot, add the following to the /etc/network/interfaces file

```

gksu gedit /etc/network/interfaces

```


```

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

Again substitute values that are appropriate for you!

---

