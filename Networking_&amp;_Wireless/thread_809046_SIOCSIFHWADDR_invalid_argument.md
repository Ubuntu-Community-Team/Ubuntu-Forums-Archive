---
title: "SIOCSIFHWADDR: invalid argument"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by macogw on 2008-05-27
sudo ifconfig wlan0 hw addr 00:xx:xx:xx:xx:xx
(xx's are all sets of 2 hex digits)
After running that to set a different MAC address on my wireless, I get:
SIOCSIFHWADDR: invalid argument

Google shows lots of people getting that error, but no solutions :(  Any ideas?

I'm using an IPW3945 with the iwl3945 driver on Hardy.

---

### Post by dmizer on 2008-05-27
looks like incorrect syntax
```
sudo ifconfig eth0 hw [COLOR="Red"]ether[/COLOR] 00:a0:WH:AT:EV:ER
```

other possibilities could include:
- invalid mac address
- hardware
- your driver doesn't support mac address changes.

---

### Post by macogw on 2008-05-27
er...yeah, i had the "ether" in when i ran it...just not when I typed it in on here

so intel's new wifi driver is mac-addr-change-less? :(

---

### Post by dmizer on 2008-05-27
so it seems.  could be worthy of a bug report.

---

### Post by u`F`o on 2010-03-10
> **macogw said:**
> sudo ifconfig wlan0 hw addr 00:xx:xx:xx:xx:xx
(xx's are all sets of 2 hex digits)
After running that to set a different MAC address on my wireless, I get:
SIOCSIFHWADDR: invalid argument

Google shows lots of people getting that error, but no solutions :(  Any ideas?

I'm using an IPW3945 with the iwl3945 driver on Hardy.

Sorry for the two year later answer, but I had the same problem and I solved it with "macchanger" ;) Hope thats useful for someone :)

---

### Post by kerso on 2011-11-18
Hello guys, I guess i know the problem and solution. 
You guys are trying to change MAC address of virtual wireless adapter. Actually the error is expected because you cannot change it, you should change the pyhsical one. Let's try that way step by step and putting your own info. You can use macchanger for this instruction.

*destroy your virtual adapter.*
wlanconfig **ath0** destroy 

*put pyhsical to down*
ifconfig **wifi0** down

macchanger **wifi0** -m <new MAC address>

let's recreate virtual adapter

wlanconfig **ath0** create wlandev **wifi0**

make your configuration with ifconfig and iwconfig, and look with ifconfig ath0, as you see you changed your MAC successfuly.
See you guys.

---

