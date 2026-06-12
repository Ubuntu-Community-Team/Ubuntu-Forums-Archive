---
title: "can't get wireless internet"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by rastaband on 2007-07-15
I just got ubuntu, and am trying to set up the wireless internet, but am yet to successfully establish a connection. I tried manually inserting the IP address and server, and I also tried using the roaming mode and connecting to the server, but when I do, it shows the bars, but no signal strength, and I cannot connect to any sites(but when I use the Windows OS on the same computer, it has perfect connection, and I am able to access the internet.)
Also, when I connect it directly to the router, using an ethernet cable, it works fine.

Does anyone think they know how to help?
PS. if it helps, I am using a linksys router for the connection

---

### Post by ugm6hr on 2007-07-15
Start with the following in Terminal:
```
lspci
ifconfig
iwconfig
```

In lspci - you are looking for Network / Ethernet Controller (assuming it is an internal wifi card).

Reply with the output of these, and you'll be half way to finding the problem..

---

### Post by pompeyjohn on 2007-07-15
I have  exactly the same problem; here is my output...

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-21 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

output of lspci

```
projector@paris:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```

ifconfig

```
projector@paris:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:B0:13:9A  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:feb0:139a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:550406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:607646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43546270 (41.5 MiB)  TX bytes:362804618 (345.9 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1855 (1.8 KiB)  TX bytes:1855 (1.8 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:A8:C5:E7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1424 (1.3 KiB)  TX bytes:2907289 (2.7 MiB)
          Interrupt:21 Base address:0xc000 
```

thanks in advance :)

---

### Post by pompeyjohn on 2007-07-15
somebody ... anybody? please help as I really need to have this sorted tonight... thanks

---

### Post by pompeyjohn on 2007-07-15
linux  gods, I throw myself at your feet, I beseech you; for the love of all that is good and proper, please please take pity upon me,... and help!

---

### Post by ukripper on 2007-07-15
> **pompeyjohn said:**
> linux  gods, I throw myself at your feet, I beseech you; for the love of all that is good and proper, please please take pity upon me,... and help!

try wlassistant, it is a kde app which will detect available networks and then you can configure your essid once it is detected.

```
sudo apt-get install wlassistant 
```

you can run it from terminal if you are runing gnome environment

just type ```
sudo wlassistant
``` when you want to connect

---

### Post by jokerjens on 2007-07-15
I also had some problems with wireless internet. I turned off all security on my router, then it worked. Afterwards I turned security back on and it still worked. (I changed the password so that it didn't contain special danish characters, I don't know if this was the cause of the problem)

Anyway if you haven't already tried to turn off security it might be worth a shot to simplify things.

---

### Post by ugm6hr on 2007-07-15
> **pompeyjohn said:**
> linux  gods, I throw myself at your feet, I beseech you; for the love of all that is good and proper, please please take pity upon me,... and help!

This might help:
[http://ubuntuforums.org/showthread.php?t=241565](http://ubuntuforums.org/showthread.php?t=241565)

If not - try searching for rt2500 (your wifi chipset).

---

### Post by psamp14 on 2007-07-15
i just got ubuntu linux as well....i am on a home built pc and dual booting windows xp/ubuntu linux

i typed in the lpsci -v command and it does recognize my wireless card, but it says no wireless extensions

i have no idea what to do....

---

### Post by psamp14 on 2007-07-15
update: i dont know what i did, but i see now that its detecting a nearby wireless connection, linksys, at 31%

but when i open up firefox the webpage doesnt load at all....

how do i get wireless internet, even if its to this linksys connection?

---

### Post by MyR on 2007-07-15
this link should help for the rt2500
[http://www.lockergnome.com/nexus/linux/2007/06/12/ralink-help-for-ubuntu-feisty/](http://www.lockergnome.com/nexus/linux/2007/06/12/ralink-help-for-ubuntu-feisty/)
peace

---

### Post by MyR on 2007-07-15
> **psamp14 said:**
> i typed in the lpsci -v command and it does recognize my wireless card, but it says no wireless extensions
you may need to install drivers
this link might help
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
peace

---

### Post by psamp14 on 2007-07-16
i dont see my wireless card on that list...i have a texas instruments card and its not on the list

---

### Post by MyR on 2007-07-16
> **psamp14 said:**
> i dont see my wireless card on that list...i have a texas instruments card and its not on the list
can you post the relevant output of the lspci? (your wifi card maker and chipset)

---

