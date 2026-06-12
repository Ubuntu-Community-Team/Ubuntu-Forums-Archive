---
title: "Setting up a Windows window inside Ubuntu"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by asharpham on 2010-01-30
When first being introduced to Ubuntu I used wubi to set up Ubuntu on my Windows drive just to try it out. I've become totally committed to using Ubuntu as my default OS but I still need to keep Windows for some of the programs I can't run under linux.

I have installed Ubuntu on a 16Gb thumb drive and it all works wonderfully well. My BIOS is set to read USB first so if the thumb drive is there, it brings up the various selections including Windows. If the thumb drive is not there, I get a grub error. That doesn't bother me at the moment as long as i don't lose the thumb drive!

My question here concerns running Windows inside an Ubuntu window so I don't have to log off Ubuntu and relog into Windows (using restart and selecting Windows when the boot menu comes up again).

I understand it is possible to set this up but have no idea how to. Can anyone point me towards instructions on how to do this? Remember, it is not dual boot I am after as I basically have that now with the boot menu. I want to be able to go straight to Windows while still in Ubuntu - not have to restart.

Alan.

---

### Post by howefield on 2010-01-30
You are looking at something like Virtualbox.

Have a read here and watch some of the short video tutorials.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Then ask any questions you have.

---

### Post by NightwishFan on 2010-01-30
I would advise you install on a normal harddrive. Flash drives are not meant for such constant use I would think, besides performance would be better on a normal disk.

Please note that you will need a valid Windows install CD to use Virtualbox. It does not load your installed Windows, you will need to reinstall everything, and be able to activate Windows.

If you lose your thumb drive, you can repair the Windows boot loader using the SuperGrubDisk.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by asharpham on 2010-01-30
Thanks so much for pointing me towards this helpful document. I am in the process of reading it and have downloaded and installed Virtualbox. But it's not appearing in my Applications menu. I notice it's placed in the System Tools menu but this menu doesn't show up under Applications. Everything is correctly ticked but there is nothing between Sound & Video and Wine.

Alan

---

### Post by tom.swartz07 on 2010-01-30
> **asharpham said:**
> Thanks so much for pointing me towards this helpful document. I am in the process of reading it and have downloaded and installed Virtualbox. But it's not appearing in my Applications menu. I notice it's placed in the System Tools menu but this menu doesn't show up under Applications. Everything is correctly ticked but there is nothing between Sound & Video and Wine.

Alan


Also, You might find it interesting to take a look at this:
[http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)

You can run Ubuntu as a program RIGHT INSIDE windows, on top of everything. Its definitely worth a shot.

Hope this helps!

---

### Post by HermanAB on 2010-01-30
Howdy,

I'd suggest Virtualbox or Vmware Player.  Virtualbox is slightly easier to install.  VMware has the advantage that USB works.

I'm running VMware Player with a Windows 2003 Server and XP Pro VMs on my ancient little Eee PC 701 netbook and use it on a daily basis.  It works really well.  On an Eee PC everything is solid state, so don't worry about using memory sticks heavily - they work until you drop them on the floor and step on them or something.  My /home directory is on a 16GB SD camera card.

The the 'Virtualization' sub forum - lots of activity there.

---

### Post by Merk42 on 2010-01-30
Two important bits of information.
1. What are the specs of your computer? 
You need a bit of a good system especially in RAM since it'll be running both Ubuntu and Windows at the same time.
2. What are you planning to do in Windows?
3D Support is experimental at best, also some applications I'm sure you know by now, may have a native linux equivalent or be runable in WINE.

So far you really should install Ubuntu to the drive.
Then you'd have to REINSTALL WINDOWS FROM SCRATCH in Virtualbox ([this technically isn't required](http://forums.virtualbox.org/viewtopic.php?t=9697), but is much easier)

> **HermanAB said:**
> Howdy,

I'd suggest Virtualbox or Vmware Player.  Virtualbox is slightly easier to install.  VMware has the advantage that USB works..

[Virtualbox PUEL version](http://www.virtualbox.org/wiki/Downloads) from the website works with USB.

---

### Post by asharpham on 2010-01-30
I'm running a Dell Inspiron 6400. The HD is almost full with Windows stuff - that's why I loaded Ubuntu on the thumb drive. I'm loathe to reinstall Windows only because of the amount of work involved. However, if this is the only way to do it, I may have to rethink.

Thanks for everybody's help. I'll consider the various options before making a decision.

Alan

---

### Post by C.S.Cameron on 2010-01-30
I would not worry too much about bricking your thumbdrive running Ubuntu from it. 
A flash drive is good for at least ten thousand writes, that is like filling a 16GB drive with data then deleting the contents continuously eight hours a day for a year.
I have never actually heard of any one killing one from running too much Ubuntu.
One of mine is over two years old and I run Ubuntu from it a lot and I have Vbox installed running XP Pro with Autocad, Rhino 3D and SketchUp.

---

### Post by warfacegod on 2010-01-30
> **asharpham said:**
> Thanks so much for pointing me towards this helpful document. I am in the process of reading it and have downloaded and installed Virtualbox. But it's not appearing in my Applications menu. I notice it's placed in the System Tools menu but this menu doesn't show up under Applications. Everything is correctly ticked but there is nothing between Sound & Video and Wine.

Alan

Did you put a check next to the System Tools menu itself?

---

### Post by asharpham on 2010-02-10
It's showing up under Accessories. I was looking in the wrong place.

I was trying to set it up so that the Windows I have can be used but I realise I will need to completely reinstall windows to use it under VirtualBox. I'll have to give it a lot more thought.

Thanks to all who have shared.

Alan.

---

### Post by bpalone on 2010-02-10
I can't remember if it was on the VirtualBox Forums or where, it may of even been on LinuxJournal.com, but I read of a way to use your installed Windows in VirtualBox.  It is a bit of a hassle and you do run a risk of messing things up in a big way.  But, it can be done.  I have also seen some threads about moving an existing Windows install to a Virtual Hardrive and being able to use it.  I am guessing that they may of had to reactivate Windows, but were able get around a long reinstallation job.

I haven't used or tried what I had seen.  But, I did look at it out of curiosity. VirtualBox (the PUEL version) is the way to go.  I use it all the time, well when I need a Windows app.  I still keep dual boot systems, because sometimes it is just better to do it natively.  But, for most quick applications like web postage, or the occasional web site that requires Internet Explorer, a Virtual machine gets the job done.

Good luck.

---

### Post by Mark Phelps on 2010-02-11
> **bpalone said:**
> ... I read of a way to use your installed Windows in VirtualBox.  It is a bit of a hassle and you do run a risk of messing things up in a big way.  But, it can be done.  I have also seen some threads about moving an existing Windows install to a Virtual Hardrive and being able to use it.  I am guessing that they may of had to reactivate Windows, but were able get around a long reinstallation job.

I was planning on doing a similar thing ... but the threads I read claimed that doing such forced you to reactivate Windows (in this case, Vista) every time you went in and out of the virtual session!!

Since some versions of Vista only allow ONE activation, that's obviously NOT a good solution.  Given the similarity of Win7 architecture to Vista, I would guess it suffers from the same limitation.

---

### Post by asharpham on 2010-03-03
I hope the activation thing is not correct. I have XP but I think it would still be annoying to have to activate it every time yuo want to access it. Does anyone know whether this is correct?

Alan.

---

### Post by Mark Phelps on 2010-03-03
> **asharpham said:**
> I hope the activation thing is not correct.
For Vista, at least, it IS correct.  The posts I read were from folks that actually tried this and confirmed the deactivation problem.
>  I have XP but I think it would still be annoying to have to activate it every time yuo want to access it. Does anyone know whether this is correct?
Don't "know" if it's the same for XP, but my best guess is that it is not.

However, before you do this, you should do a forum search on this. I remember reading some other posts from folks who said doing this "messed up" their MS Windows install.

---

### Post by asharpham on 2010-03-03
Okay, thanks Mark. I'll definitely check this out before going ahead.

---

