---
title: "Wireless networks not showing up."
date: 2010-03-02
forum: New to Ubuntu
---

### Post by gameguy245 on 2010-03-02
I've recently done a reinstall of Ubuntu 9.10 not too long ago. I installed all of the necessary packages to run my Broadcom BCM4306 wireless card (e.g. ndisgtk, b43-fwcutter). The code "sudo lshw -C network" shows that my card is working, but none of my networks show up. If i manually put down the information for my network it connects in 3 seconds, but i still can't any where. 

I found out that it doesn't even matter. I can put the network name as "tacos" and it will still "connect" anyway. Additionally, when I disconnect, a bunch of weird network names show up in my available list. I can't really show how it looks but it's just... weird.

Any ideas about what's wrong?

---

### Post by kerry_s on 2010-03-03
you only need b43-fwcutter, if your also using ndiswrapper then there's probably a conflict of drivers.
what i do i use synaptic to install b43-fwcutter, then reboot. i don't like using the hardware drivers program cause it's buggy, but it should show that it's activated after. you need to make sure your connected to the internet, either using a hard line or wireless that don't need drivers, so it can download it.

---

