---
title: "Broadcom BCM4313: Wireless connected but no internet access"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by adimarat on 2013-12-16
**&#8203;**After upgrading to Ubuntu 13.10 from 13.04 my wireless card connects to the router, the router is connected to internet (I am sure about that) but still no internet access for my laptop.
I am using [U]Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter.

[/U]iwconfig gives me

```
root@asteras:~# iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:"asteras"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 80:1F:02:8D:4E:8C   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

rfkill list all gives me
```
root@asteras:~# rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

I forgot to add that I have the wl proprietary driver installed and when I tried brmcsmac it didn't work at all, I couldn't even connect to a wireless network.

Could anybody help please??

---

### Post by adimarat on 2013-12-17
I post here the solution if someone else has the same problem: I saw that this problem doesn't exist in other wireless connections except my home one. The problem was in the band mode. There must be something going wrong with the N mode, so I just selected B and G modes. Thank you.

---

### Post by awambawamb on 2013-12-17
I am in your same situation, but I haven't tried other wifis yet. can I solve the problem without changing my router's setup?
Thanks!

---

