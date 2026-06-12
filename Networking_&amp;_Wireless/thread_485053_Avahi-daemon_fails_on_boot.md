---
title: "Avahi-daemon fails on boot"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by neok on 2007-06-26
Hi!

I have a problem with my WiFi connection and Avahi-daemon, in Feisty. When I configured my network in the /etc/network/interfaces file, avahi-daemon fails on boot and GNOME doesn't boot (GDM works).

I use DHCP in my WiFi connection and WEP128. My /etc/network/interfaces file is like:

```
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
address 192.168.0.11
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid THOMSON
wireless-key MY_WEP_KEY

auto wlan0
```

In Dapper I haven't got this problem. My solution is to clear the /etc/network/interfaces file, and configure manually in all boots the network using network manager, it's a lot of work!

Anyone has a better solution?

Thanks!

---

### Post by spd106 on 2007-06-26
First I think you should edit the interfaces file. If you are using dhcp then you don't need address, netmask and gateway assignments, so comment then out. If you're using static then change the iface line from dhcp to static. I would also change the order so that the wireless- lines are before the address etc.

Secondly, I think you should check the /var/log/syslog file for Avahi-daemon errors, this should help you diagnose what's wrong. Also check that Avahi-daemon is set to start automatically in the /etc/default/avahi-daemon file, the default in Ubuntu 7.04 (Feisty) is on, whereas in Ubuntu 6.06 it was off. 

Avahi-daemon is not a critical service, so even if it fails you should still be able to start GNOME. This suggests that you may have deeper problems.

---

### Post by neok on 2007-06-27
**spd106** I will look in /var/log/syslog for avahi errors and if there are errors, I will post them.

When I had the first error, I put off avahi-daemon using /etc/default/avahi-daemon file, and GNOME doesn't boot in the same way when avahi-daemon fails.

I see bugs in launchpad with the same problems, but nobody has a diferent solution.

Thanks!

---

### Post by vanadium on 2007-06-27
I have had a similar issue. What I did is start with a "clean" etc/network/interfaces each time at booting. At that point, network manager alone does all the network configuration.

* create a file /etc/network/networking.default that contains only (command: gksudo gedit /etc/network/networking.default)

```

auto lo 
iface lo inet loopback 

```

permissions should be like:

```

-rw-r----- 1 root admin 207 2007-05-21 10:01 interfaces 

```

(use sudo chown root and sudo chmod 640 if needed. I am not sure whether this is necessary, but these are also the permissions of /etc/network/interfaces)

Then edit /etc/init/networking. (gksudo gedit ...) This is the startup script that initializes networking. Right after the PATH= statement (at the start of the file) I added:

```

cp /etc/network/interfaces.default /etc/network/interfaces 

```

This will make sure that the interfaces file is each time "reset" before initializing the network. Indeed, network manager changes that file, and for me, I had difficulties starting up especially when starting at a different location that requires a different network configuration.

---

