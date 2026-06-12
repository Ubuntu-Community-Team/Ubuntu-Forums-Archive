---
title: "Can't Connect!"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by sLxNet on 2008-02-07
Hey guys, I'm a little new with linux, so be easy if you would.

I just finished installing the latest version of Ubuntu to mess around and get away from windows for once.  Everything went swell until I realized that I had to configure the network myself!  I'm very lost, however, I have done my research.  I can't get my Realtek 8201CL PHY LAN Chip to connect.  I'm probably doing something wrong.

If it helps, the Realtek 8201CL PHY is on an Asus A8V-XE.
Thanks!
Josh

---

### Post by Iowan on 2008-02-07
May need a bit more info... connect to what?  Did your Windows machine get it's address via DHCP or did it have a static address? Is there another machine on the network? From a terminal, check **ifconfig** to see if the card has an address.  (Or you can look under System>Administration>Network Tools(Devices,eth0).

---

### Post by sLxNet on 2008-02-07
Connect to the internet as a whole.  My windows machine got it's address itself via DHCP.  There are many machines on my network (about 7 in my home alone).  

Not sure what you mean when you asked if my card has an address, but this is what terminal shot back at me.  [http://i25.tinypic.com/221di1.jpg](http://i25.tinypic.com/221di1.jpg)

Thanks for the patience and the help!
Josh

---

### Post by Iowan on 2008-02-07
OK!  Looks like eth0 has been assigned an address (192.168.1.105).  If the other machines in your network are in the same subnet (probably with addresses 192.168.1.XXX), you should be able to connect (at least to them...)  Which machine (or router) has the internet connection  - what is it's address?  When I first started w/ Ubuntu, I needed to set up gateway address, but after upgrading, I see System>Administration>Network>Wired connection/Properties shows  Automatic Configuration (DHCP) - Dunno what "Enable Roaming" does.

---

### Post by sLxNet on 2008-02-07
The machine has an address of 192.168.1.103

---

### Post by bwtranch on 2008-02-07
Still need the output of ifconfig iwconfig and might as well post lspci or just lshw. Might as well get the whole rundown on this caper.:)

---

### Post by Iowan on 2008-02-07
Is that a Windows machine?  Also, is there a DHCP server on your network, or by "I had to configure the network myself!", do you mean you set up a static ip address?  If you set up a static address, you might gain on the problem by configuring the gateway to be 192.168.1.103

---

### Post by bwtranch on 2008-02-07
Re#7 Might work in one instance, but what happens on a re-boot? If he/she has a DHCP connection it will be different (probably) each time. Or, if you have an ISP like mine, they rotate the IP address every six hours, so in that case you would go down 4 times a day and have to re-enter it.

---

### Post by bwtranch on 2008-02-07
Oh yeah, sorry, forgot. Turn roaming off. Mine won't work at all with roaming on. Yours may be different, but for the time being let's shut it off.

---

### Post by Iowan on 2008-02-07
> **Iowan said:**
>   If you set up a static address, you might gain on the problem by configuring the gateway to be 192.168.1.103 On a re-boot, a static address should still be static.  If address is via DHCP...

---

