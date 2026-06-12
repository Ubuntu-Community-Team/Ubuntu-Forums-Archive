---
title: "Can't get card to connect to network"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by darkzim on 2007-06-04
I am a linux beginner, and have just received a laptop with Ubuntu 6.10 installed on it.  

I tried to use my wireless card (netgear wg511 v2, a very infamous card based on research :D), and after a day of messing around, finally managed to get the card to be recognized by the system using NDISwrapper.  

However, I still can not connect to my router for whatever reason.... the status for "wlan0" (the card) is always "disconnected" with no signal...

Here's the output of "sudo gedit /etc/network/interfaces":
> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid 2WIRE539
wireless-channel 6
wireless-key 8109178926





auto eth0


and iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I'm not sure exactly what to do from here...

Thanks, 
darkzim

---

### Post by spd106 on 2007-06-05
Could you also please post the output of these commands?
```
lspci
```
```
sudo lshw -class network
```

---

