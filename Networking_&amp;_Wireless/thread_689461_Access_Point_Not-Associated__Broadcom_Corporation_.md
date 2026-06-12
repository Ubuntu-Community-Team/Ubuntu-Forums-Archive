---
title: "Access Point: Not-Associated / Broadcom Corporation BCM4318"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by neburzaragoza on 2008-02-06
Hi, I just changed from Dapper to Gibbon, and I'm having troubles with my wireless conexion. The system seem to recognize the nets, but it's impossible to get connected.

this is my wireless card: 
```

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

This could be helpful:
```
iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  Nickname:"Jazztel Wireless"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

I don't know what a Access Point: Not-Associated is, but it seems the problem comes from there.

any suggestion or idea?

thank you all

---

### Post by faulkes on 2008-02-06
> **neburzaragoza said:**
> Hi, I just changed from Dapper to Gibbon, and I'm having troubles with my wireless conexion. The system seem to recognize the nets, but it's impossible to get connected.

this is my wireless card: 
```

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

This could be helpful:
```
iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  Nickname:"Jazztel Wireless"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

I don't know what a Access Point: Not-Associated is, but it seems the problem comes from there.

any suggestion or idea?

thank you all

Try first to see what wireless networks exist using:

```

sudo iwlist eth1 scan

```

If you are not automatically pickup up / associating with an AP, there are a number of posible reasons.  The first thing I would try is to manually associate with it by setting the ESSID via:

```

sudo iwconfig eth1 essid <the essid of the AP you want to connect to>

```

Also, are you running WEP or WPA on the network?

Faulkes

---

### Post by neburzaragoza on 2008-02-06
```
xxx@xxx-laptop:~$ sudo iwconfig eth1 essid "Jaztel Wireless"
xxx@xxx-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Jaztel Wireless"  Nickname:"Jazztel Wireless"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=24 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

it seems like now the access point is associated, but invalid

---

### Post by neburzaragoza on 2008-02-06
ok, everything has changed. I restarted and now my Access Point is linked, but the wireless is not working yet.

```
rumbaruben@rumbaruben-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Jazztel Wireless"  Nickname:"Jazztel Wireless"
          Mode:Managed  Frequency=2.472 GHz  Access Point: 00:03:C9:E5:EA:78   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=66/100  Signal level=-46 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:13836  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

uhmmmm!!

---

### Post by faulkes on 2008-02-06
> **neburzaragoza said:**
> ok, everything has changed. I restarted and now my Access Point is linked, but the wireless is not working yet.

```

eth1      IEEE 802.11b/g  ESSID:"Jazztel Wireless"  Nickname:"Jazztel Wireless"
          Mode:Managed  Frequency=2.472 GHz  Access Point: 00:03:C9:E5:EA:78   
          Rx invalid nwid:0  Rx invalid crypt:13836  Rx invalid frag:0

```



Note the "invalid crypt: 13836" message, which would seem to indicate that either the laptop or the AP is expecting WEP/WPA to exist (IMO).

Faulkes

---

### Post by rustybronco on 2008-02-06
> **neburzaragoza said:**
> 
          Bit Rate:54 Mb/s   Tx-Power:25 dBm    
          
> **neburzaragoza said:**
> 
 Bit Rate=24 Mb/s   Tx-Power=19 dBm 

> **neburzaragoza said:**
> ok, everything has changed. I restarted and now my Access Point is linked, but the wireless is not working yet.

          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          
uhmmmm!!
Your bit rate is dropping and at 1mb/s it ain't going to be to very fast.
try DarkNOOB's guide [http://ubuntuforums.org/showpost.php?p=2431305&postcount=1](http://ubuntuforums.org/showpost.php?p=2431305&postcount=1)

***edit*** fresh install or an upgrade ? the reason I ask is, if it was the upgrade path you could try to connect while running a live cd and see if it works.
[http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)

---

