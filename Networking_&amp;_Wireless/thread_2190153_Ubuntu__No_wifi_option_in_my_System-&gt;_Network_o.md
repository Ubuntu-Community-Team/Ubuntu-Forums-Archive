---
title: "Ubuntu : No wifi option in my System-&gt; Network option"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by prakash_prasad on 2013-11-26
[TABLE]
[TR]
[TD="class: votecell"]              
[/TD]
              [TD="class: postcell"]                I have an Ubuntu 12.04 LTS box but in System->Network  option I do not see WIFI option. I am trying to make us of Ralink WIFI  dongle but not sure how to use it?
  # lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 004 Device 002: ID 13ee:0001 MosArt 


# iwconfig 
lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
      

[/TD]
[/TR]
[/TABLE]

---

### Post by rackit on 2013-11-26
You need to install a driver perhaps. Here is a good thread for your specific device: [http://is.gd/V3HEQy](http://is.gd/V3HEQy)

---

