---
title: "Internet not working after Intel driver change"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by flyver on 2010-07-13
So I was reading an article about [how to change the Intel driver to get better performance with videos]("http://www.ivankristianto.com/os/ubuntu/install-intel-latest-driver-to-your-ubuntu-10-04/1278/"). As I ("PD") have written in the comments on that page, that made it impossible for me to connect to the internet. My wireless connection is there (I can see it and select it), but nothing happens, I can't get online.

Another computer running 10.04 is able to connect to the internet as well as before.

The problems started after having updated the driver, and I went back to the old driver, but this internet problem is still there.

Thank you!

---

### Post by pytheas22 on 2010-07-13
While anything is possible, it seems very unlikely that those instructions would have broken your Internet connection.  I suspect it's just a coincidence.

If you could please try connecting a few times and then post the output of these commands, however, it should hopefully provide a better idea of why the connection's not working:
```

ifconfig
sudo iwlist scan
lshw -C Network
dmesg | tail -25
```

---

### Post by flyver on 2010-07-13
Here it is:


eth0      Link encap:Ethernet  HWaddr 00:1a:80:b6:c9:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7408 (7.4 KB)  TX bytes:7408 (7.4 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:5d:b5:c3  
          inet6 addr: fe80::21c:bfff:fe5d:b5c3/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:395 (395.0 B)  TX bytes:2793 (2.7 KB) 




lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:22:B0:D4:B2:22 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on 
                    ESSID:"JOHN DOE" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s 
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000004a4be15cac 
                    Extra: Last beacon: 1640ms ago 
                    IE: Unknown: 00174368657A2050617363616C206574204D617269652D4A6F 
                    IE: Unknown: 010882848B960C183048 
                    IE: Unknown: 030101 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32041224606C 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD0900037F01010006FF7F 
                    IE: Unknown: DD0C00037F020101420002A34000 




 *-network               
       description: Ethernet interface 
       product: 88E8039 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 15 
       serial: 00:1a:80:b6:c9:8a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes 
       resources: irq:43 memory:f6000000-f6003fff ioport:2000(size=256) 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 3945ABG [Golan] Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: wlan0 
       version: 02 
       serial: 00:1c:bf:5d:b5:c3 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-6-generic firmware=15.32.2.9 latency=0 multicast=yes wireless=IEEE 802.11abg 
       resources: irq:46 memory:fa000000-fa000fff 





[   17.592463] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9 
[   17.702544] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   18.095667] ppdev: user-space parallel port driver 
[  593.197847] wlan0: deauthenticating from 00:22:b0:d4:b2:22 by local choice (reason=3) 
[  593.200647] wlan0: authenticate with 00:22:b0:d4:b2:22 (try 1) 
[  593.204227] wlan0: authenticated 
[  593.204829] wlan0: associate with 00:22:b0:d4:b2:22 (try 1) 
[  593.208745] wlan0: RX AssocResp from 00:22:b0:d4:b2:22 (capab=0x431 status=0 aid=1) 
[  593.208751] wlan0: associated 
[  593.212274] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[  594.969987] audit_printk_skb: 15 callbacks suppressed 
[  594.970047] type=1400 audit(1279065999.599:17):  operation="getattr" pid=1589 parent=914 profile="/sbin/dhclient3" name="/lib/" pid=1589 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0 
[  594.970114] type=1400 audit(1279065999.609:18):  operation="getattr" pid=1589 parent=914 profile="/sbin/dhclient3" name="/usr/lib/" pid=1589 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0 
[  603.460047] wlan0: no IPv6 routers present 
[  640.640111] wlan0: deauthenticating from 00:22:b0:d4:b2:22 by local choice (reason=3) 
[  640.700136] cfg80211: All devices are disconnected, going to restore regulatory settings 
[  640.700144] cfg80211: Restoring regulatory settings 
[  640.700151] cfg80211: Calling CRDA to update world regulatory domain 
[  640.704007] cfg80211: World regulatory domain updated: 
[  640.704013]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[  640.704020]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  640.704026]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[  640.704032]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[  640.704038]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[  640.704157]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

### Post by pytheas22 on 2010-07-13
From your output, it looks like you were able to connect for a little while (about a minute), and then the connection dropped.  Were you able to access websites in that time?

You might have better luck connecting with wicd, an alternative connection manager that you can install by running the following command while plugged into the Internet (if you don't have a wired connection available, let me know and I'll provide instructions for an offline installation of wicd):
```

sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Note that you need to enter your WPA key in wicd before trying to connect to your network by clicking the "Advanced Settings" tab--wicd doesn't prompt you for the password like NetworkManager would.

---

### Post by flyver on 2010-07-13
Thanks for taking the time to interpret that information!

No, I was not able to connect to the internet during that minute.

If it helps, the network manager applet in the panel keeps showing that it is searching, and after about a minute it stops and shows no connection.

I am able to be online when wired and did what you said. This is the message I get from wicd: "Connection Failed: Unable to Get IP Address"

Hmm...

Thanks again!

---

### Post by pytheas22 on 2010-07-13
That's a bit strange.  If possible, could you disable security on your wireless network temporarily, just so we can see if you're able to connect and hold the connection then?  That will help narrow down the possible sources of the problem.

---

### Post by flyver on 2010-07-14
Now we're getting dangerously close to a situation where I know nothing about what to do... I don't think I know how to do that and I keep thinking it would just be better for me to format my drive and reinstall (yet again).

:?

But thanks for wanting to help!

---

### Post by pytheas22 on 2010-07-14
No problem.  If you end up deciding against reinstalling and want to try troubleshooting the wireless more, let me know.  I can probably help you figure out how to disable encryption on your network.

---

