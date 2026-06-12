---
title: "Strange issue.. no network connectivity when auto-powering on, but ok when reboot"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by steve457 on 2007-07-19
I'm having a strange issue when my pc starts from a power failure (auto power-on set in the bios).  When this happens, for some reason I do not have a network connection.  I am also unable to even ping my router.  If I then do a reboot, the network connection comes back correctly.  I checked the route table, and also looked did an ifconfig -a, and am unable to distinguish any differences from when the connection works or does not work.  Also, doing an ifdown/up does not fix the problem when the connection is not working.  The only way to solve the issue seems to be a soft reboot.  Any ideas?

---

### Post by steve457 on 2007-07-19
Did a little more research and discovered the following.  Instead of booting off of the hard drive, I used the Ubuntu Fiesty live CD.   Booting from the CD the network connection was established fine, regardless of whether or not it was a hard or soft reboot.  When I mean hard reboot, I mean physically unplugging the computer and then plugging it back in and having it automatically turn on.

Ok, so I figured with that test out of the way that I would again try booting from the hard drive.  Well, same problem.  When doing a hard reboot (unplugging) my network connection does not work.  Since I am using a static IP address it appears that the connection is working, but I am unable to even ping my router.  If I turn off computer and then turn it back on, without unplugging it, then the network connection comes up fine.  This is really weird!!!  

Checking dmesg, I was able to find a difference when the connection was working and when it was not.

Working:
```
[   21.137833] sky2 eth0: addr 00:1b:fc:58:93:c2
[   21.138046] sky2 eth1: addr 00:1b:fc:58:89:68
[   21.184803] sky2 eth0: enabling interface
[   21.186605] sky2 eth0: ram buffer 48K
[   21.205576] sky2 eth1: enabling interface
[   21.208501] sky2 eth1: ram buffer 0K
[   22.890296] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control both
[   33.263259] bridge-eth1: enabling the bridge
[   33.263474] bridge-eth1: up
[   33.263655] bridge-eth1: already up
[   33.263856] bridge-eth1: attached

```

Not working:
```
[   12.939546] sky2 eth0: addr 00:1b:fc:58:93:c2
[   12.939679] sky2 eth1: addr 00:1b:fc:58:89:68
[   12.954948] sky2 eth1: enabling interface
[   12.958620] sky2 eth1: phy write timeout
[   12.960082] sky2 eth1: phy write timeout
[   12.961541] sky2 eth1: phy write timeout
[   12.963002] sky2 eth1: phy write timeout
[   12.964462] sky2 eth1: phy write timeout
[   12.965924] sky2 eth1: phy write timeout
[   12.967385] sky2 eth1: phy write timeout
[   12.968845] sky2 eth1: phy write timeout
[   12.970308] sky2 eth1: phy write timeout
[   12.971769] sky2 eth1: phy write timeout
[   12.973229] sky2 eth1: phy write timeout
[   12.974690] sky2 eth1: phy write timeout
[   12.976150] sky2 eth1: phy write timeout
[   12.977610] sky2 eth1: phy write timeout
[   12.977673] sky2 eth1: ram buffer 1020K
[   12.991225] sky2 eth0: enabling interface
[   12.993025] sky2 eth0: ram buffer 48K
[   26.298928] bridge-eth1: enabling the bridge
[   26.299004] bridge-eth1: up
[   26.299026] bridge-eth1: already up
[   26.299117] bridge-eth1: attached

```

I guess the question is, what is causing the phy write timeout??  This totally has me stumped.  I'm almost about to install Windows Server 2003 onto the computer..  please help!

I've also attached the full dmesg, and lspci output.  Any pointers or advice would be greatly appreciated.

---

### Post by bren on 2007-07-20
steve,

by no means an expert but....

does this command get your network up after a hard reboot?

> sudo /etc/init.d/networking restart

if it does then it is pretty easy to add this to start up (sys-admin-startup) as a oneline script (you will have to make executable).

easy to describe above in more detail if you need

cheers
bren

---

### Post by steve457 on 2007-07-20
Bren,

Unfortunately, no.  That command does not bring the network up.  I also tried doing an ifdown/up with no such luck either.

BUT...  I think I finally found the solution!   

I'm using an Asus P5K-WS motherboard (Intel P35 chipset), and I just flashed the system BIOS to the latest version.  On the Asus website it said the version was the intial release, yet my motherboard had a version that was 2 months older.  In any case, after the reflash the computer works great!  Very odd.. but I'm happy.  Ubuntu gets to stay on the system after all (not that I really would switch.. ).

-steve

---

