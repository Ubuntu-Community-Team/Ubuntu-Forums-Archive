---
title: "DHCP Server"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by Robotuner on 2007-02-24
Hi,  I'm fairly new to linux and Ubunto.  I have installed Edgy on my laptop and would like to give dhcp a try.  Looking at Synaptic Package Mananger, I see that dhcp3-server is installed on my laptop, so what I would like to do is learn how to activate it on an intermittant basis.  

The scenario is that occasionally, I have a need to setup a small local network of machines that does not necessarily need/have internet access.  (Think the night of an auction and I want to link together several laptops for checkout purposes.)  Under normal usage, Edgy connects and gets its IP from my router, so I would want to only turn on the dhcp server when I need it.

Thanks.

---

### Post by kidders on 2007-02-24
Hi there,

You shouldn't encounter any problems doing what you've described. DHCP server configuration is extremely well covered, both here and elsewhere, and you won't have to do anything weird to set yourself up. :-)

The one wrinkle to be aware of is that the machine running the server itself will require a manually assigned IP ... but only while the DHCP server is in use. Once you've sorted out all the steps necessary to switch between "I'm a DHCP client" mode and "I'm a DHCP server" mode, and arranged everything the way you like it, I would suggest creating a pair of short scripts to automate the process for you. That way, whenever you need to quickly test a new set of machines, you can rely on it to just work.

---

### Post by gradedcheese on 2007-02-24
I'd like to suggest a different (more modern? :)) approach -- link-local networking.  In this scheme, your PCs will self-assign addresses in the 169.254 prefix, resolving any conflicts before announcing their address.  They'll do this when they don't find an address via DHCP (but not otherwise).  To use this, make sure avahi is installed and enabled.

---

### Post by Robotuner on 2007-02-24
What a great solution, my problem is that all the other machines are likely windows machines.

---

### Post by gradedcheese on 2007-02-24
Actually, Windows supports Link-Local networking just fine (especially in ad-hoc WiFi networks).   It first tries DHCP (as you'd expect), then it fails and assigns itself a 169.254.x.x address.  MS just has some other name for it (I don't recall what it is) while Apple calls it IP4LL.  I don't use Windows so I am not 100% sure about how to make it do this if it's not doing it, but I have personally seen it do this out of the box (I think it was XP).  You can also install Apple's Bonjour suite for Windows, this is like an Avahi for Windows essentially: [http://www.apple.com/support/downloads/bonjourforwindows.html](http://www.apple.com/support/downloads/bonjourforwindows.html)

---

