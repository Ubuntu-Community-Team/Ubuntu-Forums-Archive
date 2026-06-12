---
title: "I don't understand how drivers work in Linux"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-27
I don't understand drivers in Linux.

I'm sure it is a big topic, but can someone put a pretty bow on it for me and/or direct me to something that is simple?

For example, how does a "Live CD" know what drivers to use? Are they universal or something?

If I installed Linux onto a USB device, I have heard that you can take that USB device anywhere and put it in any computer and it will boot up.  How is that possible?

---

### Post by galacticaboy on 2011-03-27
The thing with linux is "It just works" no one really questions how it does, it just does. When you run it from a USB and take is anywhere you go, it boots up like a live cd, it runs off of the USB as a sort of hard drive. It does not use your PC's hard drive, but the USB itself. It is a pretty handy tool especially if you do not have a cd burning drive. As for the drivers, I would guess that they use a generic form for the live CD just to work and when you install and run the update manager it then corrects it to a proper version.

---

### Post by Sef on 2011-03-27
> I don't understand drivers in Linux.

I'm sure it is a big topic, but can someone put a pretty bow on it for me and/or direct me to something that is simple?

Mostly the drivers are already in the kernel. If they aren't then you have to download them.

> For example, how does a "Live CD" know what drivers to use? Are they universal or something?

If I installed Linux onto a USB device, I have heard that you can take that USB device anywhere and put it in any computer and it will boot up. How is that possible?


Linux automatically detects the drivers. If the drivers are in the kernel, then those drivers will be used. 

Either a Live CD or Live USB can be used on almost any computer. Just set the boot menu to check the USB port or CD-ROM first.

---

### Post by Diametric on 2011-03-27
> **galacticaboy said:**
> The thing with linux is "It just works" no one really questions how it does, it just does. When you run it from a USB and take is anywhere you go, it boots up like a live cd, it runs off of the USB as a sort of hard drive. It does not use your PC's hard drive, but the USB itself. It is a pretty handy tool especially if you do not have a cd burning drive. As for the drivers, I would guess that they use a generic form for the live CD just to work and when you install and run the update manager it then corrects it to a proper version.

With all due respect, I think that your comment "no one really questions how it does, it just does" runs counter to what Linux is.  Not trying to make a mountain out of a mole hill...really, but I feel that leaning the how's and whys is exactly what makes Linux and it's users as cool as they/we are.  Question everything...learn everything...hack everything.  that's what makes an open OS cool....you can break, create, hack and modify what ever you want.

Respect,
-Dylan

---

### Post by galacticaboy on 2011-03-27
I understand what you mean, that is mostly how I feel, I do not care how those drivers work, just as long as they do and it gets me online fast. I am sure some people care, but I however do not! lol I am just glad they work!

> **Diametric said:**
> With all due respect, I think that your comment "no one really questions how it does, it just does" runs counter to what Linux is.  Not trying to make a mountain out of a mole hill...really, but I feel that leaning the how's and whys is exactly what makes Linux and it's users as cool as they/we are.  Question everything...learn everything...hack everything.  that's what makes an open OS cool....you can break, create, hack and modify what ever you want.

Respect,
-Dylan

---

### Post by beew on 2011-03-27
If you need proprietary drivers (most common examples are some wireless cards and video cards) then they are not in the kernel and need to be installed by the user. The way to install them depends on the distro, in Ubuntu it is usually super easy you just need to click a button, in other distros it can be a painful process.

---

### Post by craigdele on 2011-03-27
I have Ubuntu 10.4 install on a 8gb usb drive. It works well on my employers desktop, home desktop, and home laptop.

To start from USB, Press F12  when PC is rebooting or on initial startup. A menu will be displayed allowing you to select from Hard-drive, Optical Drive, or USB.

Dele

---

### Post by Learning Linux 2011 on 2011-03-27
> **Sef said:**
> Mostly the drivers are already in the kernel. If they aren't then you have to download them.



Linux automatically detects the drivers. If the drivers are in the kernel, then those drivers will be used. 

Either a Live CD or Live USB can be used on almost any computer. Just set the boot menu to check the USB port or CD-ROM first.


Thanks Sef, that was the type of thing I was looking for.

---

### Post by bodhi.zazen on 2011-03-27
> **galacticaboy said:**
> The thing with linux is "It just works" no one really questions how it does, it just does. 

You may not care, but the OP cares enough to ask, and many people here do care how Linux works.

The short answer to the OP question is that drivers are (typically) built into the kernel.

If you want to know the details, take a look at compiling a custom kernel ;)

[http://www.howtoforge.com/howtos/linux/kernel](http://www.howtoforge.com/howtos/linux/kernel)

Most distros, such as Ubuntu, build many drivers into the kernel as modules. In simple terms this means the module is not loaded if it is not needed.

To see the modules you are using, open a terminal and use lsmod

Some hard ware, most commonly video drivers and wireless cards, lack open source drivers. In that event either the hardware may not work or you may need to compile the driver yourself, perhaps applying a patch or two.

When building a live CD people typically include as many drivers, as modules, as possible so that as much hardware will work "out of the box"

Some people build custom kernels, either to enable drivers not included by default, add modules, or, more commonly, remove modules (see linux from scratch or gentoo).

IMO building a custom kernel saves a bit of hard drive space and a bit of ram. With modern hardware you will not likely notice a difference.

---

### Post by piquat on 2011-03-28
> **bodhi.zazen said:**
> When building a live CD people typically include as many drivers, as modules, as possible so that as much hardware will work "out of the box"

So following that line of thought, the modules are all on the CD (or where ever, maybe even online), not initially "loaded" into the kernel until it looks at the hardware and picks the module it needs.... am I looking at this the right way?

Thanks.


Excellent topic btw.  I've tried to read a bit on this, but the summary kind of ties it all together.

---

### Post by bodhi.zazen on 2011-03-28
> **piquat said:**
> So following that line of thought, the modules are all on the CD (or where ever, maybe even online), not initially "loaded" into the kernel until it looks at the hardware and picks the module it needs.... am I looking at this the right way?

Thanks.


Excellent topic btw.  I've tried to read a bit on this, but the summary kind of ties it all together.


That is correct, and it applies not only to live CD, but most kernels on most distros.

[http://www.freeos.com/articles/4051/](http://www.freeos.com/articles/4051/)

Best way to understand how it works is to compile your own kernel.

When you make menuconfig you will see all the various options / drivers . You can then select to build a driver into the kernel or as a module.

Most distros build many drivers into the kernal as modules.

When building a custom kernel, you first identify your hardware, then build only the drivers you use. The result is a smaller kernel with only the drivers you use on your hardware.

Although many people claim speed advantages, in my experience it is more a learning experience. The speed advantages are modest at best.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by galacticaboy on 2011-03-28
Like I said this was how I felt, I should have not worded it that way, I am sure some people do care, but I do not, as long as it works, I am happy.

---

### Post by piquat on 2011-03-29
> **bodhi.zazen said:**
> That is correct, and it applies__[]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")

Thanks, the fist link helped a lot.

I've looked at compiling my own (read through that second link before) just solely for the learning experience but I'm not quite there yet.  Baby steps...:P


Thanks again!

---

### Post by Nutria on 2011-03-29
> **Learning Linux 2011 said:**
> I don't understand drivers in Linux.

I'm sure it is a big topic, but can someone put a pretty bow on it for me and/or direct me to something that is simple?

Not really.  :(

But I suspect that you didn't mean to ask the question that you actually asked...  ("Precision asking" is important to getting the information you really want.)

> For example, how does a "Live CD" know what drivers to use? Are they universal or something?

Many are built into the "kernel".

> If I installed Linux onto a USB device, I have heard that you can take that USB device anywhere and put it in any computer and it will boot up.  How is that possible?

Partly, the motherboard must tell the OS what hardware is attached to it, and partly Linux probes the mobo and it answers.

Given that list, Linux has been programmed to know which drivers (pre-stored by the people who created the ISO file) to use for which device.

---

