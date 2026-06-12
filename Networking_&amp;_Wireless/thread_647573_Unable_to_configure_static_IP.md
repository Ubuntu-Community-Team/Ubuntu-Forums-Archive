---
title: "Unable to configure static IP"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by bristleburger on 2007-12-22
I've got a machine running gusty which refuses to boot into X/gdm.

I would like to attempt to reinstall xorg and gdm using apt-get or dpkg to see if I can fix this, but unfortunately the network interface doesn't come up either :-(

I feel it should be easy to configure a static IP address by editing /etc/network/interfaces, but I can't get it to work.

If I use ifconfig to set an IP address, I am able to ping other machines on my LAN but can't ping any WAN servers – this means that I can't use apt-get.

This seems like a problem that should be quite easy to fix, but I'm out of ideas.

Any suggestions would be gratefully received.

---

### Post by guyvertoon on 2007-12-24
Sounds like you have the wrong gateway and/or DNS addresses entered. Check with a box that is working.

HTH

---

### Post by wieman01 on 2007-12-24
You could basically use my WPA tutorial and copy the Static IP section (signature). It should work for you as well.

---

### Post by willie_wang on 2007-12-24
yeah, i had the same problem. tried for days and DAYS to get a static IP.

The solution I found was just to configure the router to assign specific IPs through DHCP to each mac address of each computer on the network. Hope that makes sense. :)

---

### Post by likes2skate on 2007-12-27
I have two desktops with wired networking and gutsy.

For me, static IP does NOT work on kubuntu, but DOES work on edubuntu.

Go figure.

---

