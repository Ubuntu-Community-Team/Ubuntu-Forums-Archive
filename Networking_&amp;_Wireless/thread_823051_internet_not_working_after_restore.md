---
title: "internet not working after restore"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by stldirty on 2008-06-08
i just restored my system from a backup and now my internet isn't working.  i can see the wireless networks but it won't connect.  i can't connect via my ethernet port either.  any help would be greatly appreciated.

im using hardy heron btw and have an hp dv6000

---

### Post by superprash2003 on 2008-06-08
please post your iwconfig output from the terminal

---

### Post by stldirty on 2008-06-08
```
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

eth0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by superprash2003 on 2008-06-09
do you find any restricted drivers under sytem->administration->restricted drivers (or hardware drivers) ?

---

