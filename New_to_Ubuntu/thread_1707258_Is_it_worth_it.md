---
title: "Is it worth it?"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by KrajtMalti on 2011-03-15
I have an MSI CX623 laptop, with the specs 

VGA : NVIDIA Geforce 310M/1GB DDR3
RAM : DDR2 4GB (2GB*2)
Processor: Intel(R) Core(TM) i5 CPU       M 450  @ 2.40GHz (4 CPUs), ~2.4GHz

I want to be able to run Adobe CS 5 Master collection mainly (Premiere, Photoshop, After effects, Flash and so on, and Steinberg Cubase and maya in the future (But I will probably use my desktop as it's more powerful. 

I know of a problem concerning the optimus driver on the NVIDIA card, but I wish to know if I would get better performance  then the Windows 7.

I would like to know if it's worth it to switch to Ubuntu Netbook OS.

Thank you, Stephen.

---

### Post by Dutch70 on 2011-03-15
Welcome to UF KrajtMalti,

Try running it from a live usb stick to find out for yourself. If you're using windows, you can create the usb stick here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Or you can use Unetbootin here...
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

ps. You can also use & create a live cd, but it's much slower running from a cd than a hdd even if it's a usb stick.

---

### Post by mcduck on 2011-03-15
Apart from Maya, all the applications you want to run are only available for Windows & OSX, not for Linux. Based on that, you'd probably be happier with Windows 7 than with Ubuntu.

While some of those programs *might* work through Wine, it definitely isn't going to be as smooth experience as it would be on Windows. Same goes for virtualization.

If you want to use Ubuntu, I recommend dual-booting so you can still run those programs on an OS they were made for, and use Ubuntu when you don't need to work with those apps.

(Or skip those applictions, and learn Gimp, Inkscape, Ardour, Blender etc native Linux applications instead. Maya still works. ;))

---

### Post by fabricator4 on 2011-03-15
> **KrajtMalti said:**
> 
I want to be able to run Adobe CS 5 Master collection mainly (Premiere, Photoshop, After effects,

That software suite is written to run under Mac and Windows. There is no native Linux versions or support.

There are programs that will probably do all of what you need, but to get native apps running under Linux, you will have to make some changes.

The Gimp for example is at least as powerful as Photoshop, but it is a lot more hands-on.  For example, scripting which is done with a few key presses under Photoshop requires Python type programming under The Gimp, unless they've added auto scripting since the last time I looked.

This actually makes The Gimp _more_ power in some ways, but it requires a steep learning curve, especially if you're not familiar with some programming languages.  I suggest you have a look the programs available.  To maintain productivity you'll have to keep the windows boot partition until you are ready to fully migrate over to Ubuntu.  Many people find it well worth the effort, and gradually find they need to boot into Windows less and less, and maybe not at all.  Deleting Windows completely and installing Ubuntu only would not be advised unless you're sure that's the way you have to go.

Linux has some distinct advantages...  A secure environment, less worry about viruses and trojans, excellent protected  memory management, efficient kernel code and applications, Completely free OS and updates, Long term support, a friendly community, and while Ubuntu is one of the best out of box friendly Linux distributions it also all of the under the hood configurability of a serious distribution.  Much of the software that is available is outstanding, and free.

One of the down-sides that you will have to look at is hardware compatibility.  For example you will have to look at how well supported your photo printer is.  Epson tends to be good to excellent, Canon is rather variable across the range.  There is a very good print manager called Turbo Print fixes a lot of compatibility issues and does it very well indeed, but it is not free.

I suggest you set up a dual boot system, Perhaps 10.04 LTS rather than 10.10.  As an alternative to a dual boot system you could try a Wubi install first.  This works in a similar manner to dual boot except you don't need to re-partition the hard drive - Ubuntu will run as a virtual boot inside of windows.  It's easy to install and easy to delete if you want to, but the performance is not quite as good as a native Ubuntu boot.

The other thing you'll need to look into if you do a lot of professional image editing is colour profiling under Linux.  I think there's workarounds now for using some of the Spyder devices under Linux, but do your research.

Image editing is the only reason I keep a Windows boot machine around any more.  It's not that it can't all be done, it's just that I don't have the time and resources to migrate it all to Ubuntu at this time.

Chris

---

### Post by Dutch70 on 2011-03-15
> **fabricator4 said:**
> 

I suggest you set up a dual boot system, Perhaps 10.04 LTS rather than 10.10.  As an alternative to a dual boot system you could try a Wubi install first.  This works in a similar manner to dual boot except you don't need to re-partition the hard drive - Ubuntu will run as a virtual boot inside of windows.  It's easy to install and easy to delete if you want to, but the performance is not quite as good as a native Ubuntu boot.

Chris


As much as I hate to say it. The performance of a Wubi install on my g/f computer worked better than mine(native install), until I found a workaround for Compiz. My system kept freezing,  Her's did not. The workaround for the graphics card is in my sig. I had to use it on Linux Mint & Kubuntu as well. 

I have 4GB of RAM, she has 1GB.
We both have Intel dual core processors, mine is 1.8GH, hers is 1.6GH.
**We have the same exact video card.**

The downside to Wubi is, if windows fails, it takes Ubuntu with it, As opposed to a native install, if windows fails, you still have a computer & access to all your files because of Ubuntu.

---

### Post by fabricator4 on 2011-03-15
> **Dutch70 said:**
> As much as I hate to say it. The performance of a Wubi install on my g/f computer worked better than mine(native install), until I found a workaround for Compiz. 

Probably not a typical result.  Certainly I found a Wubi install slower to boot, and slower to shut down.  One thing I was amazed at was how fast some of my machines shut down.  The 900SD for example (900 MHz Celeron) shuts down in about 2 or 3 seconds as long as there is not a large amount of cached disk writes or something.

One of the reasons I _hate_ booting into Windows is how darn slooow it seems, even though it lives/lived on my fastest machines.  Shut down Windows and get that message "Installing update 1 of 8. Do not turn your computer off" etc and steam starts coming out of my ears.

I went to demo an album layout to a client and turned the laptop on, and got the "Windows is installing 8 updates..." etc even though it was my fourth boot that morning and I thought it had already done all its messing around.  The Laptop nearly got flying lessons.  My own fault, I know, but *really*...  

The laptop now has a full Ubuntu install on it.  Windows is history.

Sorry, I didn't mean to rant.:(

Chris.

---

### Post by mastablasta on 2011-03-15
> **fabricator4 said:**
> The Gimp for example is at least as powerful as Photoshop, but it is a lot more hands-on. For example, scripting which is done with a few key presses under Photoshop requires Python type programming under The Gimp, unless they've added auto scripting since the last time I looked.
 
This actually makes The Gimp _more_ power in some ways, but it requires a steep learning curve, especially if you're not familiar with some programming languages. 
 interesting cause i never saw GIMP perform the new features available in CS5 such as autocomplete etc. that i saw in the demo features movie on you tube
 
> **fabricator4 said:**
>  
One of the reasons I _hate_ booting into Windows is how darn slooow it seems, even though it lives/lived on my fastest machines. Shut down Windows and get that message "Installing update 1 of 8. Do not turn your computer off" etc and steam starts coming out of my ears.

This should only happen once a month. first Wednesday of the month, is it? 
 
> **KrajtMalti said:**
>  
I would like to know if it's worth it to switch to Ubuntu Netbook OS.
.
 
Netbook version is designed to run on netbooks that have small screen and is suposed to be optimized for Atom processors.
 
In your case - for windows programmes you will have to use windows, however as suggested you can use dualboot (place system side by side on separate hard disk partitions). it should be normal desktop, probably the AMD64 version (64bit system) in your case.

---

### Post by mcduck on 2011-03-15
> **mastablasta said:**
> interesting cause i never saw GIMP perform the new features available in CS5 such as autocomplete etc. that i saw in the demo features movie on you tube
 

Do you mean the content-aware resizing/filling?

That was released as a plugin for Gimp soon after the first working concept of the idea appeared in public. I've used that feature on Gimp since 2004, so it took quite a long for Photoshop to catch up... ;)

Anyway, like fabricator4 said, Gimp is a bit more hands-on, allowing you to do the same things, but requiring you to actually know how to do that yourself instead of providing you with automatic single-purpose tools (not that I wouldn't like using the extract tool on PS, for example, but I also know how to separate image from background myself. ;))

---

### Post by mastablasta on 2011-03-15
i need to investigate into pluins then... i use Gimp on Windows as well as on Linux. I liek it cause there is a version in my language and i can understand the small icon notes. so i can go through quickly without searching help online all the time. i am an amateur, but sometimes i need to do something advanced. :-)

---

### Post by Dutch70 on 2011-03-15
> **fabricator4 said:**
> Probably not a typical result.  Certainly I found a Wubi install slower to boot, and slower to shut down.  One thing I was amazed at was how fast some of my machines shut down.  The 900SD for example (900 MHz Celeron) shuts down in about 2 or 3 seconds as long as there is not a large amount of cached disk writes or something.

One of the reasons I _hate_ booting into Windows is how darn slooow it seems, even though it lives/lived on my fastest machines.  Shut down Windows and get that message "Installing update 1 of 8. Do not turn your computer off" etc and steam starts coming out of my ears.

I went to demo an album layout to a client and turned the laptop on, and got the "Windows is installing 8 updates..." etc even though it was my fourth boot that morning and I thought it had already done all its messing around.  The Laptop nearly got flying lessons.  My own fault, I know, but *really*...  

The laptop now has a full Ubuntu install on it.  Windows is history.

Sorry, I didn't mean to rant.:(

Chris.

No need to apologize, I thought it was kinna funny. 

Also, I wasn't referring to the boot/shut down times. I still can't figure out why her system didn't have the freezing problem and mine did, 
even though we both have the Intel 82945G video card, and mine is faster than hers on every other scale.

---

### Post by fabricator4 on 2011-03-15
> **mastablasta said:**
> 
This should only happen once a month. first Wednesday of the month, is it? 

It would, except I don't use that machine too often, and I booted Windows on it hardly at all.  On that morning I decided to use Windows for some reason, and the epic upgrade cycles it went through trying to catch up were horrifying.

Chris

---

