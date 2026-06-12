---
title: "Intel 2100 3B wireless help needed"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Undertwotimes on 2007-05-15
Ok, to preface, I just upgraded my Girl Friends lap top, then she moved out of state for the summer.  When she got to her new apartment, her damned wireless card now does not work after upgrading to Feisty.  I managed to get her to give me an ssh tunnel, so here is what I know:

It will scan:

```

         Cell 03 - Address: 00:18:4D:55:05:B8
                    ESSID:"noodle"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Quality:79  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 16ms ago
          Cell 04 - Address: 00:13:49:89:BF:15
                    ESSID:"salsa"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:62  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 284ms ago

```

Notice that on every scanned network, the Signal and Noise levels are 0.

```

joe@blackbox:~$ sudo lshw -C network
  *-network:0
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 04
       serial: 00:0c:f1:12:e6:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated

```

ifconfig && iwconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:0C:F1:12:E6:63
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 Memory:c0204000-c0204fff

eth0      unassociated  ESSID:"noodle"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:7261-6D75-6B61-6B61-0000-0000-00   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Please help me, before I'm shamed forever.  Fyi, I've tried manually setting the shiz with iwconfig etc.](*,)

---

### Post by chili555 on 2007-05-15
I think your encryption key is wrong. See all those zeroes in the key? I think *iwconfig* is expecting one of the following:

# 40 or 64 bit ASCII WEP code has 5 characters
# 40 or 64 bit HEX WEP code has 10 characters
# 128 bit ASCII WEP code has 13 characters
# 128 bit HEX WEP code has 26 characters 

It looks to me, unless your key actually has a bunch of zeroes, in the router, that you have input 16 characters, which doesn't match anything. 

Please recheck the key.

---

### Post by Undertwotimes on 2007-05-15
Ahh yes, that could be it, I will take a look tonight.  The problem is that my gf's roomates claim they don't remember the login to the router, so it may be difficult to confirm.  Thank you for that observation.

---

### Post by chili555 on 2007-05-15
A great many routers use 'admin', sometimes as the user name and some as the password, with the other being blank. With the make and model, you should be able to Google it.

---

### Post by deva on 2007-05-16
I'm also having trouble getting this wireless device to work on 7.04.
(p.s. I'm completely noob.) It seems to be picking up the hardware, but I can't get it to work. I'm pretty sure we're using WPA security on our wireless and i can't see anywhere to put in the WPA key.

any help would be much appreciated. :)

---

### Post by Undertwotimes on 2007-05-17
Fixed!  It turns out that it was a WPA key, and there was some problem with the upgrade process and the new network manager applet thing was not showing up correctly.  I followed (roughly) the link bellow and got it working.  I removed all the configuration from /etc/network/interfaces except lo, and then added the file /etc/default/wpasupplicant and added ENABLED=0 to it.  Then I rebooted, and blammo, a new network thingy popped up in the toolbar.

The key was to use the new Network Manager widget (left click which brings out the drop down menu listing the available wireless connections).  

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

