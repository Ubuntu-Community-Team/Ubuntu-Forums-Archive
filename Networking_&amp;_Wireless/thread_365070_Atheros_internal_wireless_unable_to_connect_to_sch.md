---
title: "Atheros internal wireless unable to connect to school router"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by marx2k on 2007-02-19
Running:
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

On a HP Compaq NC6000 running Edgy.  I have no problem connecting to my home router with this laptop and the internal Atheros (Im typing and posting this through the wireless router now).

However, when i go to school, I can't seem to connect to their router at all (This wasnt a problem on a seperate laptop running Edgy and using a Belkin wireless B card.)

Here are the stats for the internal wireless capabilities:
```

[17182278.096000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17182278.096000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17182278.096000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17182278.096000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17182278.096000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17182278.096000] wifi0: mac 5.6 phy 4.1 5ghz radio 1.7 2ghz radio 2.3
[17182278.096000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17182278.096000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17182278.096000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17182278.096000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17182278.096000] wifi0: Use hw queue 8 for CAB traffic
[17182278.096000] wifi0: Use hw queue 9 for beacons
[17182278.100000] wifi0: Atheros 5212: mem=0x90080000, irq=11

```

The laptop sees the router no problem, on multiple cell access points:
```

ath0      Scan completed :
          Cell 01 - Address: 00:E0:63:50:A9:7A
                    ESSID:"truax wireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:01:F4:EC:FE:93
                    ESSID:"truax wireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:E0:63:81:D4:F3
                    ESSID:"truax wireless"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

```

However, I get the dreaded No DHCPOFFERS issue...
```

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:20:95:2e:b3
Sending on   LPF/ath0/00:0f:20:95:2e:b3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

It seems like everything is set up correctly in iwconfig:
```

ath0      IEEE 802.11Ta  ESSID:"truax wireless"  
          Mode:Managed  Frequency:5.76 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
          Rx invalid nwid:192  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

(not sure what 802.11Ta is, but that changes with every scan from Ta to b to g...)

I mean, the lappy definately sees the access points:
```

ath0      Peers/Access-Points in range:
    00:E0:63:50:A9:7A : Quality=11/94  Signal level=-84 dBm  Noise level=-95 dBm
    00:01:F4:EC:FE:93 : Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
    00:E0:63:81:D4:F3 : Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm

```

A little more info, if necessary:
```

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 20
  ath0: 0003   33.  194.  161.     289      0      0      0      0        0

```

Does anyone have any tips as to how to proceed? Im going to go to the computer lab there and see whats up but Im going to guess that when I tell them Im on a linux box, they will turn and run like their Product-ID key was on fire.

---

### Post by ctsdownloads on 2007-02-19
I had a similar problem with hotel wifi, posted and posted, no one apparently ever goes away from home with their notebooks...lol

For me, I was able to make it happen with the installation of [networkmanager-gnome]("https://help.ubuntu.com/community/WifiDocs/NetworkManager").
Assuming it sees your card alright (I have had issues with some), then you should be able to connect. If that does not work, you could also try wifi radar, although I have never had it working.

---

### Post by marx2k on 2007-02-19
Welll, this program works great at home (which wasnt a problem in the first place) but does not work @ school.

I'm wondering if it has anything to do with the many 'Rx invalid nwid' I am seeing (2087 at current count).  

:confused: 

Overall, i don't think linux wireless connectivity is that difficult. It's pretty straightforward and can be set up many different ways.  I'm pretty certain I have it set up the way it is supposed to be set up as the only difference between home and school is the "Mode" of the AP at school is "Master" (and of course it has multiple AP Addresses with the same ESSID)

Beyond that, it doesn't employ any sort of WEP/WAP encryption and is an open system that SHOULD be giving anyone who requests one, an IP.  

It worked fine with a PCMCIA wireless B card that I put into a laptop.  Just not having much luck with the internal wireless networking chip in this other laptop.  

I will talk to the 'linux lab guy' at school when he is in and see what's going on.  Im going to guess he will suggest an added external PCMCIA card

---

### Post by elamericano on 2007-02-25
What program are you using to connect? Since it's an open network, you should just bring up your device and try to connect manually by setting the SSID and running dhcpd after that. That would rule out a driver incompatibility. If you have to, you can try a newer driver from madwifi.org.

Do you know how to do any of this? Sorry it's so general, but it's really unclear what you've tried so far.

---

