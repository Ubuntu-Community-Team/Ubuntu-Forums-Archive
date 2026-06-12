---
title: "How do I edit network startup scripts?"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2007-03-01
Yeah so I have a Wired Ethernet problem that can only be solved by using these commands.  But the effects are only temporary, every reboot I do requires typing in those commands again if NIC doesn't find Internet.
```
sudo dhclient eth0
sudo route add default gw 192.168.0.1
```

Since I'm a lazy person I made a BASH script named netfix to execute the same commands as above but with just one word.  Still that is not a permanent DHCP solution to my problem, I still have to go in terminal and type to fix DHCP if NIC doesn't find Internet.

So I'm wondering how can I add this script to the network startup scripts?
Where is this so called network startup script?

---

### Post by jingo811 on 2007-03-07
bump 1.  Still need some tips on automizing those two commands on reboot.

---

