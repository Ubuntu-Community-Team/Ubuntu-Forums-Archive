---
title: "Just had internet installed, unable to configure dhcp correctly"
date: 2005-07-15
forum: Networking &amp; Wireless
---

### Post by hollywoodb on 2005-07-15
Just got a direct connection set up, however I've never configured linux for internet without being behind a router, which I've never had a problem with...

I've got my hostname set correctly.
Domain & nameserver are set correctly in /etc/resolv.conf
added "iface eth0 inet dhcp" to /etc/network/interfaces

/etc/init.d/networking attempts to configure the device, but after about 60 seconds it fails to fetch an IP, etc... 

lsmod shows correct module (forcedeth) is loaded

ifconfig shows some ipv6 info for eth0, but nothing relating to my actual internet connection

I do have a windows partition I'm using now, and it works fine here with everything in network options set to automatic, so what am I missing?

---

### Post by blu.gecko on 2005-07-15
just a question, but your not a insight customer are you? :roll:

---

### Post by hollywoodb on 2005-07-16
no... but after browsing many a debian & ubuntu forum thread.... I ended up just backing up configs, reinstalling and letting the installer do the work, then restoring installed packages in configs.... took about 1.5 hrs, which is less time than I spent trying to get 'net working in the first place  :roll:

---

