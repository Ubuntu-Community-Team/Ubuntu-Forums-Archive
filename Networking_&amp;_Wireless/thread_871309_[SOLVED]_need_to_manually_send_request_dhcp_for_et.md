---
title: "[SOLVED] need to manually send request dhcp for eth0 since installing wifi stuff"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by ghoulsblade on 2008-07-26
I have to manually send a dhcp-request to my router ("sudo pump") after each reboot,
otherwise i don't get an ip for my normal,wired LAN.
It worked fine a while ago, i think it stopped working ever since i installed some wireless related packets 
(wireless-tools,kwlan,wpasupplicant,aircrack-ng,kismet and maybe others).
Having to do this is rather annoying, and i think installing wlan stuff isn't supposed to break normal wired LAN in this way.
Could someone please give me a hint on how to resolve this ?  
Can i maybe add the "pump eth0" to one of those scripts in /etc/init.d/ or would that be a bad idea ?

I'm running KUbuntu 8.04.1, kernel 2.6.24-19-generic
any help appreciated,
best regards,
ghoulsblade

---

### Post by ghoulsblade on 2008-08-02
a friend took a look and we solved the issue by manually editing 
/etc/network/interfaces :

adding a line 
iface eth0 inet dhcp
at the bottom

and adding eth0 to the line starting with auto :
auto lo eth0


/etc/network/interfaces  looks like this before :
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

```

and now it looks like this:
```

auto lo eth0
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

```

might be a bug in the kde system control panel for network settings, as i had enabled eth0 there, but it seems it didn't save it to that file.

anyway, issue solved =)

---

