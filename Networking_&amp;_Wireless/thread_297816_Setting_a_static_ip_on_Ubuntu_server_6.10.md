---
title: "Setting a static ip on Ubuntu server 6.10"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by napoelon on 2006-11-11
i am setting up my server, and i have run into a problem. the present dynamic ip is 192.168.0.101. i will like to change it to be static  to 192.168.0.110.

i followed this guide.. [http://www.sematopia.com/?p=50](http://www.sematopia.com/?p=50)

i set mine to as follows..


# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1

for some reason, i can still access it through 192.168.0.101 thru ssh, and i cant access it using the static ip that it should be which is 192.168.0.110

anything else i should do?

---

### Post by Swab on 2006-11-11
sudo ifdown eth0
sudo ifup eth0

Apologies if you have already done this :)

---

### Post by napoelon on 2006-11-11
what exactly does the above do?

EDIT: well i typed those 2 things in, and boom it worked.. so seriously, what does it do lol

---

### Post by Swab on 2006-11-11
> **napoelon said:**
> what exactly does the above do?

Takes down the eth0 interface, then brings it back up again with the new settings.

---

### Post by jayprall on 2006-11-28
I tried this and it didn't work for me either.  I fixed it by adding

auto eth0

right before 

iface eth0 inet static

---

