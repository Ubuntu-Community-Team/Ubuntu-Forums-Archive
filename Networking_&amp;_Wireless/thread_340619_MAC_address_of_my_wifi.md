---
title: "MAC address of my wifi"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by dimothy10 on 2007-01-17
Hi guys and girls,
basically am fairly new to ubuntu and linux but have been bashing through a few books and web sites to get to grips with the thing.  unfortunately try as i might i cannot work out how to find out the mac address of my wifi card.  lots of sites tell me how to change it but i only want to know it!  its been driving me nuts.  i may be very stupid and for that i apologise but all your help will be greatly appreciated.

cheers

---

### Post by JamieC on 2007-01-17
Do you know the name if your interface? If so, open a new terminal and type the following (replacing <device> with the name of your interface):
```

ifconfig <device> | grep "HWaddr"

```

This will display a line similar to the following:
> 
<device>     Link encap:Ethernet  HWaddr 00:00:00:00:00:00


I hope that helps.

---

### Post by dimothy10 on 2007-01-17
Thanks very much.  worked a charm!

is there any chance you could explain, briefly as i dont want to take up too much time, what the command consists of?  I understand the pipeline idea and as far as i am aware iwconfig is similar to ipconfig from windows?  just trying to forward my knowledge of what is proving to be quite a tricky but rewarding experience!

---

