---
title: "eth0 and eth1 are gone"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by mgolobay on 2008-08-08
After a night of fighting with all of the dependencies for ffmpeg at some point I lost wired and wireless connectivity.  Linux still boots but the X server won't start.  When I do an ifconfig eth0 and eth1 no longer appear which explains why I've lost connectivity.  Since I'm totally lost, is there an easy way to regain connectivity or would it be easier to re-install.

---

### Post by tamoneya on 2008-08-08
Can you show us the contents of /etc/network/interfaces:```
cat /etc/network/interfaces
```

Also try running these commands:```
sudo ifconfig eth0 up
sudo ifconfig eth1 up
ifconfig
```

---

### Post by mgolobay on 2008-08-08
cat /etc/network/interfaces

auto lo
iface lo inet loopback

Which looks just like the other Ubuntu machine I built at about the same time.  And it does come up with eth0 and eth1

sudo ifconfig eth0 up
works fine but it never gets an IP.  Trying eth1 results in 

error while getting flags: No such device

---

### Post by Iowan on 2008-08-08
Before you re-install, search the forums for a sample **/etc/network/interfaces** file.  Unless the hardware/drivers have disappeared/corrupted, you should be able to rebuild the file - depending on whether your addressing is DHCP or static.

---

### Post by tamoneya on 2008-08-08
can you add these lines to /etc/network/interfaces:```
auto eth0
iface eth0 inet dhcp
```
Then run the following code in terminal:```
sudo /etc/init.d/networking restart
```

---

### Post by Avinash.Rao on 2008-08-08
Ya, dont have to reinstall, just add the entries in /etc/network/interfaces and restart the network services, this should do the job.


> **mgolobay said:**
> cat /etc/network/interfaces

auto lo
iface lo inet loopback

Which looks just like the other Ubuntu machine I built at about the same time.  And it does come up with eth0 and eth1

sudo ifconfig eth0 up
works fine but it never gets an IP.  Trying eth1 results in 

error while getting flags: No such device

---

### Post by Iowan on 2008-08-08
[Here]("http://ubuntuforums.org/showthread.php?t=804930") is a link that contains a copy of mine - it won't help much if you have a static IP address.

---

### Post by mgolobay on 2008-08-08
> **tamoneya said:**
> can you add these lines to /etc/network/interfaces:```
auto eth0
iface eth0 inet dhcp
```
Then run the following code in terminal:```
sudo /etc/init.d/networking restart
```

That did it!  I'm now back online.

But I'm not out of the woods yet since I can't get the desktop to start.  I tried the Xserver and package fix options from the grub menu now that I have connectivity but no luck yet.  I'll keep digging.

Thanks a lot for all the help!

---

