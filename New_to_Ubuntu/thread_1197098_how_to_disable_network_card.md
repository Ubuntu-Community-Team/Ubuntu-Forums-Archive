---
title: "how to disable network card"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by mevets on 2009-06-25
i have a wireless n card in my desktop that works terribly. is there a way to disable it so i can use a usb network stick?

---

### Post by Revolutionary101 on 2009-06-25
Did you try to change your network connections in System>Preferences>Network Connections? Try that.

Also if you are having problems with the network card in 7.10 Ubuntu I suggest upgrading to 8.10+ because using wireless has become easier in these more recent versions.

---

### Post by mevets on 2009-06-25
i tried that but it only allows me to play with different networks and what i need to do is disable one card and use the usb

the network card is a atheros ar5008 wireless n card. in the upgrade from intrepid to jaunty the driver seemed to get worse so i reverted to intrepid. it still doesnt work reliably though.

---

### Post by Revolutionary101 on 2009-06-25
I cant help you then, sorry. I don't know that much about wireless n cards.

---

### Post by brettg on 2009-06-25
Every wireless laptop I have ever used has had a wireless switch to diable the hardware. The HP my GF uses has a slider switch on the front of the unit, my Clevo/Sager has FN+F6 to toggle it on/off.

I would check the docs for your laptop and take a look at the brown icons printed on the top of your function keys for clues.

---

### Post by mevets on 2009-06-25
> **brettg said:**
> Every wireless laptop I have ever used has had a wireless switch to diable the hardware. The HP my GF uses has a slider switch on the front of the unit, my Clevo/Sager has FN+F6 to toggle it on/off.

I would check the docs for your laptop and take a look at the brown icons printed on the top of your function keys for clues.

This is a desktop tower. Regardless, those buttons usually turn off networking instead of disabling the card.

---

### Post by brettg on 2009-06-25
> **mevets said:**
> This is a desktop tower.

OK, if it is a PCI card then you have to remove the card. If it is built in to the motherboard you should be able to disable it in the BIOS.

If you can't or won't do these things then you will need to blacklist the driver module so that it won't load at boot. Do an lsmod to identify the driver and then place it in the /etc/modprobe.d/blacklist.conf file.
 
>  Regardless, those buttons usually turn off networking instead of disabling the card.

Not true. They are denoted by a picture of an antenna to indicate that they affect the wireless only and I use them often to stop machines from connecting to the wireless AP when they are plugged in via a cable.

---

