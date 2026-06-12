---
title: "Computer to Computer direct wired remote desktop"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2009-11-18
Hi everyone,

I have a rather simple question. How do I use vinagre, the default vnc viewer, to connect into another computer that is connected directly by an ethernet cable?

See, I have a laptop running 9.10, everything working beautifully, and I have a just-installed-this-afternoon ubuntu 9.10 desktop connection that I would like to use vnc to hook up to and control the screen, because i dont have an other monitor.

I have ethernet from the laptop to the desktop, and (i think) I enabled wifi sharing by going to edit connections/ethernet eth0/ipv4 settings/share with other computers

I have previously 'borrowed' one of my friends monitors to make sure that everything on the desktop was set up correctly, i have auto-login, and remote desktop enabled and configured to auto-accept with a password, but for some reason it will not even show up in the list.

---

### Post by teward on 2009-11-18
> **tom.swartz07 said:**
> Hi everyone,

I have a rather simple question. How do I use vinagre, the default vnc viewer, to connect into another computer that is connected directly by an ethernet cable?

See, I have a laptop running 9.10, everything working beautifully, and I have a just-installed-this-afternoon ubuntu 9.10 desktop connection that I would like to use vnc to hook up to and control the screen, because i dont have an other monitor.

I have ethernet from the laptop to the desktop, and (i think) I enabled wifi sharing by going to edit connections/ethernet eth0/ipv4 settings/share with other computers

I have previously 'borrowed' one of my friends monitors to make sure that everything on the desktop was set up correctly, i have auto-login, and remote desktop enabled and configured to auto-accept with a password, but for some reason it will not even show up in the list.

directly connecting the two computers to each other via an ethernet cord won't work.  try connecting to a router with both computers, then connecting.

---

### Post by Cheesemill on 2009-11-18
How have you configured the wired network?

If you have the machines wired directly to each other you will have to manually configure the appropriate IP address and subnet settings as there isn't a DHCP server to provide them automatically.

Also there's a good chance that a normal CAT5 cable wont work, you may need to use a crossover cable.

---

### Post by Cheesemill on 2009-11-18
> **TrekCaptainUSA said:**
> directly connecting the two computers to each other via an ethernet cord won't work.

It will if you make the correct settings and if one of the network cards is auto-sensing.

---

### Post by tom.swartz07 on 2009-11-19
Ok, I was able to get a monitor, but because of our campus' strange internet setup, WIRED internet will not work for Ubuntu- clean access, if i need to say more....

Quite honestly, I only need to update it and install boxee to get this system up to par for a media computer- i have everything else working perfectly.

Is there a way for me to set up an internet connection similar to xbox live forwarding, internet connection sharing, etc, so that I could get online and update my system?

I tried Firestarter, and a few other tutorials online here, but nothing seems to work.

Im going from a 9.10 laptop with a connection, to a 9.10 desktop with no connection, linked to my laptop with an ethernet cable.

---

### Post by benerivo on 2009-11-19
Have you tried this online tutorial...
[http://linuxers.org/howto/how-share-internet-with-other-computers-linux](http://linuxers.org/howto/how-share-internet-with-other-computers-linux)

---

