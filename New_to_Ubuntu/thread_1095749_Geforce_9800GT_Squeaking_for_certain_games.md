---
title: "Geforce 9800GT Squeaking for certain games"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by hovzio on 2009-03-14
Hi guys, just bought a new graphic card, (the first time I have not been running intel chipsets) and overall I'm thrilled. Compiz everything runs extremly well and the graphics seem to be running well. I can definitely "feel" that there is somthing different going on in my box. So gaming for the most part seems to work rather well....openarena, sauerbraten, warsow all work fine. Then there are some games (nexius is one) that make my graphic card go nuts and start "squealying", this is in no way affecting gameplay. Nevertheless the squeaking is driving me nuts. I am using the newest graphic "driver" that ubuntu offers.(there were two to pick from, I chose the recommended one.) Like I said, I'm accustomed to intel chipsets, hence this is new territory. I must say, I really enjoy the graphics but that "tainted kernel" at boot ...(why can't they just release the source???) Is this squeeking normal?? Has anyone else experienced this?

---

### Post by Ms_Angel_D on 2009-03-14
You might want to try downloading the latest NVidia driver from thier website and follow this tutorial on installation: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

It's a much better driver, I recently installed it on my hubby's computer who has a new 1gb 9400 GS and it runs fantasticly.

---

### Post by hovzio on 2009-03-14
> **MetalHellsAngel said:**
> You might want to try downloading the latest NVidia driver from thier website and follow this tutorial on installation: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

It's a much better driver, I recently installed it on my hubby's computer who has a new 1gb 9400 GS and it runs fantasticly.

Cool, will take a look at things. I just spent the last 3 hours reinstalling and setting up things.. Somthing tells me I may end up doing this again if I try this although there seems to be the option of booting to rec. mode and uninstalling the driver if s... hits the fan. Cool, will try, thank you.

---

### Post by hovzio on 2009-03-23
Hi, people! Jsut a follow up to my original post;

My power supply was broken.. kinda. This was a brand new ps I must mention. I must admit I should have brought the pc back to the store much earlier, squeaking like that by all means has to imply that somthing is broken. What eventually ended up happening was that the pc just shut down and was dead after that. I brought it in and virtually everything was hosed. They offered me a full replacment and the option to upgrade if I wanted to pay a little extra. :guitar: So I went for an asus mobo and a quad.. very cool. 

Just thought I'd mention the problem being solved, maybe it will help someone experiencing similar problems. It was quite frustrating as a whole and the sqeaking of the vga was "just" quiet/loud enough to try and pass it off as nothing serious, nevertheless it was irritating. (And quite serious) take care everyone :D

EDIT: Thank you metalhellangel; the nvidia driver you mentioned installed perfectly and works like a charm, thanks.

---

### Post by hkb11001 on 2009-04-07
Hi,
I'm looking at installing a new graphics card on an existing Intrepid Ibex system. What was your process in installing your 9800GT? Did you simply replace the old card with the new one? Were there any other configuration issues you had to address?
Thanks

---

### Post by anewguy on 2009-04-07
A lot of the newer fast video cards require auxillary power inputs, not just from the buss the card plugs into.  There may 4 pin or other power connectors that need to be plugged in, much like a disk drive.  The result is a heavier load on a power supply.  Yours is by far not the first this has happened to.  Some people upgrade their PC's but don't upgrade the power supply and the result is an overloaded power supply destined for failure.  In your case, it sounds like it was a new PC and therefore the power supply was either defective or too small to start with.

So, just a recommendation to all who are looking at upgrading their PC, or just upgrading their video card:  Be sure to check the power requirements, then check your power supply.  With todays newer video cards a 400-500 watt power supply would be a good start.  If you have a lot of drives, consider the high end of that number.  It can save you frustration and extra expense if your power supply was to go bad and take out other components with it.

dave :)

---

### Post by striker_gt on 2009-04-15
[SIZE="4"]_9800gt on Ubuntu 8.10 64 bits_[/SIZE]

I'm getting a lot of trouble trying to install the Nvidia restricted driver for ny MSI 9800GT 512 OC.

I've tried everything and I cannot make it work. Some sort of things like:

[I][http://www.nvidia.com/object/linux_d...64_177.82.html](http://www.nvidia.com/object/linux_d...64_177.82.html)

sudo /etc/init.d/gdm stop

sudo ./NVIDIA-Linux-x86_64-173.14.05-pkg2.run[/I]

and also the built-in installation through synaptic package manager, update manager, command line and a lot of stuff...

*"I have successfully installed Nvidia drivers on ubuntu 8.04 and also compiz fusion but in 8.10 things are getting too much frustrating..."*

I have Linux ubuntu **2.6.27-11-generic kernel** and some installation give me an error saying that the kernel is incompatible...

Another times, with some methods I get the error saying **no screen found** and other times it says that I have errors with xconfig.:(

Also I know to uninstall the messed config with this command

*$ sudo apt-get remove nvidia**


Please can you describe me the method step by step (like a noob), so I can make it work.

Thank you very much for your support! :D

---

