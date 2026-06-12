---
title: "wifi woes"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by strang3r on 2008-01-25
my usb wifi adapter was working and all of the sudden some debconf poped up and because i typed the wrong things i got no wifi how do i get it back so i can fix what i typed

---

### Post by pytheas22 on 2008-01-25
what is the output of

```
iwconfig
```

---

### Post by strang3r on 2008-01-25
sorry to cause panic but i solved the problem (i think) (-u-);;

---

### Post by strang3r on 2008-01-25
yeah i thought wrong 
code:
zadesktop@zadesktop:~$ iwonconfig
bash: iwonconfig: command not found
zadesktop@zadesktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zadesktop@zadesktop:~$

---

### Post by strang3r on 2008-01-25
halp!

---

### Post by pytheas22 on 2008-02-07
sorry I didn't see your post for a while.  It looks from that output like everything should be ok.  Type

```
sudo ifconfig wlan0 up
```

in a terminal and you should be able to connect using Network Manager.

---

