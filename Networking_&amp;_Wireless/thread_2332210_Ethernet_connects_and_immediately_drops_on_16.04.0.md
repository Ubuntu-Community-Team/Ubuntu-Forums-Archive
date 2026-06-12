---
title: "Ethernet connects and immediately drops on 16.04.01 LTS"
date: 2016-07-29
forum: Networking &amp; Wireless
---

### Post by jon114 on 2016-07-29
Have just installed 16.04.01 LTS on my HP Pavillion HPE desktop.
It has ethernet on board and was working fine with Win10.
After installation I can use wifi without problem but the ethernet connects and then drops after about a second. The symbol in the top right shows that it is connected at 100Mbps but checking with the router shows that it isn't really connected.
I have also tried installing a pci ethernet card (killer xeno) and reinstalling but that wasn't detected, it powers up and detects the cable plugged in but thats it.
Any advice and help please?
Thanks
Jon

---

### Post by praseodym on 2016-07-29
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
route -n
cat /etc/resolv.conf
```
MAC-Filter in your router is deactivated?

---

