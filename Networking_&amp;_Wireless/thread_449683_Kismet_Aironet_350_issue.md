---
title: "Kismet Aironet 350 issue"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by chr3681 on 2007-05-20
Ok, so I'm trying to run kismet on my laptop. I have everything installed and since I know the internal broadcom wireless chip won't work, I'm using a Cisco Aironet350 card. I edited the kismet.conf to look like this for the source:

source=cisco_wifix,eth2:wifi0,ciscosource

but when I try to run kismet I get this error:

FATAL: Unable to open cisco control file '/proc/driver/aironet/eth2/Config' 2:No such file or directory

Any ideas on how to fix this? My cisco card works fine as far as connectivity, and I would love to get it working with Kismet.

Thanks for the help!

---

### Post by chili555 on 2007-05-20
May we please see iwconfig?

---

### Post by tturrisi on 2007-05-20
You may also have to put the card into monitor mode prior to running ksimet.

---

### Post by chr3681 on 2007-05-21
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11-DS  ESSID:"ATHENS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: ***   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/100  Signal level=-66 dBm  Noise level=-85 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2971   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"ATHENS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: ***  
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/100  Signal level=-66 dBm  Noise level=-85 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2971   Missed beacon:0

When I run Kismet it states that it is putting the code into monitor mode, so I'm not sure I have to do that manually. If I do how would I go about that?

---

### Post by tturrisi on 2007-05-21
try:
iwlist eth2 mode monitor

---

### Post by chili555 on 2007-05-21
Is eth2 your built-in Broadcom and wifi0 your Aironet?

---

### Post by chr3681 on 2007-05-21
No i have blacklisted my Broadcom to make things easier, so I'm pretty sure both refer to the Aironet

> try:
iwlist eth2 mode monitor

when I do that all it gives me are options for iwlist usage:

$ iwlist eth2 mode monitor
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

---

### Post by tturrisi on 2007-05-21
sorry...
iwconfig eth2 mode monitor

---

### Post by chr3681 on 2007-05-21
Ok i did iwconfig eth2 mode monitor with no errors. Still I get the same error, and even after that command it still shows mode as being "managed" when I do iwconfig??

---

