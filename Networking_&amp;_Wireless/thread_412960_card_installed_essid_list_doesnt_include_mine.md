---
title: "card installed? essid list doesnt include mine"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by warmfusion on 2007-04-18
Hia all,

ive had a good look around and have spent many hours trying to get my damn card running.
I have a Belkin f5d7010 3000uk which is detected by ubuntu as needing the ol' rt2500 drivers. thats all good and well, i do an iwlist and get:

```
ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And if i do an "iwlist ra0 scan" i get the following:
```

ra0       Scan completed :
          Cell 01 - Address: 00:11:50:28:8A:BA
                    Mode:Managed
                    ESSID:"Belkin_Pre-N_590344"
                    Encryption key:off
                    Channel:1
                    Quality:0/100  Signal level:-87 dBm  Noise level:-196 dBm


```

Now thats all good and fine, except, MY ap essid is "asgard" and is not more than 10 feet from my feet. I occasionaly get two other aps depending where i sit, but never asgard. 
We're using channel 13 and WEP and its not hidden or anything silly like that. My mates managed to get his wireless running but i'm having weird issues.

I'm totally new to this stuff and im trying my best to work it out, i tried ndiswrapper to use the supplied drivers but no avail. the belkin lights do not even light up atm despite the card being semi-online as its able to scan but never connect to anything.

Has anyone got ANY hints as to what i may be doing wrong?

I'm running Feisty, upgraded from Dapper via edgy last night, hopeing that the "improved wireless support" would solve it, alas no... :(

Many thanks in advance,

Toby

p.s lspic -v gives:
```

03:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Belkin F5D7010 Wireless G Notebook Network Card
        Flags: bus master, slow devsel, latency 64, IRQ 5
        Memory at 38000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

```
and ifconfig gets me:
```

ra0       Link encap:Ethernet  HWaddr 00:11:50:91:4C:EB  
          inet6 addr: fe80::211:50ff:fe91:4ceb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1512760 (1.4 MiB)
          Interrupt:5 Base address:0x4000

```
Hope that helps

---

### Post by spd106 on 2007-04-18
I'm not 100% about this, but some drivers are restricted to particular channels, as in the US you can only use channels 1-11.

So I suggest you move the AP off channel 13.

---

### Post by warmfusion on 2007-04-19
We're in the UK, and that does sound familiar as when i installed the card on windows i needed to run some ancillary utility to get it to lock into 13, I shall investigate moving to channel 11, as i recall its set to 13 to reduce interference from all the fools on default channel 1. :)

---

### Post by spd106 on 2007-04-19
You might be able to alter the country/region in a config file to enable channel 13. I don't have a Ralink card so I can't test it.

See [http://gentoo-wiki.com/HARDWARE_rt2500](http://gentoo-wiki.com/HARDWARE_rt2500)

---

### Post by warmfusion on 2007-04-19
YAY!

There is an awful lot of love for you here.

I had to edit the /etc/Wireless/RT2500STA/RT2500STA.dat file and modify CountryRegion to 2.

2 days battering my brain and you send the link that solves it all, yay for experts.

Thank you once again

Toby

---

