---
title: "Wireless problem internet extremly slow"
date: 2020-09-28
forum: Networking &amp; Wireless
---

### Post by jeyvi on 2020-09-28
I'm really new in ubuntu and i since i've been working i was so happy, but after 1 week working i noticed that my internet drop to .5 - 1 mb i tought it was the company but nope, everything is fine and i checked on my cellphone and in windows and i having 30mb/s conection i've tried everythin i've found on internet but nothing seems help, i'll attached some commands and their outputs


I'm using ubuntu 20.4, i've tried changing to 18 LTS and fedora o xubuntu, but i get the same problem:C

uname -r
```
5.4.0-48-generic
```

lshw -C network

```
WARNING: you should run this program as super-user.
  *-network                 
       description: Wireless interface
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 31
       serial: 58:00:e3:77:17:93
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.4.0-48-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=192.168.0.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:130 memory:b1000000-b11fffff
```

lspci | grep Network
 ```
02:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)
```

iwconfig
```
enp3s0f1  no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"IZZI-4F07"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 70:4F:B8:FD:65:1B   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:80   Missed beacon:0

lo        no wireless extensions.
enp3s0f1  no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"IZZI-4F07"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 70:4F:B8:FD:65:1B   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:80   Missed beacon:0

lo        no wireless extensions.
```


Please somebody help me i have to take classes from college.

---

### Post by morrownr on 2020-09-29
I read through your info and the thing that stands out to me is:

[I]Link Quality=25/70 Signal level=-85 dBm
[/I]
That signal level isn't going to do much for you. Is this a laptop with internal antenna? Where is your router/gateway relative to your wifi device? I'm looking for things that might cause a poor wifi signal... walls? Does it get better if you move your system closer to the router?

---

### Post by jeyvi on 2020-09-29
Yes it only get a good speed if i stay close but literally beside it, i was working for almost a week and sudenly it starts to fail, the weird part is ... the wifi on windows is working 10/10 :C, and yeah i'm in my room that si just one room away from the router... :(

---

### Post by morrownr on 2020-09-29
I see your power management is on. Check this out:

[https://askubuntu.com/questions/1230525/ubuntu-20-04-network-performance-extremely-slow](https://askubuntu.com/questions/1230525/ubuntu-20-04-network-performance-extremely-slow)

---

