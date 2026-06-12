---
title: "Virtual Machines?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by mills1987 on 2009-06-24
Hi,

I have decided to try the transition from my Windows XP OS to Ubuntu Jaunty Jackalope. These have been installed on separate partitions of the same HD as per the recommended method. However is there a way of being able to run/access the other OS without having to reboot the computer. As I'm only easing myself gradually into linux. I've heard of virtual machines but I am not entirely sure whether they will meet my needs.
Anyone got any ideas/recommendations

Cheers

---

### Post by ainsworth_t on 2009-06-24
There is no way to access either operating system from the other. Virtual Machines are a viable option for easing into Linux, but it depends on what your needs are. If you are trying to run Windows programs in Linux, VMs or Wine are good options. If you are just trying to access files of one OS from the other, then you need to look into compatible file systems (FAT32 is about the only one).

If you are just starting with Virtual Machines, I would check out [VirtualBox ]("http://www.virtualbox.org")or [VMware]("http://www.vmware.com/products/server/"). Both can be installed on either Windows or Linux and support installation of multiple types of Guest Operating Systems.

---

### Post by Polaris96 on 2009-06-24
If you want simple, try win4lin.  You have to pay $35 for it but it's very simple to install and run.

If you want to go opensource, I think VMware is a good choice but I like Xen best.  To use either of them for windows, you need a multicore processoer, though, because windows needs "more" virtual abstraction than another unixbased / opensource OS.  

There are a few good websites for this stuff - I'll look them up and post them for you when I get time.

---

### Post by Gaweph on 2009-06-24
What exactly are you trying to achieve?

As stated by "ainsworth_t" you can install wine and you will be able to run many windows applications from ubuntu.

If you want to run a virtual machine then vmware nad VirtualBox are both viable options (need around 1GB spare of ram to efficiently run a virtual machine of windows).

A virtual machine is basically windows running in a box, when your in ubuntu, and you run windows in a VM you will see it in a box just liek any othe rapplication.

If you just mean, can you access your windows files from ubuntu, then sure you can.  If you go to Places (at the top) then you should be able to mount your Windows drive.

To Summarize:

Install Wine (just open add remove programs, and type Wine) if you want ot runs a few windows programs (or look for ubuntu equivalent ones).

Install VirtualBox/VMWare if you really want to run a virtual machine of windows.

You can easily see your windwos files if thats what you meant

---

### Post by mills1987 on 2009-06-25
Cheers,

Just to clarify i was not talking about the file storage kind of things.

Basically what i'm trying to achieve from Linux is a platform that i can run a variety of Analysis/computation programmes on with the maximum of system resouces at my disposal. However quite frequently i need access to Windows to run other programmes which are only ported in windows. Therefore the abilty to run both OSs concurrently would be a bonus.

I have heard of WINE but was under the impression it still has a long way to go before being totally usable, and i have doubts it would support some of the programmes i use.

In addition and possible the solution lies with VMs etc,  is there a way of playing .mp3 etc within ubuntu? can this be done in a VM?

Thanks again

---

### Post by Zzl1xndd on 2009-06-25
I would suggest using VirtualBox, as long as the Tools you use  don't need 3D support you should be fine. 

You can play mp3s in Ubuntu. Just make sure you have the Codecs installed.

---

### Post by brettg on 2009-06-25
It is possible to dual boot Windows and Linux AND also boot the same Windows partition virtually using vmware workstation, but it is a bit tricky to do and can become problematic if you are using XP on new hardware. 

I am currently doing just that with the Win7 RC.

---

### Post by bodhi.zazen on 2009-06-25
You can boot physical partitions with KVM as well.

It is probably easiest to boot ubuntu on Virtualbox or VMWare from windows then the other way around (if you boot windows in a VM it will complain the hard ware has changed ... so if you wish to do this, follow a how to).

---

