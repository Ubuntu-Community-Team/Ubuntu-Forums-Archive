---
title: "RFC1483 Bridged"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by gionnico on 2007-09-05
I've installed my Conexant AccessRunner USB ADSL Modem's firmware and it works and links to the ISP.

Now I have to establish a "data link" ... with ppp.

I don't know how: it's PPPoA .. but sometimes i read PPPoE ... 

PS: My ISP also requires LLCSNAP (so, not VC)

---

### Post by gionnico on 2007-09-05
I've solved it: googling I've found that only "91" persons in the world use my configuration ( :p )

(startup script for every USB ADSL Modem - firmware must be working and loaded)
```

#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684
count=0
while [[ $((count++)) -lt 40 ]]
do
sync=$(dmesg | grep 'ADSL line: up')
if [ ! -z "$sync" ]
then
br2684ctl -b -c 0 -e 0 -a 0.35
sleep 3
ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
sleep 10
pppd call pppoe
exit 0
fi
sleep 1
done

```

---

