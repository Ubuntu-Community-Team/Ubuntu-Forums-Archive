---
title: "Shared memory for graphics card only 8 MB?"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by duruttye on 2009-04-12
Is it possible?

I'm using a DELL vostro A680, with ubuntu 8.10, upgraded memory to 3GB, dual core 2.0 Mhz processor, intel graphics video card.

I found out this (from the BIOS) after I posted a thread about the graphics driver not installed properly... still not sure about that.

I'm not able to find where I can increase the amount of shared memory so that I can allocate some more to the use of the graphics card, maybe that will take care of the lousy glxgears... around 200 fps... I saw already a few BOIS settings, but this one is too much to me, I can't find where to increase it... Maybe there are some applications inside ubuntu that can solve this...

Help me please!!!

---

### Post by ajgreeny on 2009-04-12
I am pretty sure this will be a bios setting which you will change with a key press of some sort to increase and another to decrease.  It will depend on your bios, so search a bit more.  Normally any changes you make before leaving the bios have to be confirmed at exit, so if you make a mistake just exit without saving changes and try again

---

### Post by duruttye on 2009-04-12
Well, I checked, and double-checked, but I can't find it.

It is in a menu, that says that, this is only information, these can't be changed...

---

### Post by halitech on 2009-04-12
Some laptops only have a low amount of ram allocated to the video card but with the way windows is designed, it can "steal" system memory to up the video memory as needed. I have an old toshiba tha tonly has 8meg as well with no way to change it. It really depends on the laptop.

---

### Post by duruttye on 2009-04-12
The only thing is, that this is a new laptop and with ubuntu on it. Can ubuntu "steal" memory, like windows can?

---

### Post by halitech on 2009-04-12
if its new, call Dell and ask them if you can up the video memory allotment. If you can't, then as far as I know, Linux can't re-allocate memory like windows does.

---

