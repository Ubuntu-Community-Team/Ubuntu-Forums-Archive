---
title: "VirtualBox to run dual-boot XP?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-24
Quick yes or no answer required...

If I'm dual booting XP and Intrepid, can I use VirtualBox to load and access my existing XP install? I've installed VB and had a quick go through the wizard to try and find my XP install but am not really sure what I'm looking for.

Am getting a bit tired of having to log out and restart to use iTunes etc so using my XP machine within Ubuntu would be just the ticket.

---

### Post by albandy on 2009-03-24
yes it is possible, but you need to create a special vdi that will connect to your hard disk, so it's a bit dangerous.

also you need to create a new hardware profile in XP

---

### Post by albandy on 2009-03-24
I found this
VBoxManage internalcommands createrawvmdk -filename .VirtualBox/VDI/WinXPraw.vmdk -rawdisk /dev/hd[a..z] -partitions [1..9] -relative

from this post: [http://forums.virtualbox.org/viewtopic.php?t=1404](http://forums.virtualbox.org/viewtopic.php?t=1404)

---

### Post by Nostalos on 2009-03-24
Have done it myself.   Works decently,  however Windows will complain about registration when you switch from Vbox to real boot.

---

### Post by blazemore on 2009-03-24
It can be done but I'd recommend using hardware profiles because Windows doesn't like booting into different hardware each time.

I did this but it takes a lot of setting up from the Virtualbox end, if I remember rightly.

---

### Post by GepettoBR on 2009-03-24
If you have the HDD space to spare, }I'd reccomend installing a different XP exclusively in Virtualbox. This eliminates the problems associated with running the same installation on VB and locally.

---

### Post by binbash on 2009-03-24
Yes but you have to convert it.BUT they will be different OS, they do not affect each other.

---

### Post by kyalee on 2009-08-09
> **binbash said:**
> Yes but you have to convert it.BUT they will be different OS, they do not affect each other.

I apologize for the thread hijack. Does this mean that if I load my XP partition though VirtualBox, the work I do in the VirtualBox won't be there if I load XP normally through the boot menu?

---

### Post by GepettoBR on 2009-08-09
> **kyalee said:**
> I apologize for the thread hijack. Does this mean that if I load my XP partition though VirtualBox, the work I do in the VirtualBox won't be there if I load XP normally through the boot menu?

The work will be there. However, you may encounter several problems because Windows will essentially think you're taking the hard drive and sticking it into a different computer all the time. So to avoid potential crashes, you'd have to do a few workarounds (like setting up a different hardware profile in the Device Manager).

I dual-boot, but I keep a virtual machine with XP that I can activate from both Ubuntu and my actual XP install. It's treated like just another machine on the network, so I use it for all my interchangeable tasks, and it's much easier than accessing the actual XP partition in VirtualBox.

---

### Post by mrgreggie on 2009-08-09
Not that I've done it, but I think the Windows Product Activation system would flip out if you tried to access it via VM.

---

