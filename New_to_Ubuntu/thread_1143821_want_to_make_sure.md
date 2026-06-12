---
title: "want to make sure"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by circusmonkey on 2009-04-30
I am looking for advice , before I install ubuntu as I dont want to wreck my machine.

1 I have windows vista64 installed on one HD , boots fine.I have bought a spare disk and formatted it for ubuntu. I have been reading people do this and then in the bios , they can change the boot order of the 2 disks to either install vista or ubuntu.

I unplugged my vista disk , change the boot order in the bios to get my new disk to boot first, added the unbuntu disk , but all I kept getting was the "error 21" message. 
I have read this is windows boot info , I find it weird I get this as my disk is new and its never been near linux. 
What should I do to get a clean safe install 

r

---

### Post by Niniel on 2009-04-30
In order to dual-boot Windows and Linux, there is no need to unplug anything or to mess around with settings in the BIOS. Just plug in your second hd (no need to format, either), install Ubuntu to it - make sure you pick the correct disk! - and also install the Grub boot manager into the MBR of the _first_ disk. In most cases, this works flawlessly and Grub will autodect Windows and configure itself accordingly.
To install Ubuntu, the easiest way would be to use the live CD.

---

### Post by Mark Phelps on 2009-04-30
OK, so I agree that there is no need to unplug anything -- but I prefer to mess with the MS Windows stuff as little as necessary.  So, I unplugged the MS WIndows disk, installed Ubuntu on the other one, changed to boot from the Ubuntu disk, added a stanza to the menu.lst file for MS Windows.

This way, I made sure that I did not overwrite the MBR of the MS Windows disk.

But, as already said -- you don't need to do this.

---

