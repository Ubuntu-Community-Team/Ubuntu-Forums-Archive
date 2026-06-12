---
title: "&quot;Karmic Koala 9.10&quot; will it run on my laptop?"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by s1design on 2009-12-01
[SIZE=2][FONT=Verdana]I'm new to the ubuntu forums and I'm seeking advice. I have been intrigued by what Linux has to offer on it's open source OS. I have seen a bit of what it can do and the interface looks awesome as well... when customized. I just received my installation cd in the mail for Karmic Koala 9.10. First of all, I would like to know if it will run perfectly on my laptop.

Here are the specifications:

Compaq Armada M700
Pentium III
1Ghz Processor
576 megs of RAM
ATI Rage Mobility AGP
Toshiba 40gb Hard Drive


I'm aware of the minimum requirements, but I mainly want to know if I won't run into any problems... will the graphics run smooth... and if it is worth installing it on my laptop???

:P Let the comments Begin!!!!

Sal
[/FONT][/SIZE]

---

### Post by Paqman on 2009-12-01
The best way to find out how well it will run is to boot up the CD. Choose "try Ubuntu without any changes to my machine" (or words to that effect). That will boot you up into Ubuntu running completely from the CD, so you can test all your hardware.

It'll run a lot slower off the CD than it would off the the hard drive, and you won't be able to install drivers for your graphics card yet, so you won't get all the flashy desktop effects. But it gives you a chance to test everything else, and if you're happy you can start the installer straight away.

---

### Post by QIII on 2009-12-01
I have an old machine with very similar specs that is running the current development version, Lucid Lynx.

But it has an nVidia GPU.

I am concerned about the ATI GPU, because it is definitely legacy.  You would have to make do with the open source driver and none of the flashy effects would likely be available to you.

Also, just to be sure:  You did order the 32 bit version, right?

---

### Post by Land Rover Series 3 on 2009-12-01
Like Paqman says, the only way to know is to try it. Run it from the live CD first, without installing it, then you'll get a feel for how it works - though it will work MUCH MUCH slower than the real McCoy installed on your hard disk.

I've been using Ubuntu for a couple of weeks, and will never go back to using Micro$oft stuff again. It would now seem a completely retrograde step.

Any Linux distribution ("distro") will probably run MUCH faster and definitely more stably than what you have at the moment - what are you running at the moment?

Anyway, there are even a lot of Linux distributions tailored towards the (dare I say it) lower capability pc's - those lacking in hard disk space, memory, graphics cards and so on - and they will probably outshine anything else that you could put onto your pc.

Good luck

---

### Post by nerdy_kid on 2009-12-01
wouldnt he be better of with Hardy?  i dont think the nonfree ATI drivers work (they dont with mine) with karmic but they do with Hardy.

---

### Post by doas777 on 2009-12-01
I to am a bit worried about the rage card. the 3d drivers won't work with it. if your good with basic graphics though, the rest will probably work. if you have a wifi card that may or may not function correctly.

---

### Post by Land Rover Series 3 on 2009-12-01
You might also want to have a read through this:

[http://ubuntuforums.org/showthread.php?t=1341458](http://ubuntuforums.org/showthread.php?t=1341458)

---

### Post by s1design on 2009-12-01
The graphics would be awesome... but it's not really a crucial element at the time. I'm more curious if I can run 9.10.

---

### Post by Rytron on 2009-12-01
Scroll down a bit to see your model.

[http://www.linux-on-laptops.com/compaq.html](http://www.linux-on-laptops.com/compaq.html)

Edit: Also try [here]("https://wiki.ubuntu.com/LaptopTestingTeam/CompaqArmadaM700").

---

### Post by mc4man on 2009-12-01
I would try the live cd first, if it does boot into ubuntu you'll get a fairly decent idea on how it will run though with that small amount of ram it may run a bit slower.

If it doesn't boot into ubuntu then you could try an install ( reboot and choose the install option instead of the try first one.

Xubuntu may of been a more realistic choice for those specs ( depending on usage

While not that relevant to the Op, to clear up 2 things -
 
On 9.04 and 9.10 you can install the restricted drivers if available and load them for testing on the live cd. 
9.10 actually has some on the cd, though I think it's better to install them from the ubuntu repo

The drivers are loaded thru a log out, a restart is not needed.

As far as running slower if you have at least 1Gb of ram, ( preferably 2 or more), a live cd will run as fast as the real install, you can get an excellant idea on how the install will work

---

### Post by s1design on 2009-12-02
At the moment I find myself backing up all my data... don't want to lose anything. I will load 9.10 and see it first hand, can't wait :rolleyes: As a second option, some have suggested running and earlier version on my laptop. What might that be? and... where may I get it?

---

### Post by doas777 on 2009-12-02
poke around the ubuntu first page, and you will find a link to the alternative installs including text-only installers, and past versions.

---

### Post by s1design on 2009-12-02
](*,) Can't seem to locate it...

---

### Post by s1design on 2009-12-03
I managed to install 9.10 on my laptop and it runs fine. I can't seem to run all the effects... I guess I'm missing some drivers... I do use a wifi card by netgear to get my internet access but if I install the drivers will it work? I do use several programs that run on Windows, can I install them on Ubuntu??? What do I need???:-k

---

### Post by s1design on 2009-12-04
Little help...  What should I be looking for???

---

### Post by zkriesse on 2009-12-04
> **nerdy_kid said:**
> wouldnt he be better of with Hardy?  i dont think the nonfree ATI drivers work (they dont with mine) with karmic but they do with Hardy.
Hardy is built for older systems or at least it was built during the time of older systems but his is newer...and he has a slower processor. Hardy to me hogs up system processing.

> **doas777 said:**
> I to am a bit worried about the rage card. the 3d drivers won't work with it. if your good with basic graphics though, the rest will probably work. if you have a wifi card that may or may not function correctly.
Very good point sir.

> **QIII said:**
> I have an old machine with very similar specs that is running the current development version, Lucid Lynx.

But it has an nVidia GPU.

I am concerned about the ATI GPU, because it is definitely legacy.  You would have to make do with the open source driver and none of the flashy effects would likely be available to you.

Also, just to be sure:  You did order the 32 bit version, right?
Agreed my man.

---

### Post by Elfy on 2009-12-04
> **s1design said:**
> Little help...  What should I be looking for???

If there is a driver available then they will be in System - Admin - HArdware Drivers

Some windows programs work in Wine - and I do mean _some_

Let us know what they are - might be alternatives

[http://www.linuxalt.com/](http://www.linuxalt.com/)

---

