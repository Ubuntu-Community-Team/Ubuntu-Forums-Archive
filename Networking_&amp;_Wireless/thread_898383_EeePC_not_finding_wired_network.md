---
title: "EeePC not finding wired network"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by Pacey on 2008-08-23
Hey guys,

Just installed Ubuntu 8.04 out of the box and it doesn't find my ethernet card. It is not even listed in /etc/network/interfaces. I know there is an issue with the wireless support, but I haven't heard people mention this one. Any help would be greatly appreciated.

---

### Post by Rhubarb on 2008-08-23
People are experiencing this same issue.
The solution from what I've read is to take the battery out, and put it back in.
I don't have an eeePC myself, so I can't say exactly.
I read it somewhere in the eeeuser.com's forum (under how to get ubuntu 8.04 installed on an eeePC)
[http://www.eeeuser.com/](http://www.eeeuser.com/)
I'm a bit vague on the specifics of it all, so you may benefit from looking for the fix yourself.
Post back here your solution if / when you find it so that others may benefit too.

---

### Post by zekica on 2008-08-23
If it is an eeepc with Atheros L2 wired card (for example eeepc 701), you need to download a new driver (ubuntu 8.04 ships with an older version):
[http://people.redhat.com/csnook/atl2/atl2-2.0.5.tar.bz2](http://people.redhat.com/csnook/atl2/atl2-2.0.5.tar.bz2)

You can then transfer it to eeepc with an usb stick, extract it and compile it:
(if we assume that the file is copied on Desktop, you can open a termial and):
```
tar -xjf Desktop/atl2-2.0.5.tar.bz2
cd atl2-2.0.5/
make
``` (this will compile the driver)

You then have to move an ubuntu shipped version of atl2 driver:
```
sudo mv /lib/modules/`uname -r`/ubuntu/net/atl2/atl2.ko /lib/modules/`uname -r`/ubuntu/net/atl2/atl2.ko.old
```
and copy new driver (assuming that you are still in atl2-2.0.5 folder:
```
sudo cp atl2.ko /lib/modules/`uname -r`/
depmod -a
```
and then restarting.

---

### Post by fkrogh on 2011-05-08
> **Rhubarb said:**
> People are experiencing this same issue.
The solution from what I've read is to take the battery out, and put it back in.
I don't have an eeePC myself, so I can't say exactly.
I read it somewhere in the eeeuser.com's forum (under how to get ubuntu 8.04 installed on an eeePC)
[http://www.eeeuser.com/](http://www.eeeuser.com/)
I'm a bit vague on the specifics of it all, so you may benefit from looking for the fix yourself.
Post back here your solution if / when you find it so that others may benefit too.

Worked for me!!! How do people discover these things??!  Thanks,
Fred

---

