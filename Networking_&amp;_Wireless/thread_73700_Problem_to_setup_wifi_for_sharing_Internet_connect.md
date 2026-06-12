---
title: "Problem to setup wifi for sharing Internet connection"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by der_kaiser on 2005-10-09
Hello,
I have 2 computers using Ubuntu :
- A desktop directly connected to Internet using a DSL modem, and equiped with a PCI Wifi Card (will be used as gateway)
- A Laptop equiped with Wifi.
The Wifi hardware seems to be correctly setup by Ubuntu, and the quality of wifi connection is around 90%.
My network settings are : 
The desktop (gateway) : 
IP : 192.168.0.1
Netmask : 255.255.255.0
Brodcast : 192.168.0.255
The Laptop : 
IP : 192.168.0.2
Netmask:255.255.255.0
Broadcast : 192.168.0.255
Gateway : 192.168.0.1

I've tried to connect to Internet from the laptop, but without success...
Internet is working well with the desktop.
I tried to ping the gateway, and it's working..
I've disabled the firewalls on both computers..

Here is the content of  /etc/network/interfaces 

The desktop  :

mapping hotplug
    script grep
    map wlan0

iface wlan0 inet static
wireless-essid Home
wireless-mode Ad-Hoc
wireless-key fd1f8b6bfe274704bd3e3a5b2a
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255


The laptop :

mapping hotplug
    script grep
    map ath0

iface ath0 inet static
wireless-essid Home
wireless-mode managed
wireless-key fd1f8b6bfe274704bd3e3a5b2a
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.1
broadcast 192.168.0.255

auto ath0


And the output of iwlist :

Desktop :
wlan0     Scan completed :
          Cell 01 - Address: 00:71:76:71:00:B5
                    ESSID:"Home"
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level=19/100  Noise level=0/100
                    Encryption key:off
                    Bit Rate:11 Mb/s

Laptop :
ath0      Scan completed :
          Cell 01 - Address: 46:86:32:04:2F:80
                    ESSID:"Home"
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100


I think that's all!
Has anyone an idea? I've been dealing with this problem since a week!

---

### Post by jasmuz on 2005-10-09
Seems like everything is in order. If you are able to ping both ways means you have them seeing eachother.

On your desktop, open a terminal and type sudo apt-get install dnsmasq 
That will resolve your dns for the laptop or any other computer that will connect to it.

---

