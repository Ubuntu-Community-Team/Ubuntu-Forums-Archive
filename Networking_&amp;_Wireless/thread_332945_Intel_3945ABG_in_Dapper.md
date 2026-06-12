---
title: "Intel 3945ABG in Dapper"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by kleo32 on 2007-01-06
I've been unable to get my Intel wireless 3945ABG to work. I understand there are many other threads in this forum about the same issue. I have gone through almost all of the threads, but to no avail.

Any help would be much appreciated. Some info which may of assistance :

The drivers are there...
```

lsmod | grep 'ipw3945'
ipw3945               126620  1
ieee80211              37064  1 ipw3945

```

It isn't detecting the hardware I presume..
```

iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.
eth1      radio off  ESSID:off/any
          Mode:Managed  Frequency:nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:off
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1010   Missed beacon:0
sit0      no wireless extensions.
ppp0      no wireless extensions.

```

and...

```

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:15:C5:B4:70:20
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

eth1      Link encap:Ethernet  HWaddr 00:18:DE:0D:26:82
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17512 errors:0 dropped:1010 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x6000 Memory:dfcff000-dfcfffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:82.2.81.63  P-t-P:62.253.189.143  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:49513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:69628465 (66.4 MiB)  TX bytes:2475245 (2.3 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

Thanks...

---

### Post by n00b@linux on 2007-01-07
You have to configure your eth1 connection using iwconfig in order to associate it with an access point (ie. ´connect´).  You didn´t state if you are using WEP or not.  This DOES make a difference as the ´key´ in iwconfig is for WEP.  You need to use wpa_supplicant if you´re using WPA. - there is a sticky by wieman01 on this forum (or just click on the link in my sig) and read it.

---

### Post by kleo32 on 2007-01-07
Thank You n00b@linux.

Now posting wirelessly from ubuntu.. :D   My router was indeed using WPA1. I checked the sticky and followed the instructions to successfully setup the wireless connection.

Just one hinderance though, I have to restart my networking everytime I logon by 

```

sudo /etc/init.d/networking restart

```

Its hardly a problem !!

Thanks,

---

### Post by n00b@linux on 2007-01-07
> **kleo32 said:**
> Just one hinderance though, I have to restart my networking everytime I logon by sudo /etc/init.d/networking restartIsn't there something on that in the thread on my sig/sticky?  Something about creating a script called wireless-network.sh?  (My memory fails me).

---

### Post by kleo32 on 2007-01-07
Thanks once again n00b@linux.

I was following the sticky on the forum ([http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)) rather than the one in your sig. The one I referred doesn't contain info about the startup script though.

Setup the script and succesfully connected to the network on reboot.

Thanks...

---

### Post by n00b@linux on 2007-01-07
Great!  Thank you for notifying me of the difference between the sticky and the thread.  I'll bear that in mind next time I offer advice.  Cheers.

---

