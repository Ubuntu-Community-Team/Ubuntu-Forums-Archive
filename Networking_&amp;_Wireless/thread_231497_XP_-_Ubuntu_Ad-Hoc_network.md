---
title: "XP - Ubuntu Ad-Hoc network"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by i++ on 2006-08-07
hi all, 

I have a PC with windows and a broadband connection which i would like to share, ad-hoc, with my ubuntu laptop. ndiswrapper etc is working on the laptop, and i've shared the internet connection on the PC, and set up an ad-hoc network. but the laptop can't seem to connect? how can I browse for networks?

sorry for being a noob!

i++

---

### Post by gruffy-06 on 2006-08-07
I've had some problems connecting wirelessly to ad-hoc networks too because the default operation mode is set to "Managed".

Changing the operating mode to "Ad-Hoc" requires console action. Open a terminal and enter:
[I]
sudo iwconfig ath0 mode Ad-Hoc[/I]

where "ath0" is the name of your network adapter. Enter your password if necessary. Run *iwconfig* to ensure ad-hoc mode is set.

To access networks in range, click Desktop on the top panel, point to Administration, then select Networking. A list of detected network devices will appear. Click on the relevant wireless device you configured with iwconfig then click Properties. Enter the ESSID (Network Name), key type (plain or hex) and the WEP key. WPA is not supported. Leave DHCP as it is, then click OK. It should take some time to connect. After that, click OK to close the window.

Finally, open Firefox or your favourite browser, then type in a valid url. If you see a web page, congrats! You're online!

If you still experience problems, then reply back. I'm happy to help. :-)

---

### Post by sandor.dornbush on 2006-08-14
I am trying to set up an ad-hoc network with kubuntu. I am using a dell inspiron and I want it to connect to a XP machine.  I have got the wireless (rt2570) set up.  It works fine in infrastucture mode.  I have configured the device for ad-hoc networking.  I put the following in the /etc/network/interface file:
```

auto rausb0
iface rausb0 inet static
address 192.168.2.1
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-essid streetsmart
wireless-channel 6

```

I think that the dhcp is wrong, but I don't know how to say use static ip.  The keywork static is refused.  When this is used iwconfig prints this:
```

rausb0    Link encap:Ethernet  HWaddr 00:0D:0B:9F:71:83
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:bff:fe9f:7183/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4171708 (3.9 MiB)  TX bytes:179034 (174.8 KiB)

```

When I try to connect to this network from the XP machine I do see the network.  However I cannot get them to ping each other or otherwise talk.  Anybody know what I am doing wrong?  Anybody know of a straightforward Ubuntu ad-hoc guide?

thanks in advance.

---

