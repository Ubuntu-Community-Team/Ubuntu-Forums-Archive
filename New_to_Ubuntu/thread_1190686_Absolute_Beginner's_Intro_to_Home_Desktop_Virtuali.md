---
title: "Absolute Beginner's Intro to Home Desktop Virtualization"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-06-18
I've used Linux for a year now but not everyone in the house is comfortable it yet. Dual-booting worked reasonably well but isn't ideal. 1st, when Windows is on I can't access files on the computer or ssh etc. 2nd, they'll never learn anything about Linux if they always dual boot into windows, but they'd be happy enough to try it out & if something doesn't work they way they're used to they escape quickly & easily to Windows.

System Info: Ubuntu 9.04 on Athlon X2 2.5 GHz with virtualization tech enabled in BIOS. 1 SATA hdd with Ubuntu, 1 IDE hdd with XP SP3. 2 GB DDR2 Ram. ATI Radeon 4670.

I'll try KVM first since it's the 'official' Ubuntu virtualization app. If I'm not happy with it I'll try to figure out VirtualBox later, maybe once version 3 comes out. I'm mostly interested in KVM right now, but if there's a big difference between that & Virtualbox it might be nice to know.

The virtualization sections has lots of answers for specific problems but I didn't find answers to these introductory noob questions:

Can I load the OS that I've been dual-booting, or do I have to do a fresh install within KVM to make it work?

[related] Will the guest OS be able to read/write files & run programs that are currently installed on the XP SP3 hdd?

Will video card, motherboard, webcam etc. drivers work as in Windows, or will they only work at best as well as they work with the host OS's drivers? (Windows needed drivers on cds while installing, otherwise it went kaput) Should I be able to print from either OS?

If windows is running on its hdd will I still be able to move files between disks from Ubuntu as I do now, or does the fact that windows is running on the disk cause problems? (I saw a lot about sharing files, special shared folders, samba networking etc... why is that necessary? Can't I just be using windows, jump back to linux to copy something from ext4 to ntfs, then jump back?)

For what I imagine are my pretty basic 'mostly defaults' virtualization needs (I'm not building a web server or data farm here), can I get started fairly intuitively with KVM & its GUI, virt-manager, or do I have to spend 3 hours reading about command-line options?

What risks do I face? (Specifically, when a noob is trying to set this up, what are the chances he/she'll wipe a hard drive without seeing a big fat warning first?)

What kind of graphics performance can I hope for? (e.g. would something along the lines of far cry 1 still be playable on this computer, maybe after a tweak or two? What about video playback or flash, which intermittently stink with fglrx?)

How seamless is switching from one OS to the other? (after it's booted the first time) Is the guest put in a window that I can resize & put in a corner if I like? Could I somehow move it to tty6 so that I do ctrl-alt-F6 & I'm in the guest OS? How does that work?

Anything else I ought to keep in mind about virtualization?

That's it, thanks!

---

### Post by kendoori on 2009-06-18
I have slowly migrated from Windows XP to Ubuntu, first by running WUBI, then via dual boot (still alive but not using it much), and now with XP running virtualized as a guest under 9.04 using Virtualbox. 

As someone previously green about all of this, Virtualbox was not in the least bit difficult to figure out, and the "seamless model" makes using both OS at the same time, well, seamless (or close). I did experiment with virtualizing my existing XP install using [VMWare's converter]("http://www.vmware.com/products/converter/"), but eventually chose to start from scratch. There are apparently some tricks to doing this (disabling hardware specific references), so I might try this again at some point. BTW, the VMWare machine could be played back on Virtualbox.

I find that my clean XP install works very well as a guest. Actually quite amazing to have a complete OS install that's portable and not tied to hardware.

I'm not sure it's supported on your hardware, but you may want to explore [VMWare's ESXi]("http://www.vmware.com/products/esxi/"), which is a bare metal hypervisor that would load ahead of your various OS.

---

### Post by clive littlewood on 2009-06-18
Hi

I use Virtualbox to run XP for my ONLY windoze program itunes.

If you go with Virtualbox make sure you use the Sun site download and not the OSE version in the repos.

The repo version does not give you USB support.

Not sure if that is the same for the windows download !!!!

Hope that helps

Clive

PS. Also remenber that you will never get the same performance as a dual boot.

---

### Post by corstar on 2009-06-21
> **clive littlewood said:**
> 

The repo version does not give you USB support.



Just FYI, you should clarify that it's "usb over a network" that's not included in the OSE version.
Can you imaging not having any usb support in vbox; how pointless would that be.

---

### Post by clive littlewood on 2009-06-21
Hi

Perhaps it's me !!!!

But I did NOT have any USB support in the OSE version

Sorry

Clive

---

### Post by andrew.46 on 2009-06-21
Hi clive,

> **clive littlewood said:**
> Perhaps it's me !!!!

But I did NOT have any USB support in the OSE version


No it is pretty much everybody :-). The details can be seen here:

Open Source VirtualBox and other editions
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Mind you I also use the OSE version and I access simple USB devices such as memory sticks and usb hard drives by accessing a link I have placed in the shared folder. Thus the sequence is:

Guest System ---> Link in Shared Folder ---> Points to USB drive in Host system.

Andrew

---

