---
title: "Intel Wireless AC 7260 cannot enter 802.11ac mode"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by hong2 on 2014-08-11
Hey guys,

I'm trying to use Intel Wireless AC 7260 card to do some experiments in 802.11ac standard, but with the latest firmware(version 22.24.8.0), the card is now showing as 802.11abgn mode instead of AC. 

I have this 7260 card and an ASUS USB-AC56 card in my laptop, and after I type iwconfig, it looks like below:

```

wlan1     IEEE 802.11abgn  ESSID:"Linksys_CSI_5GHz"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: 94:10:3E:05:F0:08   
          Bit Rate=216 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:47   Missed beacon:0

wlan2     IEEE 802.11AC  ESSID:"Linksys_CSI_5GHz"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.805 GHz  Access Point: 94:10:3E:05:F0:08   
          Bit Rate:174 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=76/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

As you can see, the ASUS card is working as 802.11AC, while the intel 7260 is working as 802.11abgn.

Does anyone know how to resolve this problem and put Intel 7260 to 802.11AC mode? 

Thank you very much for your time!

---

### Post by hong2 on 2014-08-12
Any thoughts?

---

### Post by chili555 on 2014-08-12
You may find this thread helpful: [http://ubuntuforums.org/showthread.php?t=2178873](http://ubuntuforums.org/showthread.php?t=2178873)

---

### Post by hong2 on 2014-08-14
Thanks for your reply and the pointer. 

I actually have tried several combinations of firmware and Kernel version, but I still cannot get it right. 

Now my kernel version is 3.16.0, and I've tried iwlwifi-7260-7.ucode,  iwlwifi-7260-8.ucode, and iwlwifi-7260-9.ucode, I still cannot enter 802.11ac mode. The outcome of iwconfig still shows it as 802.11abgn, while my ASUS card shows 802.11AC.

I've tried many methods in related threads, and I've seen your replies a lot, you seems to be an expert on this chip. Any help is really appreciated!!!

Thank,
Hong

---

### Post by Charlie_Hedlin on 2014-10-01
I'm running Kernel 3.14.14-031414-generic with firmware version 25.222.9.0.  I am getting great speeds, reporting 780 mbps (if I remember correctly, I tested last night) and network transfers over 300 mbps. However iwconfig still shows 802.11abgn, so I would ignore that part, as there is no way I was on 802.11n.

---

