---
title: "eth(number) changes on every ubuntu startup"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by seizui on 2008-02-27
First time and I am, like many others here, new to Linux [Ubuntu 7.1] and need a little [?] help:(. First I'll explain the history up until to arrival of the problem.
I am dual booting with XP pro on a asus 5pk board. Originally i had just xp, this is still running but on the second hard disk. On installing Ubuntu [on the first hard-disk], it gave the option of copying all documents from XP, very handy. I also presume it copied a lot more too. Because of serious "error" in XP i first attempted to repair it, but without success. I  reinstalled XP, but had to disconnect the 1st Ubuntu hard disk XP installation refuses to see hardware with Linux]. on completion and reconnection of first disk, everything seemed to OK, i.e. choosing an OS at startup. The problem I now have on Ubuntu is that when I want use the internet or use mail, my isp provider gives a message about the mac address already being bound/registered to a DHCP ip address. Then it says I should ask for a new ip address vis DHCP release / discover, a bit of a contradiction if it is already bound, still, not a problem, just re-register with my ISP. and then use the Network tools to reconfigure the eth name/number, currently on eth(32). Configuring to DHCP or roaming in the Network tool does not seem to make any difference. So not a "serious" problem for me, but definitely for the wife and kids. Oh yes, absolutely no problem on XP, So obviously the DHCP release / discover is not necessary.
So, and I come to it, how can keep the eth(number) static and bound to the DHCP address. I unfortunately do not have the option to opt for a static ip address, which would probably work. Any tips from anyone are most welcome, thanks very much in advance;).

---

### Post by spd106 on 2008-02-27
I'm not entirely clear on the situation, but here are few things to try.

The /var/lib/dhcp3/ directory has the current saved leases for each interface. You could edit this so that it tries to use the IP you set next time you log on to the Internet.

You can do a release using dhclient directly (see the man page for more details).
```
sudo dhclient -r 
``` 

You can ensure an interface is given a particular name by defining it in the /etc/iftab file. Though from what I understand the more recent versions of HAL should take care of this automatically. Some people do report interface name change each time they return to Linux from the Windows dual boot partition.

---

### Post by seizui on 2008-02-27
> **spd106 said:**
> I'm not entirely clear on the situation, but here are few things to try.

The /var/lib/dhcp3/ directory has the current saved leases for each interface. You could edit this so that it tries to use the IP you set next time you log on to the Internet.

You can do a release using dhclient directly (see the man page for more details).
```
sudo dhclient -r 
``` 

You can ensure an interface is given a particular name by defining it in the /etc/iftab file. Though from what I understand the more recent versions of HAL should take care of this automatically. Some people do report interface name change each time they return to Linux from the Windows dual boot partition.

Your right spd106, not so clear, but basically reinstalling XP has affected the ubuntu's ability to access the internet even though the mac address of the network card and the ip remained the same

Interesting place /var/lib/dhcp3/ and it is clear that my ip address has been changing due to my own efforts, I've used among other things the sudo dhclient -r already. I have currently 32 leases in this file, cannot delete them, no rights [even though I thought I had] I shall focus here, thanks for the tip and I will let everyone know how I resolve this issue.

---

### Post by seizui on 2008-02-27
Oh yes spd106 I forgot to ask, any reason why I do not have a /etc/iftab folder?

---

### Post by seizui on 2008-02-27
Oh yes /etc/iftab file!  I think I am off to bed

---

