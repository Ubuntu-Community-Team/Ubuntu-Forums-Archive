---
title: "no wireless connection"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by zeusdo on 2008-12-15
I just installed Ubuntu on a laptop and I can not connect to my wireless network. What do I do to get started?

---

### Post by Izek on 2008-12-15
What is your wireless card?

---

### Post by decoherence on 2008-12-15
> **zeusdo said:**
> I just installed Ubuntu on a laptop and I can not connect to my wireless network. What do I do to get started?

Depends on what kind of wireless card you have.

Run Applications > Accessories > Terminal and type

```
sudo lshw -C network
```

copy/paste the output here.

---

### Post by motang on 2008-12-15
If you go to Systems->Administrator->Hardware Drivers does you wireless card showup?  If it does can you activate it? (Make sure you are connected to the network hard wired when you do as it will try to install the wireless drivers).

---

### Post by zeusdo on 2008-12-15
> **Izek said:**
> What is your wireless card?

Linksys card on a laptop

---

### Post by zeusdo on 2008-12-15
> **motang said:**
> If you go to Systems->Administrator->Hardware Drivers does you wireless card showup?  If it does can you activate it? (Make sure you are connected to the network hard wired when you do as it will try to install the wireless drivers).

It says "No proprietary drivers are in use on this system"

---

### Post by Michael.Godawski on 2008-12-15
There are many wlan cards but only few chipsets.

Are you able to post the whole output of these commands (some are mentioned above, too) this will help us a lot.

```
sudo lshw -C network
iwconfig
```

---

### Post by zeusdo on 2008-12-15
> **Michael.Godawski said:**
> There are many wlan cards but only few chipsets.

Are you able to post the whole output of these commands (some are mentioned above, too) this will help us a lot.

```
sudo lshw -C network
iwconfig
```

*-network:0 DISABLED
   description: Wireless interface

when I right click on the Network icon in the taskbar it has a check next to the enable wireless

---

### Post by zeusdo on 2008-12-15
> **zeusdo said:**
> It says "No proprietary drivers are in use on this system"

I connected via a wired connection ans was able to update and then download the broadcomm drivers, thanks for your help.

---

### Post by decoherence on 2008-12-15
> **zeusdo said:**
> *-network:0 DISABLED
   description: Wireless interface


Surely that wasn't EVERYTHING "sudo lshw -C network" spit out? In particular we need the lines that start with "product" and "vendor" but it's best just to give us the complete output.

In Linux-land, when people ask "what kind of wireless card do you have?" they actually mean "what kind of chipset does it use?" (purists will say that this is the same thing.) Saying it's a Linksys only tells us the brand, not the chipset. Saying it's a linksys and giving us the model number will at least let a friendly forum goer investigate what chipset it is.

Best thing, though, is the above command which should give you information on the vendor and the product. From this information we can tell you what wireless driver your system wants and what you need to do to get it working.

If you're concerned about posting personal information, you can modify the command

sudo lshw -sanitize -C network

which removes things like IP addresses and serial numbers.... not necessary for us.

---

### Post by Nico-dk on 2008-12-15
Sorry, thought you were done. Started [my own thread here](http://ubuntuforums.org/showthread.php?p=6374237#post6374237)

Requested output from this thread is already there ;)

---

### Post by Murphy2880 on 2008-12-15
hi there, 
      I've got the same problem! 
  The chipset is RTL-8139/8139C/8139C+  nad the vendor is Realtek! 
 Pls help! 
       10x anyway!
           BR!

---

