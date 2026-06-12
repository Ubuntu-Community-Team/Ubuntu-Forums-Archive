---
title: "How can I run windows vista directly off a windows partition useing vmware?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by cosmoshell on 2011-08-05
a long time ago i ran windows xp off a partition and i cant seem to do this again with windows vista.

---

### Post by haqking on 2011-08-05
> **cosmoshell said:**
> a long time ago i ran windows xp off a partition and i cant seem to do this again with windows vista.


you can do it with virtualisation if thats what you mean ? like vmplayer etc.

see here

[http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699)

you can alos convert an existing partition into a virtual machine for use etc if you wanted to

---

### Post by Sef on 2011-08-05
Virtual Box is in the repositories, so it is an easy download.

---

### Post by haqking on 2011-08-05
> **Sef said:**
> Virtual Box is in the repositories, so it is an easy download.

Virtual box being the best tool of course, though i am not sure if using Virtual box you can rnu an already existing installed OS on a partition ? or can you.

i know you can convert an existing install for use within a VM but didnt know if you could use VB for running an existing partition which i think is what he asked ?

the one in the repos is old too, best get latest here at [www.virtualbox.org](www.virtualbox.org)

---

### Post by anewguy on 2011-08-05
It is possible with virtualbox to run an existing stand alone installation in a VM.  However, it's not recommended.  I went against the advice given me a few years ago and did this.  It results with Windows wanting to re-register and also find a lot of hardware due to the VM, and you can't go back and just boot a stand alone installation after you have opened it directly in a VM.  I got LOTS of errors and the end result was that Windows wouldn't boot again either way.

You take a terrible chance on some sort of failure messing up your disk whereas a virtual disk created by a VM is just a file.

If you insist on taking the chance, look in the help supplied with virtualbox and the vboxmanage parts - that's where the info on how to do it used to be.  Just be forewarned - my Windows installation got really messed up doing this and I eventually had to reinstall Windows.

Dave ;)

---

### Post by bhaverkamp on 2011-08-05
You can go back to the physical world if you keep two different hardware profiles which was supported by XP and I believe is still supported. Then when you need to tweak windows multiboot menu to boot using the different configurations. I echo Haqking's recommendation however that it is not a good idea. Too many opportunities to really frak things up. However if you succeed it works great. If your going to try I would recommend to do an image backup of your windows partition first so that you can restore it should you break things along the way.

---

### Post by cosmoshell on 2011-08-11
I keep getting a blue screen after booting up windows threw vmware.

---

### Post by fqowehf on 2011-08-11
try enabling PAE/NX, 3d video acceleration, 2d video acceleration, and add at least 512 MB of RAM.

---

### Post by Paqman on 2011-08-11
> **cosmoshell said:**
> I keep getting a blue screen after booting up windows threw vmware.

I'm not surprised, it's a hack, and not really how you're supposed to use VMs. If you want to have Windows running on both bare metal and a VM, you should use two copies of Windows. Unless you've got a VLK that means you'll have to buy a second license.

---

### Post by cosmoshell on 2011-08-12
> **NullCity said:**
> try enabling PAE/NX, 3d video acceleration, 2d video acceleration, and add at least 512 MB of RAM.

how do i do this?

i see accelerate 3d graphics checked, but i dont see the other ones.

also this is the screen i get.[IMG]http://i.imgur.com/T5GTP.png[/IMG]

---

