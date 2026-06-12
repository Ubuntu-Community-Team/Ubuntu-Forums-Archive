---
title: "basic network things"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by jeremytaylor on 2005-08-06
Hi there,
I've used linux for a fair amount of time but I've recently installed it on my laptop and realized I don't understand anything about the way it deals with networks. Can someone point me towards some basic info or answer these questions please?

How do I get the machine to start when it's not connected to its usual network connection? It tries to set up networking on startup and just pauses, I can do Ctrl+c and it moves on to the next thing but the lots of programs don't seem to work.

How can i set up multiple networks? i.e. so it will use my ethenet card when I'm at home and my labs wireless connection at work?

Any help would be very much appreciated.
thanks
Jeremy

p.s. I moved this from the beginner section.... honest I'm not trying to flood all the forums  :)

---

### Post by whoiam55 on 2005-08-07
[QUOTE=jeremytaylor]It tries to set up networking on startup and just pauses,[/QUOTE]

did you setup you static IP correctly while installing ? if it stucking at startup that means you probably using a DHCP server is there any DHCP server exist in network ? what are the type of network you are connecting your computer to. Home network ? if yes how other PC got IP address ? static ? or DHCP if static then assign a static IP otherwise check why you are not able to got IP from DHCP server.

to change IP address chang the /etc/network/interfaces like this

open shell then do the following

vi /etc/network/interfaces

change it so it will look like this
[i]auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address [www.xxx.yyy.zzz](www.xxx.yyy.zzz)
        netmask 255.255.255.0
        network [www.xxx.yyy.0](www.xxx.yyy.0)
        broadcast [www.xxx.yyy.255](www.xxx.yyy.255)
        gateway [www.xxx.yyy.zzz](www.xxx.yyy.zzz)
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers [www.xxx.yyy.zzz](www.xxx.yyy.zzz)[/i]

---

### Post by jeremytaylor on 2005-08-08
thanks I'll go home and try that this evening! 

Is there anyway of using the DCHP still? I think I can set a static IP address but it's my college network and I'm not quite certain?

thanks for the help
Jeremy

---

