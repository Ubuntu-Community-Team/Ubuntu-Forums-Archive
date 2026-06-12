---
title: "I see you, you see me...WHY NO DHCP?"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Bingo on 2007-06-10
Ok, I am back on the track of a fix for this monkey.  IBM T21, Cisco 350 card, DI-624+ router.

I have beaten the board silly and tried just about everything I could find...

My router sees my laptop connected to the AP, my laptop sees my AP.  But I still cant get an IP address via DHCP.

any help would be greatly appreciated.
Bingo

---

### Post by kevdog on 2007-06-10
Do you have any encryption set up in the router??


What happens you type:
ifconfig wlan0 down
ifconfig wlan0 up
dhclient wlan0

Substitute wlan0 if your interface is different (might be eth0 or something else)

---

### Post by Bingo on 2007-06-10
Yes, 64bit Wep HEX

ifdown eth1 drops the interface
ifup eth1 brings it back up
dhclient  eth1

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0f:8f:57:5e:f7
Sending on LPF/eth1/00:0f:8f:57:5e:f7
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS recieved 
No working leases in persistent database - sleeping


forgive me, but I have to type all that by hand...so I may flub some stuff...

---

### Post by Mr. C. on 2007-06-10
"Seeing" a wireless device is different than being associated.  Is your wireless card associated to the AP?

The failure to receive a dynamic address is often due to not being associated to the AP. 

This concerns me: "wifi0: unknown hardware address type 801".

This also concerns me: "DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8"
You appear to have eth1 (a wired Ethernet device) also enabled and active.

MrC

---

### Post by Bingo on 2007-06-10
With this card in this machine I have had both eth1 and wifi0 showing wireless extensions...I have seen this with othes and they always say to configure eth1, I have been doing both...either way my AP shows me as connected and see below for the iwconfig return. 

thanks in advance for all help.

I have the following return from iwconfig

```


lo no wireless extensions

irda0 no wireless extentions

eth1 IEEE 802.11-DS  ESSID:"mywirelessnetwork"
        Mode:Managed  Frequency:2.442 GHz  Access Point 00:40:05:24:F2:D3
       Bit Rate:11 Mb/s Tx-Power=20 dBm Sensitivity=0/65535
       Retry limit:16 RTS thr:off Fragment thr:off
       Power Managment:off
       Link Quality=100/100  Signal level=-36 dBm Noise level=-86 dBm
       Rx invalid nwid;112052  Rx invalid crypt:1197  Rx invalid frag:0
      Tx excessive retries:2  Invalid misc:511889  Missed Beacon:0

wifi0 IEEE 802.11-DS  ESSID:"mywirelessnetwork"
        Mode:Managed  Frequency:2.442 GHz  Access Point 00:40:05:24:F2:D3
       Bit Rate:11 Mb/s Tx-Power=20 dBm Sensitivity=0/65535
       Retry limit:16 RTS thr:off Fragment thr:off
       Power Managment:off
       Link Quality=100/100  Signal level=-36 dBm Noise level=-86 dBm
       Rx invalid nwid;112052  Rx invalid crypt:1197  Rx invalid frag:0
      Tx excessive retries:2  Invalid misc:511889  Missed Beacon:0


```

---

### Post by Bingo on 2007-06-11
System was also showing the wrong channel, I fixed that in my interface file.  Not sure if that helps at all.

Thanks
Bingo

---

### Post by Bingo on 2007-06-11
Somebody...has to have have the 350 working.

Why is this so hard?

---

### Post by kevdog on 2007-06-11
What does your /etc/network/interfaces, and /etc/iftab files say.  You shouldnt have two wireless interfaces.

---

### Post by Bingo on 2007-06-11
etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-essid funkzilla317
wireless-channel 7
wireless-key 0000000000

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface wifi0 inet dhcp
wireless-essid funkzilla317
wireless-channel 7
wireless-key [1] 0000000000


auto wifi0

iface eth0 inet dhcp



auto eth0

```

/etc/iftab
```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:10:a4:78:1d:58 arp 1
eth1 mac 00:0f:8f:57:5e:f7 arp 1

```

I thank all for any assistance, this is the one hurdle I have to getting this thing happy...everything else is so cool, I just cant work with it without wireless.

I see others with this card are having similar issues, someone has to have a fix.

thanks a ton in advance,
Bingo

---

### Post by Bingo on 2007-06-12
I am seriously losing hope...dont make me go back to windoze...

I have a Cisco 340 card, but it exhibits the exact same behavior.

---

### Post by kevdog on 2007-06-12
Sorry Im not familar with your card, however did you have to install drivers for your card, and if you did, what method did you install the drivers?

Why do you have duplicate entries of wifi and eth1 in your interfaces file??

Did someone instruct you to set it up like this??

---

### Post by Bingo on 2007-06-12
No drivers need they are included in the distro.  The Cisco 350 is suppose to work out of the box...heard that before...using the Airo drivers.

From everything I have read/tried, the eth1 and wifi0 just show up...I have seen folks say to ignore it and others say to set them both up the same.

I am at the end of my rope.

I thank you in advance for any insight.
Bingo

---

### Post by Bugrit on 2007-08-18
I nearly went mad with this one also, turned out a clue from from [COLOR="Blue"][PRGSDW]("http://ubuntuforums.org/showthread.php?t=398144&highlight=Network-Manager")[/COLOR] solved it for me.
Everthing seemed to be working, but no DHCP request would be satisfied.
Everything looked like it should work.
Finally I took the advice from the aforementioned post and removed the network manager using 
**sudo apt-get remove network-manager**
I rebooted and it was all working happily!
Sad loss of about 4 hours of my life trying all the other options tho :(

Thanks to all the posters.
My setup..an old IBM Thinkpad T30 using the Cisco Aironet 350 series wireless mini-PCI adapter.
Ubuntu Desktop 7.04.

Buggy

---

