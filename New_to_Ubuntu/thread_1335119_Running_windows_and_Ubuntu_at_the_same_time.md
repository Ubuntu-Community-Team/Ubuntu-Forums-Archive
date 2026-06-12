---
title: "Running windows and Ubuntu at the same time"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by X Zeater X on 2009-11-23
Hey guys, I'm currently using a dual boot setup with windows 7, and  wubi running ubuntu on the side.
I was wondering if it's possible to control the ubuntu side of things while logged in on windows 7, without having to restart every time I want to switch?
Know what I mean?:KS

---

### Post by overdrank on 2009-11-23
Hi and welcome. I believe the only way to do this is with a [virtual machine]("http://www.virtualbox.org/").

---

### Post by Uluru on 2009-11-23
[http://www.virtualbox.org/](http://www.virtualbox.org/)
Installing VirtualBox onto your HOST OS Win7, you can then install Ubuntu as a Guest OS within VirtualBox. To change over to Ubuntu from Win7 to Ubuntu is simply a matter of starting the program VirtualBox, and starting Ubuntu. The main problem is that you need enough resources, RAM, CPU, to run Win in the background as a HOST, and Ubuntu on top as the Guest. Basically a computer that can run Win 7 should do this with ease, minimum 512 MB RAM.

---

### Post by X Zeater X on 2009-11-24
Ok thanks, I have 2gb RAM, so that should be good right?

---

### Post by bumanie on 2009-11-24
Virtualbox is probably the easier to set-up, but there is also a program called qemu that will let you run linux on top of windows and you can switch between the two OSes at will. Qemu is not the quickest thing around, but it can be booted off an external hard drive and thus used on any windows computer where ever you are.

---

### Post by X Zeater X on 2009-11-24
Ok, I did the VirutalBox thing, and I get this..
[IMG]http://i47.tinypic.com/2u61oxu.png[/IMG]
I'm not sure what to do, because my C drive isnt in the drop down box,
it gives me the option to partition it, but I don't know how...
Help please..

---

### Post by jocko on 2009-11-24
> **X Zeater X said:**
> Ok, I did the VirutalBox thing, and I get this..
...
I'm not sure what to do, because my C drive isnt in the drop down box,
it gives me the option to partition it, but I don't know how...
Help please..
The virtual machine will not see your c:\ drive, it only sees the virtual disk that you created (which is a 8 Gb file stored in your windows partition). Just let the partitioner set things up automatically (that's the "erase and use entire disk" option).

---

### Post by X Zeater X on 2009-11-24
Ok, I see my D drive under the erase and use entire drive option, which the drive is too small anyway.

So I clicked partition manually, I get this:
[IMG]http://i48.tinypic.com/nz0d2x.png[/IMG]
I'm not sure how to do it.

---

### Post by ad_267 on 2009-11-24
No, those aren't your actual hard drives. They're virtual disks.

You want to select the "erase and use the entire drive" option.

Another option you might consider is using Portable Ubuntu, which has a similar effect to using a virtual machine but works quite differently.

---

### Post by X Zeater X on 2009-11-24
[IMG]http://i49.tinypic.com/qx6kph.png[/IMG]

All that comes up is my D:// Drive, and I don't want to erase all of the stuff on it..
I'm not entirely sure I'm getting all of it, could you tell me what happens if I click Erase and Use the ENTIRE Disk?

---

### Post by blazemore on 2009-11-24
OK I don't think you understand the fundamentals of virtualisation.

A virtual machine allows you to run one operating system inside another. You install the "guest" operating system onto *virtual* hardware, that is, the "hard disk" it sees is actually just a file. You can see it, at /home/username.virtualbox

While there are ways of installing a virtual OS onto "real" hardware, they are unsupported and not recommended (certainly not by me anyway!)

So you should choose Erase Entire Disk.

---

### Post by X Zeater X on 2009-11-24
Thanks man, I understand now.
Installing now(;

---

### Post by X Zeater X on 2009-11-24
Ok, Now I run the installation fine, but after it's completed my whole win7 system goes MEGA slow, almost completely freezing, I manage to click the restart now button after the ubuntu installation, but it's so laggy I have to restart my comp and it's back to normal, but the installation seems to not of taken place? After running start again in VirtualBox it comes back up with the same setup screen..
I allocated it 500mb of RAM out of my 2GB.
Help?

NVM, FIXED.

---

