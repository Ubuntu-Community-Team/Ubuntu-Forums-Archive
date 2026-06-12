---
title: "Windows program in ubuntu.."
date: 2011-02-15
forum: New to Ubuntu
---

### Post by art_monu on 2011-02-15
I am using Ubuntu 10.04 LTS desktop edition. I use a program called "Test Room" provided by my institute.. it is a program to take the test online  from your home. It requires Microsoft Dot Net framework 2.0 and some other things to run on windows which are included in the CD with the main program itself. Is there any way to run that program on linux? I have heard about virtualisation.. but do not know much and never used it. Please tell me how can I use that program on Ubuntu.. because that's the only thing stopping me to make a complete transition to Ubuntu.

thanks in advance!!!

---

### Post by Paqman on 2011-02-15
Virtualisation is the process of creating a virtual PC on your machine. It creates a set of virtual hardware (actually built totally out of software) which presents itself as if it were a real computer. You can therefore install an operating system into the virtual machine, and the OS will think it's installed on an actual machine.

So all you need to do is:
[LIST=1]
[*]Install Virtualbox. It's in the repos, but if you need to use USB or remote desktop you should use the non-open source version from the Virtualbox website.
[*]Installing the "guest additions" is highly recommended
[*]Create a new virtual machine in Virtualbox
[*]Install a copy of Windows into the VM
[*]Set the VM up just like you would a real one ie: install antivirus, etc.
[*]Install your Test Room app onto it
[*]You will now be able to start up and shut down Windows as if it were an application on your Ubuntu desktop.
[*]Enjoy!
[/LIST]

You will need to have a reasonably powerful machine to run a VM well. You'll have to dedicate a chunk of RAM to the VM, how much will depend on what version of Windows you want to run. I would recommend Win XP with 512MB or 1GB RAM if you have a valid licence available for it. A dual-core or better PC will also run VMs better than a single-core one.

---

### Post by Souptik on 2011-02-15
> **art_monu said:**
> I am using Ubuntu 10.04 LTS desktop edition. I use a program called "Test Room" provided by my institute.. it is a program to take the test online  from your home. It requires Microsoft Dot Net framework 2.0 and some other things to run on windows which are included in the CD with the main program itself. Is there any way to run that program on linux? I have heard about virtualisation.. but do not know much and never used it. Please tell me how can I use that program on Ubuntu.. because that's the only thing stopping me to make a complete transition to Ubuntu.

thanks in advance!!!
Hello, have you tried wine ???? It lets you use windows applications on linux... But there's a catch.. I do not think softwares which are not too popular will run using wine...

---

### Post by Souptik on 2011-02-15
> **Souptik said:**
> Hello, have you tried wine ???? It lets you use windows applications on linux... But there's a catch.. I do not think softwares which are not too popular will run using wine...
I believe Paqman's method is better.....

---

### Post by Paqman on 2011-02-15
> **Souptik said:**
> I believe Paqman's method is better.....

Depends. If your software happens to work well in Wine, then that's the easy way to go. That's a really big if though...

---

### Post by Mark Phelps on 2011-02-15
Anything that needs a recent version of .NET working in Wine -- is almost certainly NOT going to work.

Look at the WineHq page below for .Net Framework:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586")

As you can see, the .Net versions newer than 2006 are rated GARBAGE!

---

### Post by art_monu on 2011-02-16
thanks for all replies. I am using virtualisation..

---

### Post by mastablasta on 2011-02-16
funny how they didn't provide free copy of windows as well...

---

### Post by hansolo4949 on 2011-02-17
I would try using wine to run the program first, since unless you have a pretty fast system, a vm will run like molasses. Windows programs usually work in Wine, except for games, which require a bit more effort on the emulations' part to work properly. If Wine does not work, yes, you should go with a VM, regardless how slow it is. Good luck!

---

