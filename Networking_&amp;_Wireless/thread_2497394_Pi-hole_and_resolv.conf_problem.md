---
title: "Pi-hole and resolv.conf problem"
date: 2024-05-03
forum: Networking &amp; Wireless
---

### Post by kozimodo2 on 2024-05-03
I've just installed 24.04 and instead of using my pi-hole for DNS, my resolv.conf has:

```
nameserver 127.0.0.53
options edns0 trust-ad
search lan
```

How do I override the default Ubuntu network configuration to do what my router provides for DNS?

---

### Post by TheFu on 2024-05-03
If Ubuntu Server, put the IP of your pihole into the netplan config file and use networkd as the renderer.  Then re-generate, re-apply, and restart the networking subsystem.

For desktops, things are more complex.  I've posted multiple times in these forums how to remove systemd-resolved.  Find one of those posts and follow it. The order matters, since DNS resolution can impact the ability to sudo.  Doing everything quickly is important too, since at some point you need to enable the pihole and disable other DNS crap before it re-generates and overwrites the new settings.

---

### Post by kozimodo2 on 2024-05-03
It is a desktop system.  The problem with your [desktop solution]("https://ubuntuforums.org/showthread.php?t=2496198&p=14182845#post14182845") is that resolv.conf is set manually and the box is a laptop.  While I mostly use the system at home, if I take it elsewhere, I will need to manually edit the resolv.conf every time I leave home.

---

### Post by TheFu on 2024-05-03
Most home routers have a way to set the DNS to be used.  This can be with full **DHCP Reservations**, or just as a router setting to use a specific pair of LAN DNS servers.  Put the IP address of the pi-hole in your router to be provided with the DHCP requests. No change needed on the laptop.  Anyway, the router documentation should explain how to accomplish this.

If I had an Asus Router, I'd google for "Asus {model} lan DNS settings".  One of the top 3 results for that query found this:
     
>     #2 The WAN DNS is what the router uses for itself. The LAN DNS is the address(es) given out to DHCP clients.

That says to find the LAN DNS(es) setting in the router configuration pages and point them at the PiHole devices.  All DHCP clients will be provided that DNS to be used by systemd-resolved which does local caching of DNS on linux, unless you disable it.  In my world, I want my LAN DNS servers to do the caching, not each system, so systemd-resolved is completely disabled and removed from the systems.  My /etc/resolv.conf is setup like it was in 1995, before DHCP existed.

If using DHCP Reservations on your LAN for the laptop, which I would do to ensure my laptop got the same IP every time it connected on the LAN, be certain that the static IP is selected outside the DHCP dynamic range and doesn't conflict with any other network device on the same subnet.

If laptop had been mentioned, I'd have made a different suggestion, BTW.  "desktop" != "laptop".  A laptop that moves between different networks is a special animal.

Also, I had to make about 20 other assumptions due to the lack of data provided in the original post - like the version of Ubuntu and the DE used, if any.

---

