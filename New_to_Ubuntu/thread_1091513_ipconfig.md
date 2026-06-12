---
title: "ipconfig"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by vagelism on 2009-03-09
hello to all.
When I type the ipconfig command i got this text

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-C9-61-57-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24225 errors:0 dropped:0 overruns:0 frame:13848
          TX packets:729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:2741047 (2.6 MB)  TX bytes:33534 (32.7 KB)
          Interrupt:18 


Why I have this device and also the ath0 device? 
I have only one wireless card on my pc. 
I see that when I connect to a wireless network I only use the ath0 device.
Thank you for your help

---

### Post by mikewhatever on 2009-03-09
What you see with ifconfig is network interfaces, not devices. To see the devices, use <sudo lshw -C network>. ipconfig isn't a valid command.

---

### Post by vagelism on 2009-03-09
> **mikewhatever said:**
> What you see with ifconfig is network interfaces, not devices. To see the devices, use <sudo lshw -C network>. ipconfig isn't a valid command.

And why there are 2 interfaces in one wireless device...?
I mean what is the meaning of this interface , wifi0?
thank you for your time

---

### Post by Nxion on 2009-03-09
wifi0 is the representation of the actual hardware, used for creating APs and ad-hoc stuff. Ath0 is a "frontend" to wifi0 which actually does the connecting to the remote AP.

---

