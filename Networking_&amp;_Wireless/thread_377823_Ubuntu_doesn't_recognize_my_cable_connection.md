---
title: "Ubuntu doesn't recognize my cable connection"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by renatasr85 on 2007-03-06
Hi there!
I access the internet through a cable connection and it works just fine, most of the time. I had no problem configuring it - in fact, I didn't have to configure it at all. Ubuntu did all the work.
The problem is that my cablemodem (an old Terayon TJ110) usually takes two minutes to communicate with my cable provider after I turn it on. Till the communication is established, I obviously have no internet access. Ubuntu usually loads faster than two minutes, so I end up starting my Ubuntu session without a cable connection already activated.
During this first session, Ubuntu won't recognize my active cable connection, **even after all the leds are on and the connection is fully established**. I try to disable the eth0 and then enable it again, but it's useless. My only choice is to reboot the PC, which is really annoying (on a daily basis), but it does the trick.

Is there any way to solve this little inconvenient?

---

### Post by lloyd_b on 2007-03-06
Next time, try opening up a terminal window, and running the command
```
sudo /etc/init.d/networking restart
```

What's probably happening is that your computer is configured for DHCP (which automatically provides IP address, nameserver, and other information), but with the cable modem being offline, it isn't able to obtain this info.

Disabling and then re-enabling the interface may not cause the DHCP process to be performed (it depends on exactly how your disabling/enabling it).  Running the above command will cause the DHCP process to be performed.

Lloyd B.

---

### Post by renatasr85 on 2007-03-06
Thanks a lot, Lloyd. I'll try that. :)

---

