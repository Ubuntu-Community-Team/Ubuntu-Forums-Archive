---
title: "virtual box no bootable medium"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by halfstrike on 2009-10-07
I installed virtual box and set up the VM everything seemed in order then when i tried to run the VM with vista i get a black screen that says "no bootable medium found.

I dont know what to do.

---

### Post by mharrison on 2009-10-07
> **halfstrike said:**
> I installed virtual box and set up the VM everything seemed in order then when i tried to run the VM with vista i get a black screen that says "no bootable medium found.

I dont know what to do.

Were you trying to install with a Vista CD?  If so, did you make sure to mount the CD Rom drive within VirtualBox so that it would try to boot to it first?  Also you can try hitting F12 when VirtualBox first boots the VM and selecting the CD Rom drive to boot from.

---

### Post by Mobil1 on 2009-10-07
Hey! I used VBox quite a while ago and installed XP. As I remember you name the machine and then when you boot it is asks for the bootable medium, which I think is the stage your at?
Anyway as I remember your Vista Installation CD is the "bootable medium" so insert it and select CD from the options. It then performs an install for you just as if you were installing it to your hard drive. Hope this helps :popcorn:

---

### Post by halfstrike on 2009-10-07
> **mharrison said:**
> Were you trying to install with a Vista CD?  If so, did you make sure to mount the CD Rom drive within VirtualBox so that it would try to boot to it first?  Also you can try hitting F12 when VirtualBox first boots the VM and selecting the CD Rom drive to boot from.

I didnt use any CD's I just followed the prompts to setting it up that you get from the program.

---

### Post by mharrison on 2009-10-07
> **halfstrike said:**
> I didnt use any CD's I just followed the prompts to setting it up that you get from the program.

That might be your problem then....You have to install the operating system to run on the VM.  The list of operating systems just helps you with some recommended default settings for that operating system....for instance...if you select Vista, it reserves more RAM and creates a larger hard drive than if you selected XP.

---

