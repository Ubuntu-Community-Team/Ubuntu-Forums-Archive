---
title: "Slow speeds over wifi on fresh install of 18.04"
date: 2019-07-06
forum: Networking &amp; Wireless
---

### Post by nrung95 on 2019-07-06
I'm noticing severe speed issues when connecting via wifi on a fresh install of 18.04. My smartphone gets about 200Mbps when I do a speed test, but my laptop gets only 50Mbps max. The wireless card is "Intel Corporation Centrino Wireless-N 135 (rev c4)". I've tried disabling power management, disabling ipv6, upgrading my kernel to the latest patch version, then latest version. I've even tried downloading the driver from here and loading it into /lib/firmware/ and restarting. Does anyone have any idea what can be causing this speed decrease? 

```

&#9654; iwconfig
lo        no wireless extensions.

wlp5s0    IEEE 802.11  ESSID:"TheInternet"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: B0:39:56:XX:XX:XX   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:81   Missed beacon:0

enp3s0    no wireless extensions.


```

Let me know if there's any other diagnostic command to run.

---

### Post by Autodave on 2019-07-06
Make and model of your laptop?

Who is your service provider for the internet?

---

### Post by nrung95 on 2019-07-06
> **Autodave said:**
> Make and model of your laptop?

Who is your service provider for the internet?

ISP: RCN, but it seems to happen everywhere. I run the same speedtest using the same wifi AP on my phone and I'll get 151Mbps using some bar's wifi.
Brand: MSI 
Model: MS-16GA

---

