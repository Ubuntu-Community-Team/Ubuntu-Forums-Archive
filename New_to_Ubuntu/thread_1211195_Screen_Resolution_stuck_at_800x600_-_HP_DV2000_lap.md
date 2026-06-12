---
title: "Screen Resolution stuck at 800x600 - HP DV2000 laptop 14.1 inch widescreen display"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Phlei on 2009-07-12
Hello:

I just got Ubuntu installed successfully on my laptop (yay for me).

I am trying to get a higher screen resolution and cannot find anything that works.

I have tried: 

System-Preferences-Screen Resolution  : nothing there

sudo apt-get install displayconfig-gtk     Alt+F2   gksudo displayconfig-gtk  : I tried a few of the HP displays here but none of them work. I do not know my exact model number/display type (will knowing this do it?) 

Can anyone help me or give me some hints? 800x600 drives me nuts

Thanks for the help! I am looking forward to transitioning to Ubuntu!!!

Cheers

---

### Post by halitech on 2009-07-12
looks like you have an Nvidia video card based on the specs for the machine. Have you checked under System - Admin - Hardware drivers to see if it has drivers for you to use?

---

### Post by northern lights on 2009-07-12
Please post the output of```
sudo lshw -C display
```

---

### Post by nhasian on 2009-07-12
how can you be sure its an nvidia adaptor?  HP uses Nvidia, Intel, and ATI video adaptors.  the best way is to open a terminal from Applications->Accessories and type:

```
lshw -C display
```

> **halitech said:**
> looks like you have an Nvidia video card based on the specs for the machine. Have you checked under System - Admin - Hardware drivers to see if it has drivers for you to use?

---

### Post by Phlei on 2009-07-12
I figured it out...it was the drivers.

When I installed all of the Ubuntu updates it then asked to update video drivers...restarted...and it's beautiful.

So far I am pretty impressed with how Ubuntu looks...let's just see if I can get some windows apps to work now.

Thanks everyone!

---

### Post by LewRockwell on 2009-07-12
> **Phlei said:**
> I figured it out...it was the drivers.

When I installed all of the Ubuntu updates it then asked to update video drivers...restarted...and it's beautiful.

So far I am pretty impressed with how Ubuntu looks...let's just see if I can get some windows apps to work now.

Thanks everyone!

you don't need no stinkin' windoze apps...

.

---

### Post by halitech on 2009-07-12
> **nhasian said:**
> how can you be sure its an nvidia adaptor?  HP uses Nvidia, Intel, and ATI video adaptors.  the best way is to open a terminal from Applications->Accessories and type:

```
lshw -C display
```

I was basing it on the fact that I went to the HP website and found the DV2000 series and it said an Nvidia GoForce 7300 (if I remember right) was installed in that machine. Either way, if the OP checked restricted drivers they should have seen an ATI driver or an Nvidia driver and if by chance it is an intel card, well it should have given them better then 800x600 to start.

---

