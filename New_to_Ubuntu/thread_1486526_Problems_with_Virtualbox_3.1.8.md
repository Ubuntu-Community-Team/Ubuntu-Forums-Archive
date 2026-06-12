---
title: "Problems with Virtualbox 3.1.8"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-05-17
Hi, just trying to see if anyone has any ideas, or is having the same problems, with Virtualbox 3.1.8. I have it installed on Ubuntu 10.04 64-Bit from VBox's repositories. It is using excessive amounts of CPU (System Monitor reports 90-108% of CPU is taken by VBox...). Also, even though I have proprietary drivers for my ATI Radeon HD 5770 I cannot enable 2d or 3d acceleration for the guest (Windows XP).

---

### Post by QIII on 2010-05-18
Forgive me if this is a bit basic, but I have no idea what your level of  experience is with VirtualBox...

First, with regard to 3D acceleration:
 
 It matters little what your host machine's video card is.  VirtualBox  uses a virtual card originally designed by the German company innotek  GmbH, but since taken over by Sun.  If you install Guest Additions, you  get a better virtual card with better performance.  To set 3D  acceleration, right click on the VM, select "Display" and toggle "Enable  3D Acceleration".  That may or may not allow you to use 3D acceleration  in Windows.

Is that checked?
 
With regard to processor usage:

 How many processors does your machine have?
  
  If you have a single processor and give that over to the guest in  VirtualBox, you  will likely get that sort of behavior if the guest is using its assigned  processor(s) poorly.  A processor assigned to a  virtual will be reported by your host as completely pegged if the guest  is using it that way.

You may find similar usage if you have not assigned enough memory to the  vm.

Take a look at your system monitor when you have your vm running.  in the Processes tab, scroll down to the "V"s and see what percentage of you CPU(s) are being  used by VirtualBox. 

You might also try looking at the use of resources using the tools  withing the guest OS to see if it is using its resources wisely.

---

### Post by Ozymandias_117 on 2010-05-18
> **QIII said:**
> Forgive me if this is a bit basic, but I have no idea what your level of  experience is with VirtualBox...

First, with regard to 3D acceleration:
 
 It matters little what your host machine's video card is.  VirtualBox  uses a virtual card originally designed by the German company innotek  GmbH, but since taken over by Sun.  If you install Guest Additions, you  get a better virtual card with better performance.  To set 3D  acceleration, right click on the VM, select "Display" and toggle "Enable  3D Acceleration".  That may or may not allow you to use 3D acceleration  in Windows.

Is that checked?
 
With regard to processor usage:

 How many processors does your machine have?
  
  If you have a single processor and give that over to the guest in  VirtualBox, you  will likely get that sort of behavior if the guest is using its assigned  processor(s) poorly.  A processor assigned to a  virtual will be reported by your host as completely pegged if the guest  is using it that way.

You may find similar usage if you have not assigned enough memory to the  vm.

Take a look at your system monitor when you have your vm running.  in the Processes tab, scroll down to the "V"s and see what percentage of you CPU(s) are being  used by VirtualBox. 

You might also try looking at the use of resources using the tools  withing the guest OS to see if it is using its resources wisely.

My problem is the 2d and 3d acceleration boxes are grayed out. I do have proprietary drivers installed for Host's gfx card (Radeon HD 5770).

Host is Quad Core (Intel Core 2 Quad Q9550) Guest has 1 assigned to it.

As stated, System Monitor shows 90-108% of CPU usage (It looks as though System monitor will show 100% per core you have, so a quad core maxes at 400%, meaning VBox is using 1/4 of CPU power)

The guest is Windows XP... I have it running as efficiently as it's possible to make Windows ;) (Everything turned to Performance rather than looks, all unneeded services/apps turned off)

Edit: Sorry, missed the mention of RAM... I've assigned the VBox 1.5 Gigs out of my 4 gigs

---

### Post by Ozymandias_117 on 2010-05-18
Well... apparently there is a problem with my graphics drivers... glxgears reports "couldn't get an RGB, Double-buffered visual" and glxinfo says "couldn't find RGB GLX visual or fbconfig"... when I use lsmod I do see fglrx. Hmm...

---

### Post by Ozymandias_117 on 2010-05-18
Not sure what had happened to my drivers... No kernel updates or anything that would have needed me to reinstall them... But anyway, whatever it was is fixed now. This seems to have fixed both the excessive CPU usage and the 2d/3d acceleration problems. Sorry for wasting your time.

---

