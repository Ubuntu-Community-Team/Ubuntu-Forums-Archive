---
title: "Looks good, but no connection - RTL8180L 6.06 Dapper Drake"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by OmahaVike on 2006-07-20
hi all.  hoping someone can help me out with this wierdness...

not using ndiswrapper, but a straight 6.06 dapper drake install on a RTL8180L chipset.

ifconfig shows:
```
wlan0     Link encap:Ethernet  HWaddr 00:40:F4:B9:A1:E3
          inet addr:192.168.1.214  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:feb9:a1e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:23 overruns:0 frame:0
          TX packets:72 errors:46 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2614 (2.5 KiB)  TX bytes:4853 (4.7 KiB)
          Interrupt:201 Memory:ee916000-ee916100

```

(i did notice that dropped and errors above might raise speculation, but what could it be?!?)

ifconfig shows:
```
wlan0     802.11b linked  ESSID:"hayloft"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:06:25:F8:8F:50
          Bit Rate=11 Mb/s   Sensitivity=80/85
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-41 dBm  Noise level=-251 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

upon first glance, one would suspect incompatability with the driver, yet it's still associating with the AP, which might convince some that it is NOT a driver issue.

i cannot successfully ping the AP, nor anything else on the network!?!?  i've rechecked the WEP key over a dozen times to no avail.

any and all help is GREATLY appreciated.

---

### Post by Titus A Duxass on 2006-07-20
First of I would turn off WEP until you get the card working.
Have you tailored /etc/networking/interfaces?
Have you disabled any other network cards?  If you are only running wireless do this in bios?

What sort of card is it? 

A little more information would help a lot.

---

### Post by OmahaVike on 2006-07-21
> **Titus A Duxass said:**
> First of I would turn off WEP until you get the card working.
Have you tailored /etc/networking/interfaces?
Have you disabled any other network cards?  If you are only running wireless do this in bios?

What sort of card is it? 

A little more information would help a lot.

Thank you for the reply.

It's a Trendnet TEW-228PI (rtl8180l chipset).  I've seen threads where it claims to work natively with a fresh install.  I gave up on that, and am now pursuing the ndiswrapper route, with little success.  Yep, I did follow the exact link found in the ndiswrapper supported card list.

Can't turn off WEP for another week.  Nor can I disable the hardwired NIC card (that's how i'm posting these pleas for sanity)

Tailored interfaces up and down the river.  Currently, here's how it looks...

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.215
netmask 255.255.255.0
gateway 192.168.1.200


iface eth1 inet static
address 192.168.1.216
netmask 255.255.255.0
gateway 192.168.1.200

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet static
address 192.168.1.216
netmask 255.255.255.0
gateway 192.168.1.200
wireless-essid hayloft
wireless-key (key omitted.  no dashes)

auto wlan0

auto eth1

```

all of the wlan0 settings (essid, etc) look correct to match my network.

ifconfig now looks like this:

```
eth1      Link encap:Ethernet  HWaddr 00:30:1B:1D:10:D8
          inet addr:192.168.1.216  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe1d:10d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1126202 (1.0 MiB)  TX bytes:217621 (212.5 KiB)
          Interrupt:185 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:B9:A1:E3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:10 overruns:0 frame:0
          TX packets:572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:18304 (17.8 KiB)
          Interrupt:193 Memory:ee8be000-ee8be100


```

iwconfig looks slightly suspicious:

```
wlan0     802.11b  Mode:Managed  Frequency:2.432 GHz
          Access Point: Not-Associated   Bit Rate=11 Mb/s   Sensitivity=80/85
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=26/100  Signal level=-119 dBm  Noise level=-182 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

no associated, and a poor link quality...   hrmmm...  the AP is sitting literally 4 feet away from the card, direct line of sight, and is a linksys .11b.  strange.

now...   here's where things *really* get dicey.  check out the output for iwlist scan:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:06:25:F8:8F:50
                    ESSID:"hayloft"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality:153  Signal level:0  Noise level:49
                    Extra: Last beacon: 6ms ago

```

signal level is 0, but quality is 153!?!?  huh?

Again, any and all help is thanked by my family, as I am beginning to feel like hurting complete strangers (kidding, but you get the drift).

---

### Post by OmahaVike on 2006-07-21
fought this thing tirelessly, and never got it to work.

ended up switching out the card to use another i had laying around, and worked with no problems.  getnet GW-91263.  added it to the ndiswrapper card list.

thanks for the help, tho.

---

