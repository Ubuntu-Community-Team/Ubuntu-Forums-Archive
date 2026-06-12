---
title: "Cannot use wireless after installing Ibex 8.10"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by tugh on 2008-11-02
I looked at all the threads and couldn't find anything that helps my case. 

I'd been using 7.10 and installed 8.10 and now i cannot connect to wireless. I can see and select my wireless network next to the volume button but when I enter my wireless password, it cannot connect and keeps asking back. 

Also, if I let it keep trying to connect, it freezes the laptop completely after a minute or two. I'm pretty sure about my password and this used to work under 7.10. i think, this was also a problem under 8.04 but i had to go back to 7.10 because of some other issues so didn't pay much attention by then.

When I ifconfig, it shows ath0, eth0, lo, and wifi0-00.

When I do "dmesg reports", there are lines like:

eth0: Realtek RTL8139 at 0x9000, ... IRQ 3
eth0: Identified 8139 chip type 'RTL-8100B/8139D'
...
eth0: link down
...
ADDRCONF(NETDEV_UP):ath0: link is not ready
ADDRCONF(NETDEV_UP):ath0: link becomes ready
ath0: no IPv6 routers present

This is a Sony Viao PCG-K27 laptop. I've already checked to make sure that the manual wi-fi switch is on.

I would appreciate any help to resolve this problem.

---

### Post by gewitty on 2008-11-02
You and the rest of us Tugh. There seem to be an increasing number of posts about this problem.

---

### Post by tugh on 2008-11-02
Thanks for the warning. I'll go back and check the latest threads again and close this if I see any similar case.

---

### Post by eks on 2008-11-02
When I finally got wifi working again with an Atheros card it was not connecting to my home WEP network. But with unsecured it didn't had any problem.

I was using wicd from a Hardy upgrade, it had WPA supplicant set as madwifi. I simply set it to wext and it connected.

Different hardware, but maybe same software problem?

---

### Post by gewitty on 2008-11-02
You might want to check out this thread on the same topic. I just posted a note referring to a possible problem with the kernel.

[http://ubuntuforums.org/showthread.php?t=966245](http://ubuntuforums.org/showthread.php?t=966245)

---

