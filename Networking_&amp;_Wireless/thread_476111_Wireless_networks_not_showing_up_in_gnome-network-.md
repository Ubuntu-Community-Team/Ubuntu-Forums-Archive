---
title: "Wireless networks not showing up in gnome-network-manger on an Intel 3945"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by danhm on 2007-06-16
I have no idea when this happened since I'm normally on a wired connection, but this weekend, I'm staying at my parent's house who have a wireless network. I've connected to it before many times, but this time I can't see it when I click on the network manager icon -- my only choices are "Wired Network" and "Manual Configuration". If I select manual and enter the network's information, it does not connect.

My iwconfig output:
```
dan@dan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"<hidden>"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:0

```

And my /etc/network/interfaces:
```

dan@dan-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid <hidden>
wireless-key [the hex]

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1

```

What can I do to repair this? As I mentioned, I have an Intel/Pro 3945ABG wireless card. It looks like I have a lot of junk in my interfaces -- does something have to be removed? 

I am sure the card isn't faulty because it works great under Windows (I just tried it).

---

### Post by danhm on 2007-06-16
I fixed the problem by changing my interface file to:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid <hidden>
wireless-key [the hex]


```

---

### Post by Cain67 on 2008-03-28
Hi, i know this probably isnt the right thread to be posting on... but after searching about wifi, network manager, wpa_suppliant.conf, interface files, blah blah blah etc...
im still clueless and unable to connect without a wire....

basically, im using a macbook with ubuntu 7.10 and have gnome-network-manager, and wpa_supplicant is installed, however i have no wpa_supplicant.conf to play with... and am way to new to linux to get into that....

iwconfig gives me my card:

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:70343  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

all interface contains is :

auto lo
iface lo inet loopback

auto ath0


and when i click on the network manager icon, i get wired connection, and the title for wireless networks, but no networks listed, which cant be right as i have multiple networks in my home...

any help would be GREATLY appreciated!!!
thanks

will keep googling in the mean time.

---

