---
title: "Recovery Mode- No Networking?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by birdwin on 2009-04-13
Is networking not enabled by default if you enter recovery mode in GRUB? I'm trying to fix packages on my system (see here: [http://ubuntuforums.org/showthread.php?t=1123774](http://ubuntuforums.org/showthread.php?t=1123774)), but I can't get networking up when I'm in recovery mode. I've tried 'ifconfig eth0 up', 'ifconfig eth0 inet up' and 'ifconfig wlan0 up' (when I do the latter, my wireless light goes on). After doing each of these, I've tried 'sudo apt-get update' and 'sudo apt-get upgrade', and neither can resolve the hosts. Is networking generally not available during recovery mode, or is this a problem with my system only?

---

### Post by Hospadar on 2009-04-13
Does your wireless network have a password?  If not, you'll first need to do something like "sudo iwconfig essid <your wifi name>"

(you can google and "man iwconfig" for more info about this)

If you have a password you'll have to set that up too. (which for wep uses iwconfig, and for wpa, it's much harder, it would probably be better to just turn off your password while you're doing this)

Basically, you just need to tell your machine what wifi network you want to connect to before you connect.

Once you do all your iwconfig, then you an ifup

---

### Post by lolol i r linux noob on 2009-04-13
wireless is probably eth1

---

### Post by cariboo on 2009-04-13
When you start in recovery mode, networking is enabled, but dhcp3-client isn't. You have to request an ip address from your router at the prompt type:

```
dhclient wlan0
```

Substitute you network device if it is different.

Jim

---

### Post by birdwin on 2009-04-13
I got it working. Apparently NetworkManager removes connections that it manages from /etc/network/interfaces, so 'ifconfig eth0 up' won't use DHCP by default. I added 'iface eth0 inet dhcp' to /etc/network/interfaces, and running 'ifup eth0' worked like a charm. Thanks all.

---

