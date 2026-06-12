---
title: "Any idea as to why google earth doesn't work?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-08-18
Hi all,

I tried a few times now to install Google Earth but it just closes when I try to use it or it just sits there and stalls. Any ideas?

---

### Post by LowSky on 2009-08-18
how did you install it?

what graphics card are you using?

what happens when you open a termnial and type
```
googleearth
```

---

### Post by tahitiwibble on 2009-08-18
> **LowSky said:**
> how did you install it?

what graphics card are you using?

what happens when you open a termnial and type
```
googleearth
```

Hi,

I installed it using Synaptic and the graphic card is the onboard stuff on my mother board (I think it's in my signature). I can start it OK but it's when I try to use it that nothing happens or it quits. All I ever saw was a black, blank screen where the image usually is.

---

### Post by stinger30au on 2009-08-18
> **tahitiwibble said:**
> Hi all,

I tried a few times now to install Google Earth but it just closes when I try to use it or it just sits there and stalls. Any ideas?

googlearth will only run on a pc that has correct video card drivers installed be it nvidia or ati

if they are not installed correctly, this error that you get will occour

the other error that will happen is that ubuntu will just log u off and take you back to the log on screen

---

### Post by philinux on 2009-08-18
> **tahitiwibble said:**
> Hi all,

I tried a few times now to install Google Earth but it just closes when I try to use it or it just sits there and stalls. Any ideas?

What you got in system>admin>hardware drivers?

---

### Post by tahitiwibble on 2009-08-18
> **philinux said:**
> What you got in system>admin>hardware drivers?

It says "No proprietary drivers are in use on this system"

---

### Post by tahitiwibble on 2009-08-18
> **stinger30au said:**
> googlearth will only run on a pc that has correct video card drivers installed be it nvidia or ati

if they are not installed correctly, this error that you get will occour

the other error that will happen is that ubuntu will just log u off and take you back to the log on screen

Hmmm, does that mean that I may get away with installing a driver ........ or does it have to be a whole new card?

---

### Post by tahitiwibble on 2009-08-19
Can I just install a driver? or does it have to be a new card?

---

### Post by hovzio on 2009-08-19
hi, I am having the same problem... fire up googleearth and it crashes,.(exactly as the op has described) I have a GeForce 9800 GT and the drivers are in place... everything works as should.(compiz, gaming..) I havent really looked into it to much but i dont think its the drivers. I have used ubuntus restricted drivers app and I have manually installed the driver coming from nvidea site. If you have compiz running on your pc (cube and 3d) and you have no "restricted drivers" then theres about a 99% chance of having an intel onboard gfx card. In that case there are no restriced drivers to worry about and things are in place.. I'll keep looking and let you know if I find anything, btw I'm running Hardy, prior distributions have not had an issue with GE.

---

### Post by Paddy Landau on 2009-08-19
Google Earth is notoriously unreliable on Linux.

You can try this [Google Earth Troubleshooting]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Google_Earth") section, but it's not guaranteed to work.

---

### Post by BadgerKid on 2009-08-20
> **Paddy Landau said:**
> Google Earth is notoriously unreliable on Linux.

You can try this [Google Earth Troubleshooting]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Google_Earth") section, but it's not guaranteed to work.

Agreed. On my laptop with an ATI card, GE worked/works under Ubuntu 8 and 9 for AMD64.  On my desktop, also with an ATI card, GE from either medibuntu or Google will apparently crash X on 8.04LTS for AMD64.

Many thanks for the link to the troubleshooting. I will certainly be taking a look.

---

### Post by tahitiwibble on 2009-11-14
Google Earth works perfectly since I installed a medium-high end NVIDEA card

---

