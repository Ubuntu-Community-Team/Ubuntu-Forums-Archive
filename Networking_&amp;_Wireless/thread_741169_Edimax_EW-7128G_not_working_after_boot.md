---
title: "Edimax EW-7128G not working after boot"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by razta on 2008-03-31
Hello,
Im a week old to linux. Bought a wireless card from EBay "Edimax EW-7128G Wireless LAN PCI Card" got it working using the following instructions:

[http://ubuntuforums.org/showthread.php?t=156075](http://ubuntuforums.org/showthread.php?t=156075)

I turned off the PC and when I turned it back on again it wont connect. It shows up in Network Settings ticked with correct configuration.

This is my interface file:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-essid RYAN
wireless-key **********
address 192.168.0.1
netmask 255.255.255.0

auto ra0





auto eth0
```

iwconfig shows:
```
ryan@ryan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The above for some reason is not showing the ESSID.

PING shows:
```

ryan@ryan-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 169.254.3.17 icmp_seq=3 Destination Host Unreachable
From 169.254.3.17 icmp_seq=4 Destination Host Unreachable
From 169.254.3.17 icmp_seq=5 Destination Host Unreachable

```

I also have KWiFi Manager installed which shows all the SSIDs of networks in range including "RYAN" but says "no access point" and "local IP unavailable". Im using ubuntu 7.04.

Any one know how I can fix this? Thanks in advance!

---

### Post by nixscripter on 2008-03-31
A few questions:

1. What does **ifconfig** show after you try to connect? In particular, I'm trying to figure out where does the 169.254.3.17 address come from in the "unreachable message"?

2. What are the other interfaces eth0, eth1, eth2?

3. When you try to connect with the network, run **iwconfig** again, so that the ESSID is associated with your machine. In particular, what is that "Link quality" number?

---

### Post by razta on 2008-03-31
Thanks for the reply, since the post I have succsesfully updated to 7.10 and did a complete new install so the drivers are not loaded. I was hoping 7.10 would recognise the card out of the box but it hasnt. Going to try and install the drivers again and see what I come up with this time. 

I was also wondering about that IP address you mentioned, I have no idea where it came from.

Edit====

Did not need to install drivers, wireless seems to have been detected 'out of the box'. Everything working fine in 7.10. :)

---

