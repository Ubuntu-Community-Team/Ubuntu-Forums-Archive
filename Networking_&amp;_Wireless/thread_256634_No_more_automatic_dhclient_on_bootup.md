---
title: "No more automatic dhclient on bootup"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by Tonren on 2006-09-13
Hay guys.  Recently I've been messing with my networking a little bit, and "Configuring network interfaces..." no longer runs dhclient eth0 on bootup.  Once I've actually booted and logged in, I can run "sudo dhclient eth0" and everything runs swimmingly.  However, it'd be awfully nice to get my automatic configuration back.

I'm not sure what the exact cause could be... I've snooped around in dmesg but nothing there seems to relate to DHCP, and the only few lines about eth0 haven't given me any hints.

I must stress that all I need to do to gain connectivity once I login is just run "sudo dhclient eth0".  I could probably insert this into a bootup script, but that feels really duct-tapey.  I'd like to find out what made it stop working in the first place, if possible.

---

### Post by tbonius on 2006-09-13
Check your /etc/network/interfaces config file.  

Should say something like:

auto eth0
iface eth0 inet dhcp



T

---

### Post by Iowan on 2006-09-13
System>Administration>Networking>Properties should have similar information - insure eth0 is enabled and and set for DHCP.

---

### Post by kipeloff on 2006-09-14
I have the same issue, than added 'dhclient' to obtain lease at the startup programms. It works fine for me.

---

### Post by Tonren on 2006-09-14
I figured it out, guys.  kipeloff, you should use my method instead of yours, because Startup Programs are attached to users, but if someone ELSE logged in, it wouldn't be automatic.  My method is lower-level, and runs on bootup.

The answer is in /etc/network/interfaces.  It determines how the system "automatically" configures your network interfaces.  Here's what mine looked like BEFORE:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

Notice that there's no "auto" for eth0.  I added one, and it worked fine!

I also realized that it wastes time trying to connect to the wireless even when I'm wired!  The solution was to check a special file that reflects the connectivity of the ethernet port.  (this has nothing to do with the actual topic, but is a useful trick)

Here's what my /etc/network/interfaces looks like now:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        pre-up ifconfig eth1 down
        pre-up ifconfig eth0 up

auto eth1
iface eth1 inet dhcp
        # only connect if eth0 is not plugged in
        pre-up [ `cat /sys/class/net/eth0/iflink` -ne 2 ]
        pre-up /usr/bin/wireless.sh
```

Here's the contents of wireless.sh:

```
sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwconfig eth1 ap any
sudo iwconfig eth1 essid any
```

---

