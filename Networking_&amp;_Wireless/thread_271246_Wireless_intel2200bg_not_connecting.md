---
title: "Wireless intel2200bg not connecting"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by TomFumb on 2006-10-04
Ok, I hope someone out there knows enough about wireless to help me out with this one. The story goes...

I have a laptop with an ethernet connection (eth1) and a pci wireless card (eth0 (intel 2200bg). I installed xubuntu a few days ago, and during the install it recognised both the network interfaces, but as I didn't have any aerials behind the screen at the time I decided against the wireless. Because the pci wireless was recognised I'm assuming that the all the ipw drivers and ieee drivers were installed automatically with xubuntu (although I'm not terribly sure how to check this, I am fairly new to linux). 

I've had a brief fling with wpa_supplicant to try and get connected with wpa, but so far no luck. The furthest I have gotten so far is by typing:

- iwconfig eth0 ESSID (my network name) key restricted 1 (my hex passcode)

which, if followed by iwconfig, results in the following:

lo     no wireless extensions

eth1   no wireless extensions

eth0   IEEE 802.11g ESSID:(my network name)
       Mode:Managed Frequency:2.462 GHz Access Point: 00:14....
       Bit Rate=54 Mb/s Tx-Power=20 dBm
       Retry limit:7 RTS thr:off Fragment thr:off
       Encryption key:(my encryption key) Security mode:restricted

cted   Power Management:off
       Link Quality=78/100 Signal level=-51 dBm Noise level=-87 dBm
       Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0 Invalid misc:1518 Missed beacon:3

sit0   no wireless extensions.


So, I'm not sure what most of it means, the Missed beacons troubles me a little, but this happens when I'm right next to the router so I'm fairly sure it's not a range issue.

If I go:

- nano /etc/network/interfaces

I get 

# The primary network interface
iface eth0 inet dhcp (I changed this from eth1 in an attempt to make wireless the default network connection).

The strangest thing is that if I go onto the router I can see the laptop as an available wireless station, but not as an attached device, and obviously I have no internet through the connection (why else would I care about a network connection!).

I'm fairly sure that I'm not just being an idiot and doing the settings wrong, if I change anything on the iwconfig essid... command I don't get the same result from iwconfig, I just get IEEE unassociated ...

I know that I'm close to getting wireless going on this laptop, which would be really really cool, so if you have any idea at all what I'm doing wrong please offer me your suggestions

Congratulations for getting this far through my waffle

tomfumb

---

