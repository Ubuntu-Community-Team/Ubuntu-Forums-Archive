---
title: "Easy routing?"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by Zorael on 2008-03-08
I'm on a laptop, with both a wired connection and a wireless. Depending on where I am, I prefer to connect through wired, but if there aren't any hubs nearby I switch to wireless and I'm happy.

In Windows this was easy, just had to set up both connections and connect them, then if either broke down the other took over. So in practice, when I unplugged the wired connection the wireless  became the device assigned to both the default route and the route for the local network.

In linux, this is hard. When I want to switch, I have to open up a console, and type stuff.
```
$ sudo route del... *(stuff so the table is empty)*
$ sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev wlan0 *(or eth0)*
$ sudo route add -net default gw 192.168.0.1
```

Is there a way to make this easier? As in, to assign 192.168.0.0 *and* default to both devices, and have it put priority on the wired connection?

NetworkManager generally flips out and sets default gateway to 0.0.0.0, which makes everything break down.

Am I missing something obvious? :<

---

### Post by jeffus_il on 2008-03-08
Have you tried Wicd, it's much better than NetworkManager, that is right now, NetworkManager is improving but still has too many kinks for me. There are plenty guides around, you have to add the Wicd url to the repositories and change the dhcp client to dhcp3.

---

### Post by Zorael on 2008-03-08
wicd doesn't work at all for me. After a reboot, it has renamed my wireless network, and moreover, fails to detect it. So I have to fall back on ifconfig/iwconfig/route anyway.

Isn't there some other solution? Perhaps set it up to run certain scripts when links go up and down? Meaning, when I connect and disconnect either of the interfaces?

At the moment I have to manually remove all route entries, as there to my knowledge is no command to wipe the table in one blow. Then map 192.168.0.0/255.255.255.0 to the current device, and set default gw 192.168.0.1.

---

### Post by Zorael on 2008-03-08
This is the mess NetworkManager leaves me in. And remember, wicd didn't even detect the wireless network after a reboot (did before when NetworkManager had configured stuff).

```
zorael@azrael:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0_rename
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth1
default         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0_rename
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
```

In this particular case I wanted to switch to my wireless device; wlan0_rename.

```
$ sudo su
# route del -net 192.168.0.0 netmask 255.255.255.0 dev eth0
# route del -net 192.168.0.0 netmask 255.255.255.0 dev eth1
# route del -net link-local netmask 255.255.0.0 dev eth0
*(defaults gone at this point)*
# route add -net default gw 192.168.0.1
```

That's an awful lot of keys to hit everytime I switch between wireless and wired. And I *know* you can somehow set up link up/down scripts, but I don't possess the scripting skills to create any such. :<

---

### Post by Zorael on 2008-04-19
Bump because my fingers hurt from typing all that every time I switch between wired and wireless. :<

---

