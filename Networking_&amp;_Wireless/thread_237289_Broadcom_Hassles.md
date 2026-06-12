---
title: "Broadcom Hassles"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by stormyeyez on 2006-08-15
I have a Presario R3240US with a Broadcom BCM4306 802.11b/g Wireless LAN Controller (rev 03) wireless card built in. I have been using the guide [here]("http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear") to try to get it working. I went through all the steps, rebooted, and instead of showing wireless connection it showed wired connection. When I right click on my Network Connection I get this:

[IMG]http://static.flickr.com/57/216520155_23301a1450.jpg?v=0[/IMG]

When I click Configure I get this:

[IMG]http://static.flickr.com/97/216520153_111d0ea5bb.jpg?v=0[/IMG]

It says it is active, but I can't get it to work. The weird thing is (to me anyway) is when I click Properties for Eth1 the light that indicates my card is powered on comes on briefly, but then turns off. I have tried setting the default gateway device to Eth1, but that didn't help. Plus it seems odd to me that the wireless connection is labeled "Eth" to begin with, I am very new to Ubuntu and Linux in general and any help would be greatly appreciated. TIA

---

### Post by wieman01 on 2006-08-16
To get started, could you post this file, please: "/etc/network/interfaces"

Simply open it this way using a terminal and paste the content:
> gedit /etc/network/interfaces

Also run these commands and tell us what the output is:
> ifconfig
> iwconfig

---

### Post by stormyeyez on 2006-08-16
Ok. Here is what I have... iwconfig says my access point is invalid but I don't know why.

> /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid Heather

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth1

auto eth0


>  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:04:4C:C2
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe04:4cc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:898746 (877.6 KiB)  TX bytes:210440 (205.5 KiB)
          Interrupt:185 Base address:0x6800

eth1      Link encap:Ethernet  HWaddr 00:90:4B:5D:5F:77
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3822 (3.7 KiB)
          Interrupt:11 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)



>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Heather"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


---

### Post by wieman01 on 2006-08-16
What is your router's configuration? E.g. DHCP, Static IP, WEP, WPA, etc.

---

### Post by stormyeyez on 2006-08-16
DHCP

We have it set up where the cable modem hooks to a wired router and a wireless access point is hooked up to the router as well. This worked before I switched to Linux but I don't know if it'd be an issue now.

---

### Post by haiku99 on 2006-08-16
I had similar results w/ various guides, finally got wifi working after I loaded the latest ndiswrapper using the howto at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
worth a try, worked w/ my Broadcom 4311....

---

### Post by wieman01 on 2006-08-16
What confuses me here is that you have a number of entries in your "interfaces" file that relate to wireless adapters (eth1, wlan0, ath0). What driver have you used if I may ask?

Have you seen this (bug report)?

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/32152]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/32152")

---

### Post by stormyeyez on 2006-08-16
I used the wl_apsta.o driver when I was follwing the above mentioned guide.

---

### Post by stormyeyez on 2006-08-16
I thought I made a little headway, but I don't know that I did. I saw in another thread you could type the connection you want to connect to in the Network Connection box. I did that and it showed a signal strength of 100. So I tried to enable networking and it wouldn't do anything. I rebooted and then I couldn't even get it to show a signal strength again. Through it all my little wifi power light neer came on either. I just don't know.

---

### Post by stormyeyez on 2006-08-20
Just an update...it started working....:confused: for whatever reason....the power light isn't on, it says No Network Connection but all of a sudden it works. No clue why....but not complaining.

---

### Post by wieman01 on 2006-08-22
Wow! Anything else we can help with? If not, we close this thread.

---

