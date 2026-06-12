---
title: "Ubuntu/Os X Virtualization Advice"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by palantir6er on 2011-02-26
So I'm a fairly new Ubuntu user and I'm upgrading my laptop to a Macbook Pro and considering a number of options for running Ubuntu alongside Os X (which I have no experience with). 
I have not used virtual machines like virtualbox, parallels, or vm fusion before so perhaps you guys could offer some advice on the best configuration from personal experience.

1) I could run Mac Os X with virtual Ubuntu via one of the above tools? (Which?)

2) Run Ubuntu :) with virtual Os X via one of the above tools?

3) Install both on separate partitions and use a virtual machine on each to access the other partition (Is this possible?). Is there a difference running say a virtual Os X from Ubuntu and running the Os X on the other partition as a virtual machine from within Ubuntu?

Let me know what you think or what your set up is and how you like it! Also which of the tools you use.

---

### Post by jeremyjjbrown on 2011-02-26
> **palantir6er said:**
> So I'm a fairly new Ubuntu user and I'm upgrading my laptop to a Macbook Pro and considering a number of options for running Ubuntu alongside Os X (which I have no experience with). 
I have not used virtual machines like virtualbox, parallels, or vm fusion before so perhaps you guys could offer some advice on the best configuration from personal experience.

1) I could run Mac Os X with virtual Ubuntu via one of the above tools? (Which?)

2) Run Ubuntu :) with virtual Os X via one of the above tools?

3) Install both on separate partitions and use a virtual machine on each to access the other partition (Is this possible?). Is there a difference running say a virtual Os X from Ubuntu and running the Os X on the other partition as a virtual machine from within Ubuntu?

Let me know what you think or what your set up is and how you like it! Also which of the tools you use.

You can do any of these.

Number 1 is the easiest to undo. So you could start there to get a feel for linux. Your Mac book pro will run a virtual linux machine with power to spare.

I recommend the non-free proprietary version of virtual box, because you can install host additions that will make moving between the two os's as painless as possible. There should be a 1000 tutorials online explaining the steps. If you don't like it, you can just ignore it or remove it with a few mouse clicks. I you like it you can move to dual boot. 

I personally multi boot with GRUB because I am a user/admin of win, mac and linux machines. But I regularly make virtual machines of both old and new os's for testing or to run tools that are no longer supported by new OS's.

---

### Post by josephmills on 2011-02-26
in order for us to tell which one is the best we need more info about you machine type in the following to the termanial and copy and past them here 
free -m
cat /proc/cpuinfo

---

### Post by Joeb454 on 2011-02-26
> **palantir6er said:**
> 
1) I could run Mac Os X with virtual Ubuntu via one of the above tools? (Which?)

2) Run Ubuntu :) with virtual Os X via one of the above tools?

3) Install both on separate partitions and use a virtual machine on each to access the other partition (Is this possible?). Is there a difference running say a virtual Os X from Ubuntu and running the Os X on the other partition as a virtual machine from within Ubuntu?


[list=1]
[*]Running Ubuntu as a VM under OS X is, as noted above, your easiest option. Personally, I'd go with VMWare Fusion, it's incredibly easy to use, and what I use on my MacBook. That said, however, it isn't free, and VirtualBox would likely do an equally good job,
[*]Running OS X in a VM is only supported if it's OS X Server. I tried running that under VirtualBox on Ubuntu, it didn't play nice at all.
[*]I'd try #1 before I tried this. Though you wouldn't need to create a Virtual Machine to access the partitions. You could create a 3rd partition to store data on, which could be read to by both OS's
[/list]

---

### Post by srs5694 on 2011-02-26
> **palantir6er said:**
> So I'm a fairly new Ubuntu user and I'm upgrading my laptop to a Macbook Pro and considering a number of options for running Ubuntu alongside Os X (which I have no experience with). 
I have not used virtual machines like virtualbox, parallels, or vm fusion before so perhaps you guys could offer some advice on the best configuration from personal experience.

You're getting slightly different answers based on peoples' experience, biases, etc. Before presenting my experience, I'll say that virtualization can work well for certain situations and uses, but it's got its limitations. These mostly relate to access to hardware, which is limited (at least, with the tools I've used, which include very old versions of VMware and newer versions of QEMU and VirtualBox). Virtual machines might provide no or limited access to video acceleration features, USB devices, underlying disk hardware (they typically use files as virtual disks), and unusual plug-in cards (not likely to be an issue for a MacBook). Network access can be virtualized in various ways, often including methods that make the virtual machine look like another computer on your network and others that hide the virtual machine and give it access only to its host or even no network access at all, so networking options are usually pretty good. You can usually get access to the DVD hardware. You'll lose some CPU speed, and the virtualized OS is likely to have less memory available than the host OS (although of course when the virtual machine is running, some of the host OS's memory will be gobbled up by the virtual machine).

> 1) I could run Mac Os X with virtual Ubuntu via one of the above tools? (Which?)

Yes, this will work. I've not used any of these under OS X, but I have used VirtualBox under Linux, and it runs every Linux distribution I've tried without problems.

> 2) Run Ubuntu :) with virtual Os X via one of the above tools?

Yes, but with caveats. Officially, only OS X Server is supported by VirtualBox. I'm not sure about the other virtualization packages. There are ways to get non-server versions of OS X running in VirtualBox, and probably the others, but they're contractually iffy, at best, since Apple only permits running the Server version of its OS in a virtual environment. (At least, that's my understanding; I've not studied the EULA in detail.) There's also the fact that the virtual environment, at least under VirtualBox, doesn't exactly match any Apple hardware, so you may run into problems related to these differences.

> 3) Install both on separate partitions and use a virtual machine on each to access the other partition (Is this possible?). Is there a difference running say a virtual Os X from Ubuntu and running the Os X on the other partition as a virtual machine from within Ubuntu?

If I understand correctly, you want to set up a dual-boot environment in such a way that you can switch between directly booting each OS and running it in a virtual environment. Although this is theoretically possible, it can cause problems because the real and virtualized hardware environments won't exactly match. I'm not sure how OS X would react to this, but I suspect it wouldn't handle it too well. Ubuntu would probably do a better job of it, but I can't say I've tried this. I know that Windows will flake out completely if you try this with it.

A compromise could be to set up a partition in which to store programs and/or shared data files. You could then install an OS both directly on the computer and in a virtual environment, and give the virtual environment access to the shared-data partition in one way or another. (In VirtualBox, I think this would be easiest via network file sharing tools, but there might be a way to feed it a device file for more direct access.) This approach will minimize the disk space wasted by keeping multiple installations, since you'll keep the shared data files just once on a single partition. Both OS X and Ubuntu install in 5-20 GB of space, so keeping both real and virtual installations needn't consume all that much disk space, by modern disk size standards, particularly if you're happy with fairly basic installations.

---

