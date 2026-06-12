---
title: "RaLink Doesn't connect to wireless"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by Antexter on 2008-01-19
I have a RaLink wireless PCIMCIA card, I've added the MAC etc to the router.
But when I go to connect it will not go past 28% "activation stage: configuring device"

iwconfig
> ra0       RT61 Wireless  ESSID:"xxxxxxxxxxxx"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: xxxxxxxxxxxxx
          Bit Rate=5.5 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=40/100  Signal level:-85 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig
> ra0       Link encap:Ethernet  HWaddr xxxxxxxxxxxx
          inet6 addr: fe80::20e:2eff:fedf:45fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1603 errors:325 dropped:0 overruns:0 frame:0
          TX packets:1557 errors:1 dropped:1 overruns:0 carrier:0
          collisions:4 txqueuelen:1000
          RX bytes:224398 (219.1 KiB)  TX bytes:1048 (1.0 KiB)
          Interrupt:11

Please help thanks.

Edit: I'm running kubuntu 7.04

---

### Post by Antexter on 2008-01-20
shamless bump :)

I also made this thread to try and install some drivers but no one's replying to either [http://ubuntuforums.org/showthread.php?p=4167932](http://ubuntuforums.org/showthread.php?p=4167932)

---

### Post by kevdog on 2008-01-20
What drivers are you using?

lshw -C network

---

### Post by Antexter on 2008-01-20
Thanks for the help :D, here is the output.
>  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@02:00.0
       logical name: ra0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:24000000-24007fff irq:11


---

### Post by kevdog on 2008-01-20
Ok, you got a couple of choices

#1- Your current choice -- DO NOT RECOMMEND -- use Feisty's built in rt 61 drivers
#2 - Compile and install the serial monkey cvs rt61 drivers
#3 - Ndiswrapper + windows xp rt61 drivers
#4 - Update to Hardy's developing kernel (in the how-to section) and use the rt2x00 driver.

Anyone one except #1 will work.  Just depends how adventurous you feel.

---

### Post by Antexter on 2008-01-20
I shall try updating then, been thinking about it for a while was unsure though but I will to get the card working.

---

### Post by Antexter on 2008-01-20
Sorry, would it be possible for someone to provide me with a link to upgrading I cannot find it.

Thanks.

Found it [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

### Post by Antexter on 2008-01-20
I try doing iwlist scan here the output

iwlist wlan0 scan
Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

and a bunch of AP's after that, I still cannot connect with it though, I upgraded the kernel to hardy, and installed serial monkey.

Any ideas, I don't have a windows box to get the drivers for ndiswrapper.

---

### Post by kevdog on 2008-01-20
Ok for right now, dont worry about the warnings.

If you see the access points with the iwlist scan statement -- no problem -- thats a good sign.

Just try to connect via the command line to an unencrypted access point for now.  
The instructions are in my signature.

---

### Post by Antexter on 2008-01-21
i don't have any unencrypted networks around :(.

---

### Post by kevdog on 2008-01-21
Ok, then skip that step, do you have WEP or WPA networks?

---

### Post by Antexter on 2008-01-21
WEP only encryption the router supports, I really have to convince them to ungrade!

---

### Post by Antexter on 2008-01-21
I have read through your post done everything on WEP network thing and here is the final part of the output.

> No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'm pritty sure I filled it in all correctly.

---

