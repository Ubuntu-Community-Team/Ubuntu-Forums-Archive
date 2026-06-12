---
title: "Skype connects but nothing else?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by vckeating on 2009-01-15
Hey all,

I have a problem with my internet connection.  I'm using wicd and got it all set up for my school account - proxies and everything, and it was all happy.  But now when I try to connect to my home wireless connection I have no access to the internet for most programmes.  Wicd will connect fine and assign an IP, etc, but I can't access any information from the internet.

I've removed all the proxies and made 'system-wide' changes, went into each program to make sure the proxy server was off and rebooted after this - still nothing works.  Well, except for Skype, which connects fine for some reason.  But Pidgin, browsers, email, ping, software updates - nothing else.  

Could there be something very simple that I'm missing here?  

Thanks,

- Vincent

---

### Post by hyper_ch on 2009-01-15
what's the output of:

```

iwconfig

```

```

ifconfig

```

```

cat /etc/resolv.conf

```
?

---

### Post by vckeating on 2009-01-15
Sorry, I have to type this out manually since I'm using another computer to access the internet, so I've only included those things about the wireless.  Please let me know if you need others.

```

lo, eth0, wmaster0 - no wireless extensions

wlan0     IEEE 802.11bg  ESSID:"Michrouter"
          Mode:Managed  Frequency: 2.462 Ghz  Access Point: 00:1E:2A:70:56:08
          Bit Rte=48M/s  Tx-Power=27 dBm
          Retry min limit: 7  RTS thr:off  Fragment thr=2353 B
          Power Management:off
          Link Quality=76/100  Signal level=-53 dBm  Noise level=-66 dBm
          Rxinvalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```

```

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a5:67:6a
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mast:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Rx packets:1622 errors:0 dropped:0 overruns:0 frame:0
          Tx packets:2112 errors:0 dropped:0 overruns:0 frame:0
          collisions:0  txqueuelen:1000
          RX bytes:200752 (200.7 KB)  TX bytes:296568 (296.5 KB)

```

```

nameserver 192.168.1.1

```

Cheers!

---

### Post by hyper_ch on 2009-01-15
looks fine to me... hmmmm

---

### Post by vckeating on 2009-01-16
Sorry for the self-bump, but is there anyone else who might have an idea of what's wrong here?

Thanks.

---

### Post by vckeating on 2009-01-16
OK, well, I think I got it working.  I'm not sure if this is the cause of the solution, but I stopped moblock (which never gave me problems before) and all of a sudden I could connect.  Strangely, when I restarted it I still don't have any problems.  

Anyway, there we are.

---

### Post by jre on 2009-01-17
> **vckeating said:**
> I'm not sure if this is the cause of the solution, but I stopped moblock (which never gave me problems before) and all of a sudden I could connect.  Strangely, when I restarted it I still don't have any problems.
If you get problems again and moblock is running, then check your /var/log/moblock.log to see if/which IPs were blocked. Then you can configure moblock-control to allow traffic to these IPs.

---

