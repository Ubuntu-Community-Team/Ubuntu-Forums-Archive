---
title: "Dual Boot vs VMWare vs VirtualBox"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2009-08-06
So I have a computer and I was dual booting Ubuntu and Windows XP.

Then I made a mistake and deleted some crucial windows system files (don't ask).  Now I need to reinstall Windows.

I know it's harder to install Windows after Ubuntu is already installed (because you have to keep Windows from writing over the Ubuntu partition, and then reload Grub when it's all over), and I'd rather not have to reinstall both of them.

The only thing I use Windows for is watching Netflix movies online, and playing a few games.  My computer isn't the newest, but the games I play aren't the newest either.

So what do you think would suit my situation better?  Dual boot, or virtualization?  And if you vote for virtualization, be sure to tell me if you prefer VMWare or VirtualBox, and why.

Thanks.

---

### Post by blur xc on 2009-08-06
I used this website's tutorial on how to dual boot vista and ubuntu, ubuntu installed first.  Went fine, was easy...restoring Grub was the easiest part.  Getting vista to see the partition I made for it was much harder, bot only took like 5min to figure out and get going.

[http://apcmag.com/howto_home.htm](http://apcmag.com/howto_home.htm)

They have step by step directions with screen shots all the way through, it's almost like having your hand held.  

good luck.

BM

---

### Post by blur xc on 2009-08-06
> **strAlan said:**
> Depends on your hardware specs, but take a look at mine and I'll tell you how my stuff works.  I run all versions of Windoze in Virtualbox and anything USB that has to be done in Windoze (like connecting my WM6 phone for putting audio files on it) works fine.  Sometimes when you connect a USB device that you want to use with the Windoze VM, Ubuntu will load a module and try to use that device for itself but that's easy to fix.  Virtualbox has 3d acceleration, so if you have enough video memory you can still run Counterstrike or graphics-equivalent games in the VM.  I've had no troubles using Wine so I rarely use the VM but I tested it just for kicks and I haven't had any problems.

Keeping Windoze in a VM is better because you can take a snapshot of the VM and practically destroy Windoze - delete all the critical files you want - and revert Windoze back to its original working condition with a couple clicks.  It's better to have a Linux-based host O/S because it is much more secure when browsing websites and thwarting malicious code from trying to execute on your machine.  There is no need to dual-boot, just keep Windoze in a VM.  XP seems to work best for Netflix.  Vista and above require so much memory that the sound & choppiness is intolerable.  I use Netflix in XP and it runs smoothly - Vista Netflix & sound are choppy.

I have relatively old hardware so if you're in that ballpark you should be able to do everything I do.  No need to dual boot - just keep Windoze in a VM.  You have to use MS Office?  Keep it in the VM.  When you get it fully installed, take a snapshot, and use that to restore if you ever have any problems.

but you take a pretty solid performance hit runnign a virtual machine.  You can't use all your ram (and if you don't have much to begin with, thats a problem) and you can't use all your cpu power.  Your host os is still running while your virtual machine is running, so you guest os get's whatever resources are left over.  In my experience, it also seems as though virtual box only uses one core of my dual core processor as well.  That's a big hit if you are doing somethign that requires a lot of hp.  Also, on my machine, it seems as though my usb ports only run at 1.1 speeds in my guest os.

ymmv.

right now, I do both, dual boot AND have a vista in virtual box.  I'll boot into virtual box when I need to do stuff that needs the performance of running natively.  I'll run the virtual machine for quickie tasks.  And for me, right now, Lightroom won't run in my virtual machine anyway- which is kind of the nail in the coffin for that right now.

BM

---

### Post by blur xc on 2009-08-06
> **strAlan said:**
> No, actually the o/s runs a lot faster in a VM.  Don't dual boot - keep it in a VM and like I said before - one-click restoration.  There's no need for a dual boot.

How?  I have 4 gigs of ram, 3.2 visibly by my 32bit os.  I only set 1.5 gigs aside for my vm.  When running vbox- my cpu usage is way up over 50% of at least on core at a time, the whole time.  It's just tied up.  How is that faster than running any os natively, with full system resources available to the os?

BM

---

### Post by Delever on 2009-08-06
It can't run faster in VM, never. Except for one thing - linux may cache your windows disk file in RAM automatically, so your programs load very fast.

---

### Post by Delever on 2009-08-06
> **blur xc said:**
> How?  I have 4 gigs of ram, 3.2 visibly by my 32bit os.  I only set 1.5 gigs aside for my vm.  When running vbox- my cpu usage is way up over 50% of at least on core at a time, the whole time.  It's just tied up.  How is that faster than running any os natively, with full system resources available to the os?

BM

It seems you have older version of virtual box. You can try these things: start very small secondary vm without disk and minimum RAM and see if CPU usage is still high (it's known bug). Or, install latest version of VBox which can use all host cores.

---

### Post by stoogiebuncho on 2009-08-06
Thanks for all the advice.  I think I'm going to try virtual box first and see if it can handle what I need it to.  If not, I'll try the tutorial Blur posted.

---

### Post by andrew.46 on 2009-08-07
Hi stoogiebuncho,

> **stoogiebuncho said:**
> The only thing I use Windows for is watching Netflix movies online, and playing a few games.  My computer isn't the newest, but the games I play aren't the newest either.

I have a deep suspicion that the problem with virtualisation with windows will be your games. I personally run VirtualBox with an XP guest but if I ever seriously considered gaming I would run a full dual boot so the games will have *full* access to *all* resources.

Andrew

---

### Post by blur xc on 2009-08-07
> **Delever said:**
> It seems you have older version of virtual box. You can try these things: start very small secondary vm without disk and minimum RAM and see if CPU usage is still high (it's known bug). Or, install latest version of VBox which can use all host cores.


thanks- I'll check that out as soon as I can.  I only installed it about 2 months ago, tops, and it's the puel version, but I don't recall what release it is.

BM

---

