---
title: "Please help, check out my interfaces file"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by kolslorr on 2007-09-24
Good news first, I finally managed to get ndiswrapper working in my Gutsy! Thanks to the sticky thread on top of here...

The thing is, I find that the interfaces file have been somewhat screwed by me for the past few days, although it works now, but it just doesnt look clean...

Can anyone please help to take a look for me and point out what are the redundant things inside?

```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

iface wlan0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid hillstreet

iface rausb0 inet dhcp
wireless-essid hillstreet

auto rausb0

iface rausb1 inet static
wireless-essid hillstreet
address 192.168.1.99
netmask 255.255.255.0

auto rausb1

iface wlan0 inet dhcp
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid hillstreet

```

Just in case if it helps, heres my iwconfig output...

```
kolslorr@kolslorr:/etc/network$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"hillstreet"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:13:10:23:49:F7   
          Bit Rate=12 Mb/s   Tx-Power:20 dBm   Sensitivity=-115 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

and lshw...

```
kolslorr@kolslorr:/etc/network$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:89:a2:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.48+Linksys,04/01/2004, 1.00.00 ip=192.168.1.99 multicast=yes wireless=IEEE 802.11g

```

---

### Post by kevdog on 2007-09-24
In your intefaces file comment out every line (based on what you presented) that doesnt contain a lo or wlan0 statement.  Oftentimes its better to make a copy of the current file b/c with many changes its hard to decipher what the original file looked like:

sudo cp /etc/network/interfaces /etc/network/interfaces.bak

---

### Post by kolslorr on 2007-09-24
Hey! thanks!.. that was fast~~

I followed your suggestion to comment all those unnecessary ones... and it works well now...

one thing though... After 1 reboot the initial wlan0 connection automatically changed to rausb0... and I thus had to enable rausb0 instead of wlan0... 

why this happened, i have no idea... maybe some kernel upgrade did some funny thing to it...

---

### Post by kevdog on 2007-09-24
You can change the name of the interface in the /etc/iftab file if you want.  ie from rausb ->wlan0 if you want.

---

