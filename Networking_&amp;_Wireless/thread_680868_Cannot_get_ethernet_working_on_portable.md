---
title: "Cannot get ethernet working on portable"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by Mike_Gerard on 2008-01-28
Portable HP Compaq 6820s, built-in wireless and ethernet interface, came with Vista Business.
Ubuntu 7.10 installed, no serious problems (well, actually there were, relating to the installation not liking free space between the Vista Business boot partition and two other HP primary partitions, but that is another story).
The ethernet connection goes onto a Zyxel 4-port wireless router.
I cannot get any ethernet connectivity over the wired connection. The wireless does actually see a network, but that is my neighbour's and is unavailable.
I have tried DHCP (which is how Vista works, with no problems) and also a manual configuration (192.168.1.x, subnet 255.255.255.0, gateway 192.168.1.1) without any change. I have also used sudo to down and up the interface (eth0 : eth1 seems to be the wireless i/f).
ifconfig shows all packets going out on the local loopback.
I do remember that, during the installation, there was a failed attempt to access a site for updates (security.ubuntu.com, I think).
The ubuntu CD-ROM system seems fine: run on my XP system, it happily accesses the internet.

Any suggestions?

---

### Post by eteq on 2008-01-28
have you tried "sudo route add default gw 192.168.1.1" ? That shouldn't be necessary, but  maybe it's not setting your gateway correctly if localhost is where everythin is going...

---

### Post by Mike_Gerard on 2008-01-28
Just tried it: no change.

---

### Post by Mike_Gerard on 2008-02-01
After trying different things, I find that wireless networking, with DHCP, is fine so long as I disable roaming.
For wired, a different Linux identifies the controller (Intel 82562GT), but is unable to find the network interface for the selected drive (using e1000 driver). I suspect that I shall have to download the latest driver and integrate it into the kernel (no doubt there are pages explaining how to do this).

---

### Post by rookie76 on 2008-02-01
I have the exact same problem...  Compaq 6820s with not network connectivity.  However, I don't have access to a wireless network to connect to.  I've been trying to figure this driver thing out for a couple of days now.

This thread describes how to fix the driver but for 7.04 and 32 bit...

[http://ubuntuforums.org/showthread.php?t=551720&highlight=Intel+82562GT](http://ubuntuforums.org/showthread.php?t=551720&highlight=Intel+82562GT)

I'm running 7.10 and 64 bit...  I tried to adapt the instructions but no luck.  Maybe you are more astute with this stuff than me.

---

### Post by Mike_Gerard on 2008-02-02
Well, it should be possible to get hold of the driver source on a memory stick. I got hold of what looks like the correct file : e1000-7.6.15.tar. The good news is that it comes with a read-me on how to install it, and which confirmed that it was correct for the kernel version of 7.10. The bad news is that I tried the procedure, but it seems to make no difference. It could be because the procedure must be run as root, whereas Ubuntu expects a simple use of sudo (which is not always equivalent). Anyway, I did get at least one diagnostic which looked as though it was due to not being literally su root.

Maybe I will look into Ubuntu help to see anything on installing ethernet drivers.

I chose to stay with 32-bit when installing 7.10.

---

### Post by Mike_Gerard on 2008-02-04
Success at last. Since I had (wireless) ethernet access I followed the earlier recipe. However, I could have probably done it as per the README of the downloaded driver package.
The key thing seemed to be adding e1000 into the /etc/modules file

echo "e1000" | sudo tee -a /etc/modules

So far it has only taken me a couple of weeks to get the wired ethernet interface working :-(

---

### Post by rookie76 on 2008-02-04
Still no luck...  I ran through all the steps and did not get any errors.

However, when I run pppoeconf I still cannot connect with the router.  Do you think I am still having problems because I'm running 64 bit?:confused:

---

### Post by rookie76 on 2008-02-04
OK, I have installed 32 bit ubuntu and I'm trying again...

Now when I follow the directions from the thread I show above I cannot find the linux header package?...   I switched the address in the link to the kernel I am running and nothing...  how did you get the headers?

---

### Post by Mike_Gerard on 2008-02-04
I don't know exactly what is pppoeconf. All that I know is that, after that final step everything just worked (and it was in DHCP mode with no roaming mode) once I had the e1000 line.

Trying pppoeconf: it finds three devices : eth0, eth1 and eth0:avah , and I have no idea what this last one is, but (from other posts) it seems "normal".

I sort of doubt that the 64-bit is a problem, but would not bet money on it.

---

### Post by Mike_Gerard on 2008-02-04
As I said, I had internet access via the wireless (pop down to your local internet hotspot?) and could run 
sudo apt-get install build-essential linux-headers-2.6.22-14-generic
(from the output of uname -r). My impressin was that this just got the e1000-7.6.5.tar.gz package. I then went through the rest of the instructions. Maybe apt-get install does other things also.

---

