---
title: "VirtualBox Alternatives?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-07
Just wondering if theres other good VM software out there for ubuntu?

Any recommendations?

---

### Post by cb951303 on 2009-03-07
> **Gp. said:**
> Just wondering if theres other good VM software out there for ubuntu?

Any recommendations?

kernel team supports KVM.
you may need to use console for this but believe me it's very easy to setup.

---

### Post by DGortze380 on 2009-03-07
> **Gp. said:**
> Just wondering if theres other good VM software out there for ubuntu?

Any recommendations?

Just out of curiosity, is there a particular problem you're having with virtualbox? Maybe we can help. I find it to be very intuitive and full featured.

---

### Post by Eversmann on 2009-03-07
There are lots of them: QEmu, Parallels, VMware (the most popular), and like the mate said, Kernel virtual machine (KVM), Xen...

I use virtualbox on almost every machine i need a virual os there, and for servers, vmware server.

Parallels became free recently (if i'm not wrong).

but for recomendation, virtualbox is more than enough. Maybe you can have problems with USB, but are easy to fix since Intrepid.

---

### Post by binbash on 2009-03-07
vmware is a good alternative

---

### Post by Gp. on 2009-03-07
The only thing I don't like about Virtualbox, is the fact I can't change the partition sizes without alot of work copying over the older partition to a new one.

---

### Post by DGortze380 on 2009-03-07
> **Gp. said:**
> The only thing I don't like about Virtualbox, is the fact I can't change the partition sizes without alot of work copying over the older partition to a new one.

It appears you are correct, however, you could create a new VDI and add it as a Slave to give you additional space.

---

### Post by smooch101 on 2009-03-07
vmware might work under wine

---

### Post by Gp. on 2009-03-07
> **DGortze380 said:**
> It appears you are correct, however, you could create a new VDI and add it as a Slave to give you additional space.

Nah, I need it primary.

And there is VMware for linux, so I'm going to try that. :)

---

### Post by Chan on 2009-03-07
I installed VirtualBox, and found it pretty easy to install, (after several attempts).  The greatest challenge  was figuring out the format and source of the guest operating system, Kubuntu.  After getting that straightened out, Kubuntu signed on pretty quickly, but then, my display went screwy.  I have yet to determine whether I need to make  some settings corrections in Kubuntu, Orrr, do I need to uninstall the Wubi that I was running with previously, (with its built-in Grub).  Anybody else run into this set of problems?  I want to be able to shift back and forth between Vista and Kubuntu, without having to reboot each way........Chan

---

### Post by cwmoser on 2009-03-14
The only virtualization I have used is VMWare - both VMware Server and Player.  I like the speed and easy of use of VMware player.

I run a virtualized instance of Windows XP on my Ubuntu 8.04 host workstation and am very pleased with the performance.  My physical hardware is an AMD 64 X2 6000+ with 4GB Ram.

Anyone have perceptions on performance VMware as compared to Virtual Box and KVM?

Carl

---

### Post by KayakJim on 2009-03-14
> **cwmoser said:**
> Anyone have perceptions on performance VMware as compared to Virtual Box and KVM?

Carl

[This]("http://www.techthrob.com/2009/03/02/virtualization-in-linux-a-review-of-four-software-choices/") article might be of some help to you.

On a personal note, I have been using VirtualBox for over 4 months to run WinXP Pro SP3 and have encountered no problems. Performance is fast (for Windows), games play without issue, and everything is usual. It has even made me realize how much I appreciate Ubuntu and how much I do *not* miss Windows. I would not even run it except for testing purposes.

---

### Post by tekkieguy on 2009-03-14
I love VM server.

ITS the bomb!

---

