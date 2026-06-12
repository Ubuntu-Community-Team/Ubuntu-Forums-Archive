---
title: "wireless connection problem"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by guy_incognito on 2005-11-07
hi all

I am completely new to linux(installed yesterday) and have been using guides to try and get internet going. Currently I have to reboot into windows to get information so this is a slow process for me.

I searched all through this forum and tried lots of the advice but I think I am missing something obvious.

I have a bt voyager 1040 pci wireless netwrok card and a bt voyager 2100 router. The card uses the broadcom chipset. After some while I got ndiswrapper to work, and installed the drivers. Hardware found, drivers found. It appears as wlan0 in networking.I took off all security on the router, and entered all the information but it just won't connect to the internet.

Using Ubuntu Breezy Badger 5.10

From reading I figure you may need this info

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

and

ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:319531 (312.0 KiB)  TX bytes:319531 (312.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:F5:0B:BD:82
          inet6 addr: fe80::211:f5ff:fe0b:bd82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:f3020000-f3021fff


screen of connection in networking
[http://img.photobucket.com/albums/v446/captvonbek/netset1.jpg](http://img.photobucket.com/albums/v446/captvonbek/netset1.jpg)

settings
[http://img.photobucket.com/albums/v446/captvonbek/netset2.jpg](http://img.photobucket.com/albums/v446/captvonbek/netset2.jpg)

The router is DHCP, no firewall. I can't ping i.p addresses or url's, nor the router itself. Network not available etc.

I am using ndiswrapper 1.1 as I was assured this chipset works with that version(and I had a guide for that one)

Any ideas would be great. Would using another distribution help? I would rather use Ubuntu and work through the issue, as I would probably learn more.

Thanks

---

### Post by shinygerbil on 2005-11-07
If you know the name (ESSID) of the wireless network and the WEP key (if you have one), you can try (in Konsole):

```
sudo iwconfig wlan0 essid {name of network}
sudo iwconfig wlan0 key {security key}
sudo dhclient wlan0
```

If that works, you're in business :)

However, you don't want to have to do that every time you start up, so you can add it to /etc/network/interfaces, but I forget off the top of my head the actual commands...

Steve

---

### Post by Maverick911 on 2005-11-07
After looking at your screenshots I see that in your Network settings the Default _g_ateway device is blank. This needs to be set to wlan0. Also you will not be able to connect as long as iwconfig reports ESSID as off/any. You should see your AP essid here.
Try:
```
iwconfig wlan0 essid analogy
```

Then:
```
iwconfig wlan0
```

This is what you need to see:
```

wlan0 IEEE 802.11g ESSID:"analogy"
Mode:Managed Frequency:2.462 GHz Access Point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:14 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Management off
Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

Hope this helped. I'm still trying to get mine working reliably, but it does work...(sometimes)

---

### Post by guy_incognito on 2005-11-08
ok, I ran iwconfig wlan0 essid analogy, put in my password.

but I iwconfig straight away and it still says essid "off/any"

Any reason why this is not working? SOme form of permissions, or incorrect version it can't manage?

---

### Post by guy_incognito on 2005-11-08
quick update.

I got it working, although I probably cheated :)

I actually bought an edimax wireless card and it worked straight out.

For anyone in the UK, dabs sell it for £15+3p&p. Its a ralink2500 chipset, so no ndiswrapper.

I probably should have worked through the issue, but I just wanted internet working :)

---

