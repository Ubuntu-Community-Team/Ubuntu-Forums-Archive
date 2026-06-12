---
title: "slow wireless with 3945ABG"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by tacojohn on 2006-11-28
I have been experiencing very slow times with my wireless card.  It is an intel proset wireless 3945ABG.  Output from iwconfig is

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:A2:66:6F   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-55 dBm  Noise level=-55 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:475   Missed beacon:0

sit0      no wireless extensions.


Please help and let me know if you need more information.
ps how do I disable smilies?

---

### Post by wjp.reg on 2006-11-28
Not sure what you think you should be getting in the way of performance, but this is my output from **iwconfig**:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:4A:14:8E   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=81/100  Signal level=-53 dBm  Noise level=-54 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:611   Missed beacon:0

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```
I'm running the same 3945ABG in my Lenovo 3000 N-100 laptop

---

### Post by tacojohn on 2006-11-28
it takes nearly one minute to load any webpage, and I don't have the problem under windows.  For instance msn.com just took 100 seconds to load using firefox with fasterfox installed.

---

### Post by tacojohn on 2006-11-29
Anybody know how to fix this, it sometimes works fine and sometimes is slow.

---

### Post by trubblemaker on 2006-11-29
yeah checkout google for disabling ipv6 in firefox, *should* speed things up.

a really overhanded way of crushing ipv6
```

sudo echo "blacklist ipv6" | sudo tee -a /etc/modprobe.d/blacklist
sudo reboot

```

---

### Post by pillu on 2006-11-30
I had troubles with my dlink router too. Disabling IPv6 in ubuntu and in firefox really helped to bump up the speed. To disable it in firefox you just need to type about:config in the address bar and search for IPv6 and then make the boolean variable true for the search result.

For disabling it in ubuntu you need to change some lines in /etc/modprobe.d/aliases file. Just google for some really good guides out there.

---

### Post by trubblemaker on 2006-12-01
the aliases file doesn't work to disable it in Edgy, don't know why just know it didn't work for me.  Thanks for posting the firefox way, I'll write that down so I stop forgetting.

---

