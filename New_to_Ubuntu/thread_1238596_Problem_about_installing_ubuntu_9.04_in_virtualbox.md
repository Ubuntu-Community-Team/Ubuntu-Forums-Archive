---
title: "Problem about installing ubuntu 9.04 in virtualbox"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by vash2033 on 2009-08-12
I'm new in using linux os. I've been using the ubuntu 9.04 about a couple of months and it's doing great. , its pretty awesome, bt when i used it in my present system (vista black edition) in a *virtualbox*, i can't activate desktop effects. Everyime i boot up the ubuntu in virtualbox, it always keep on asking me to set to 32 bit color mode.. The problem is, i don't know how to fix it.. i've already tried setting the display to highest diplay 1024X 768 (available in the resolution opton). But nothing happens. Or is it having a conflicts in my windows os.. (or hardware)? please feel free to post an advice. Thanks in advance. 
 
ASUS motherboard
Intel (R) G33/G31 Express Chipset Family
Pentium(R) dual core E5200 @ 2.5GHz
2 GB RAM
32 bit OS

---

### Post by SecretCode on 2009-08-12
Desktop effects require a graphics card capable of 3D acceleration, and the 3D acceleration in virtualbox is 'experimental'. .... Have you in fact turned on 3D acceleration in the vm settings?

That message about running in 16 bit mode appears every time I boot a vm - presumably the startup screens are 16 bit - so I've turned it off.

---

### Post by vash2033 on 2009-08-21
How can i set to 32bit instead of 16bit when booting ubuntu in VM? (if possible)
I'd already tried turning the 3D acceleration on and i set also these seetings too..
 
*Base memory of 768MB
*Video memory of 32MB only (i don't know how much is the minmum requirement for activating desktop effects) but nothing happens..
 
One more thing, why do i can't set to any other option in visual effect, it only set to NONE and displays a message "Desktop effect cannot be enabled"?
 
 Any idea? please help, thanks..

---

