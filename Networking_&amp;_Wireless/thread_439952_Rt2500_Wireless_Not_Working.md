---
title: "Rt2500 Wireless Not Working"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by TheoMurpse on 2007-05-11
I'm running Feisty.

I have a rt2500 driver running. I used the exact same driver previously within Gentoo. The LiveCD of previous versions of Ubuntu have provided me with working wireless on this laptop (I don't know about the new one since it won't boot up). However, invariably, after installing the LiveCD to the hard drive, BAM no wireless.

When I go into network settings, the Wireless connection is there. I have ESSID input properly, and for now I'm running an open router, so I have no WEP password typed in. I receive IPs via DHCP with this router.

However, I don't have a connection. Occasionally, when I enable the connection, my computer begins to seriously lag. Other times, it doesn't.

ifconfig ra0:
Link encap:Ethernet HWaddr 00:0C;76:CA:C1:D3
inet6 addr: blahblah Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets 0 errors:0 dropped:0 overruns:0 frame:0
TX packets (same)
collisions:0 txqueuelen:1000
RX and TX bytes are both 0
Interrupt:11 Base address:0x4000

iwconfig ra0:
RT2500 Wireless ESSID:""
Mode:Managed Frequency=2.412GHz Bit Rate:11 Mb/s Tx-Power:-2 dBm

RTS thr:off Fragment thr:off
Link Quality=0/100 Signal level=-120 dBm Noise level: -192 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I find this odd since I've configured the ESSID in Network Configuration.

iwconfig ra0 essid theo:
nothing changes. The ESSID still remains "".

dhclient ra0:
long list of DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval [this number changes]
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

What gives? I'd love to make the switch to Ubuntu, but I cannot without wireless.

---

### Post by eiapoce on 2007-05-11
Nope, same card tried evertything. Check my posts.

Enrico

---

### Post by Spartan.II.117 on 2007-05-18
i am having a similar issue with the nova tech card i just bought, i installed it and the computer recognizes it as a ralink card, and it sees networks but none of them are accesible, they show up as having zero percent strength, and it is connected to two very strong antennas, so i dont know what is going on.

---

### Post by Lylepalooza on 2007-05-18
HI there,
If it is a RT2500 chipset card (if it is that similar to the above post) then there has been a reported issue of having to "down" the card, enter the essid and then "up" the card. I will look for the bug report and try send it, though it is elsewhere on this forum.

For now, go to terminal and type:

dmesg | grep rt2500

If nothing comes up, it is not the rt2500 driver, and you can rule that problem out.

I'll do a bit of research and see what driver it is.

---

### Post by Lylepalooza on 2007-05-18
Do you know what model number the wireless adapter is?

If you go here: (a list of wireless cards supported by Ubuntu)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
I can only find one Nova Tech card, a USB adapter, which seems to have a bug.

You can read more on the bug here:
[https://launchpad.net/ubuntu/+bug/61797](https://launchpad.net/ubuntu/+bug/61797)
It has a fix in older versions of Ubuntu. Unfortunately, it doesn't sound like it is related to your problem.

If the above is your card, it sounds like your driver may be rt2570.
The serial monkey group provides information on this driver if that is the case, their website is:
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page#Latest%20News](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page#Latest%20News)

You might have more luck searching there.

What do you get if you go to terminal and type:

dmesg | grep rt2570

?

---

### Post by AirRaven on 2007-05-18
I've run across a simple solution for the problem that works with my RT2500. It's a bit of an ugly hack, but it works- and to top it all, you don't even have to fuss around with WiCd or the like.

All you'll need is a LiveCD of a previous version of Ubuntu- I used my old Edgy install CD, but I assume a Dapper Install LiveCD would do just as well so long as it fully supports the RT2500- even a Breezy LiveCD, if you're feeling particularly archiac. 

All that you need to do is start up, boot into the LiveCD OS, and then set up your network card via the standard System->Administration->Networking method using the old network-admin tool. 

Now you'll need to mount your Feisty Partition to be accessible from the LiveCD. In my case, it's hdb1, so I used the following command:

```
sudo mount /dev/hdb1 /mnt/feisty
```

Once this has been done, you'll need to open up Nautilus with Root access. 
```
gksudo nautilus
```

Now, navigate to /mnt/feisty/etc/network, and delete the contents of that folder. Replace the contents of the folder with the contents of /etc/network in your LiveCD's file system. 

Then replace /mnt/feisty/etc/resolv.conf with /etc/resolv.conf.

Reboot, and your Feisty Networking should be fully functional- or at least it is for me. I'd advise against touching the Feisty Network configuration tools- I've not touched them yet, and I'm not particularly keen on watching them mangle the working configuration tools.

Like I said- it's not a particularly graceful solution. But it works.

---

### Post by TheoMurpse on 2007-05-19
My thread seems to have been hijacked by people with other problems. Is there someone around who can address this problem? AirRaven, I'd prefer not to use your solution if I can avoid it, but thanks. I'm hoping someone can provide a solution that doesn't involve preventing me from using Feisty software.

Edit: And I'm definitely an rt2500 card with rt2500 driver: dmesg | grep rt2500 gives
[  28.788000] rt2500 1.1.0 BETA4 2006/06/18 [http://blahblah](http://blahblah)
[  30.296000] rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
[  30.296000] rt2500 EEPROM: 8 8 8 8 9 9 10 10 10 10 10 10 10 10 dBm Maximum

[  47.508000] [<dc9e5a50>] (RTMPIsr+0x0/0x150 [rt2500])
[1407.872000] rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
[1407.872000] rt2500 EEPROM: 8 8 8 8 9 9 10 10 10 10 10 10 10 10 dBm Maximum

---

### Post by Spartan.II.117 on 2007-05-21
sorry about that, i thought it was the same problem, i'll start my own thread.

---

### Post by TheoMurpse on 2007-06-01
I installed Xubuntu and now it works.

---

