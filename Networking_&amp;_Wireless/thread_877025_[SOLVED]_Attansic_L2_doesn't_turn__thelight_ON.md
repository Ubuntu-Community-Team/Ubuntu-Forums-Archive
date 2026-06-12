---
title: "[SOLVED] Attansic L2 doesn't turn  thelight ON"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by vinichc on 2008-08-01
Hi,

I buy a asus p5gc-mx motherboard with the attansic L2 network card onboard.
This card works fine in windows XP, but not in the ubuntu.

I try this threads to install:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845&page=9](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845&page=9)
[http://ubuntuforums.org/showthread.php?p=5310139](http://ubuntuforums.org/showthread.php?p=5310139)

First of all, I install ubuntu 8.04, that reconize the card, 
in ifconfig show me the eth0, but i didn't get install the driver.
Then, in same foruns said that L2 works in ubuntu 7.10, then I install ubuntu 7.10 kernel 2.6.22-14.

The driver is correctly installed, i can see eth0 (with ifconfig), lsmod list atl2 and in system properties we see all details of the drive.

Perhaps, simply doesn't work. I can ping the interface but not other computer in the network. 
**And the ligths of the card doesn't turns on**, the wire is OK because works fine in windows.

Someone Can help me????

cheers

PS.: I create this new thread because I thing this is a more generic error than the drive.

---

### Post by vinichc on 2008-08-04
Hi everbody,

Finnaly I have my attansic L2 works in ubuntu.

Basically, I install ubuntu 8.04.1 kernel 2.6.24-19-generic.

Download this drive compiled:
[http://ubuntuforums.org/showthread.php?t=853665&highlight=attansic+l2](http://ubuntuforums.org/showthread.php?t=853665&highlight=attansic+l2)

put this drive in kernel module:
```
sudo cp atl2.ko /lib/modules/2.6.24-19-generic/kernel/drivers/net 
```

This ubuntu version cames with a default atl2 drive, but doesn't  works.

so, remove the older atl2:

```
sudo modprob -r atl2
```

load the newer atl2

```
sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2.ko 
```


This will work, but stop all the times you restart your computer, to run automatically edit /etc/rc.local


```
gksudo gedit /etc/rc.local
```

put this 2 lines above the line  exit 0
```

modprob -r atl2
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2.ko

```

Now you have network all the time you turn on your computer. :)

PS.: This tips is based and compiled by this thread:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845&page=2)

---

