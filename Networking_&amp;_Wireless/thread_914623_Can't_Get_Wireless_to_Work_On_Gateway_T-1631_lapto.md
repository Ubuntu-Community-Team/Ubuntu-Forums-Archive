---
title: "Can't Get Wireless to Work On Gateway T-1631 laptop"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Pyrotechnic on 2008-09-09
I just bought a new laptop, a Gateway T-1631... it comes with Vista pre-installed, so I wanted to put Linux on there because I don't like Vista.  So far, I'm having zero luck getting the wireless card to work in Ubuntu 8.04.  I've searched everywhere for the proper driver for my card, with no luck, and I've seen other people with this same problem, but I've yet to come across the solution.

My wireless card is an integrated Realtek RTL8187S.  If anyone could point me towards the driver, or tell me how I'm supposed to get this thing working (keeping in mind I'm fairly new to Linux), I'd really appreciate it.

---

### Post by SweetTeaTurner on 2008-10-30
I can't really help, as I haven't gotten wireless to work on my t-1631, but I did install ndiswrapper, the frontend, ndisgtk, and found the xp drivers for the wireless card in the laptop, and drivers for a very similar card. What I found was installing the correct drivers produces nothing, while having both the correct drivers, and incorrect ones installed allowed ubuntu to see my wireless network, but not connect. I unsecured my network, and it still wouldn't connect. It tried for a while, but eventually ended its try, saying "network disconnected" or something like that. I can give more detailed info, if someone wants a go at trying to solve this. My guess is we won't have a solution until more folks get this model laptop, or more laptops are equipped with the wireless included in the t-1631.

---

### Post by Jc61990 on 2008-12-02
Im having the same problem with the same notbook.
i tried that ndiswrapper thing, and got no luck.. only im on ubuntu 8.10, but that shouldnt make a difference

---

### Post by Jc61990 on 2008-12-02
actually after looking again i found this thread

[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

---

### Post by WinterMadness on 2008-12-02
in order for ndiswrapper to work, youll need your wireless cards XP driver. the vista one will not work. usually you can find it on the manufacturers website. after you do that you simply install it via terminal or the graphical user interface. if you need any further help, let me know. Wireless was a pain for me at first too

---

### Post by Jc61990 on 2008-12-03
yes help would be great!

i got the driver installed. but when i click configure, it says "no network configuration tool present."

what should i download for that?

---

### Post by SweetTeaTurner on 2008-12-07
The driver here: [http://code.google.com/p/msi-wind-linux/](http://code.google.com/p/msi-wind-linux/) works. I am posting this message from within ubuntu, using the wireless now. My network is unsecured, so I can't speak to those capabilities. Have fun.

---

### Post by SweetTeaTurner on 2008-12-07
I updated to kernel 2.6.27-9, and wireless ceased to work, along with it booting with the wrong theme, and the gnomes setting manager failing to start. The previous kernel works fine with the driver I mentioned, though.

---

