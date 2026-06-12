---
title: "Trouble connecting to a wireless network"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by Turtlewind on 2005-11-09
Hi,

I'm having real trouble connecting to a wireless network. It's not a problem with the network, as it works fine with Windows machines.

I'm using a Dell Inspiron 2200n with a TP-Link TL-WN510G PCMCIA card. This card is listed as compatible on madwifi.org .

When I go into Network Settings (System > Administration > Networking) I can see my wireless card as **ath0**. When I go into Properties, the wireless network shows up in the list (as "NETGEAR"). However, when I say 'activate' it shows "Activating interface 'ath0'" for a long time (a minute?) and although after this it says the interface is active, I am not able to connect to anywhere.


I think the problem comes when it is looking for a DHCP server, as running dhconfig gives:

```

 sit0: unknown hardware address type 776
 sit0: unknown hardware address type 776
 Listening on LPF/ath0/00:0a:eb:a6:ab:7d
 Sending on   LPF/ath0/00:0a:eb:a6:ab:7d
 Sending on   Socket/fallback
 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
 No DHCPOFFERS received.
 No working leases in persistent database - sleeping.

```


I have no idea what sit0 is.


When I run iwconfig, I get:

```

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```



and the relevant part of ifconfig is:

```

ath0      Link encap:Ethernet  HWaddr 00:0A:EB:A6:AB:7D
          inet6 addr: fe80::20a:ebff:fea6:ab7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:7130 dropped:0 overruns:0 frame:7130
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:e0420000-e0430000

```



[B]UPDATE:[B]

dmesg shows:

```
ath0: no IPv6 routers present
```

for every time I try to connect. I thought for a second that this might mean the problem was related to ignoring IPv4 routers, but robotgeek on the IRC channel tells me this is not the case.

---

### Post by Elling on 2005-11-09
Are you running WPA or WEP on your access point?

---

### Post by almahtar on 2005-11-09
I'm having this identical problem.  I'm using an HP ZV6000 notebook, running the AMD64 breezy.

My card is a Broadcom 4306, and I'm using the 64bit netbc564.inf, and ndiswrapper 1.5.

ifconfig wlan0 up shows no error messages.
ifconfig shows wlan0, shows no ip address for it, and all the packet counts are zero except for
one about transmit retries exceeded, and that is "1," and then rx_fail_misc is a number usually in the hundreds that gradually grows.

I'm going to try editing my /etc/ndiswrapper/netbc564/*.conf and set Radiowhatever to 0, since I heard ndiswrapper commonly disables the radio for broadcom cards accidentally.

iwlist wlan0 scanner produces a great list of networks

In addition to what the first poster said (sorry, forgot your name), when I change the settings in the gui network admin tool and hit submit, it does just what he says (delaying... saying it is active), but when I type iwconfig from the root console none of the changes from the gui tool have stuck.  For example, if I change ESSID in the gui tool, it's still unchanged when I run iwconfig

I get the same dmesg output as the first guy... the same everything.  By the look of the first guy's ifconfig output the errors that my drivers are reporting as rx_misc or whatever are what his is reporting as "frame."

Last of all I forgot to say, for the 2nd guy: I've tried on networks with no encryption and networks with WEP.

---

