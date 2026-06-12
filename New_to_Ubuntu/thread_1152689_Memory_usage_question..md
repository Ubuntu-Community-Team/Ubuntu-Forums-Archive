---
title: "Memory usage question."
date: 2009-05-08
forum: New to Ubuntu
---

### Post by cycle_mycle on 2009-05-08
My System:

Acer Aspire 5335
Intel Celeron 575 2.0 Gig 667 fsb 1MB L2 cache
15.6" HD Acer CineCrystal LCD
Intel 4500M Graphics
4 GB RAM

In the System Monitor app it shows me that I only have 2.9 GB RAM.

Is there a way I can get Ubuntu to use all my RAM?

I'm not afraid to go to a different kernel - I think there's such a thing as a BIG MEM or HUGE kernel - is that what I need? I was pondering going to 2.6.30 because I think my graphics is supported better with it.

Any thoughts, comments, suggestions?

---

### Post by cycle_mycle on 2009-05-08
I think I see why there seems to be little interest in anyone trying to help me. 

I'm sorry I don't mean for Ubuntu to "use" all 4 GB of RAM, what I mean is there's a way for it to "recognize" that I have 4 GB of RAM.

Sorry for the silly wording. Thanks!

---

### Post by mcduck on 2009-05-08
> **cycle_mycle said:**
> I think I see why there seems to be little interest in anyone trying to help me. 

I'm sorry I don't mean for Ubuntu to "use" all 4 GB of RAM, what I mean is there's a way for it to "recognize" that I have 4 GB of RAM.

Sorry for the silly wording. Thanks!

You should just be a bit more patient, people answer questions when they notice one that they know answers for. The general rule is to bump your threads once every 24 hours if you are not getting answers.

Anyway, 32-bit operating systems are only able to use maximum of 4GB memory. As this amount includes stuff like your graphics cards memory etc. and not just RAM, the actual amount of RAM that can be used is usually somewhere around 3GB.

Apart from using a 64-bit system and 64-bit OS, it is possible to get more RAM by using PAE. Ubuntu's default 32-bit kernel doesn't have PAE enabled, but the server kernel does.

So, you have two options, you can either install the server kernel and use that, or compile the generic kernel yourself and enable PAE.

---

### Post by thelegionsplayer on 2009-05-08
er a pretty silly question--how do i kno wether my ubuntu is 32 bit or 64 bit:confused:

---

### Post by mcduck on 2009-05-08
> **thelegionsplayer said:**
> er a pretty silly question--how do i kno wether my ubuntu is 32 bit or 64 bit:confused:

It reads on the disk you used to install Ubuntu.. ;)

Seriously, you can check what kernel you are using with the "uname -a"-command. Or go to System/Administration/System Monitor and take a look at the System-tab.

---

### Post by thelegionsplayer on 2009-05-08
er. well i didnt burn a cd.i mounted the iso and installed it within windows.coz i dunno how to partition the disks
the system monitor thiny says-Kernael Linux2.6.28-11-generic
so is my ubuntu 64 bit or 32 bit?

---

### Post by 3rdalbum on 2009-05-08
Did the ISO say "i386" or "amd64" in the name? If it was i386, then you have the 32-bit version installed.

---

### Post by thelegionsplayer on 2009-05-08
aah yes it said i386 thnx for d help

---

### Post by Corelogik on 2009-05-08
Aside from the PAE extensions and being able to use 4GB or more of memory, are there any other functional difference between using the regular desktop vs. the server version of Ubuntu?

How would this impact upgrades in the future? Would Synaptic recognize it as the server version and retrieve the appropriate updates, or would I need to do it manually each time?

Basically I want to know if I can use the same apps as I planned to without having to get special versions or do a bunch of special configuring to use it as a desktop.

Also would the "amd64 - Server version" still run ok on an intel C2D? or would I need an AMD or intel x64 CPU?

---

### Post by mcduck on 2009-05-08
> **Corelogik said:**
> Aside from the PAE extensions and being able to use 4GB or more of memory, are there any other functional difference between using the regular desktop vs. the server version of Ubuntu?

How would this impact upgrades in the future? Would Synaptic recognize it as the server version and retrieve the appropriate updates, or would I need to do it manually each time?

Basically I want to know if I can use the same apps as I planned to without having to get special versions or do a bunch of special configuring to use it as a desktop.

In the end the server version is exactly the same OS as the desktop version. The difference is in what's included when you install it in the first place. The server version doesn't have any graphical user interface (as one is rarely used on production servers) but instead allows you to install several different server programs at the install time.

Anyway, if you plan to run desktop apps on the machine, use desktop version. It will give you a lot more of the things you want out-of-the-box.

Also note that **you do not need to intall server version of Ubuntu to use server kernel**. All Ubuntu versions are the same, and use same software from same repositories. You can install the server kernel on Desktop Ubuntu if you want, install any server programs on desktop version or install desktop applications on server version.

The only difference between Ubuntu versions is what's included in the default setup.

What comes to updates, all packages you have installed are updated automatically. This will of course include any kernels you have installed.

---

### Post by Corelogik on 2009-05-08
OK, so if install the i386 desktop version, I can add/upgrade to the server kernel later? Should I do that before or after I add all the apps and stuff I think I'm going to need/want or does it matter?

Also, what is the easiest/simplest way of installing/upgrading to the server kernel after install of the desktop version is completed?

I ask because the PC I'm planning to buy comes with 4GB of ram and I want t be able to use it.

Thanks for all the answers and assistance.

---

### Post by cycle_mycle on 2009-05-08
Thank you mcduck for your response. I agree I was somewhat impatient, but more so I read the post and saw what it looked like. It seemed silly to me that it looked like I would want 4 GB of RAM being used.
 
But in my defense I'd like to add that being new to Ubuntu and being forum-shy from other posts on distro site forums that tend to have "not the best dispositions" I got self-conscious. Plus I was getting a little slap happy because ever since I started posting here I've met some very nice people ready to help with some great advice. 

I'm actually sticking with Ubuntu because of my experience on this forum.

And on your behalf I would also like to thank you for the way you handled the seemingly impatient new-comer so as not to drive him off but make him feel more at ease. Thank you!

I installed the server kernel but I am still registering 2.9 GB RAM. My graphics are set to use 64 MB since I don't need to do anything more graphics intensive than watch a movie every now and then - and everything else office and Internet stuff.

Thanks again for your help.

---

### Post by mcduck on 2009-05-08
Corelogik: Yes, you can install the server kernel later. And it runs the same software normal kernel does, so it doesn't matter if you install programs before or after the server kernel.

To install the sever kernel just install the "linux-server"-package with Synaptic, or by running "sudo apt-get install liux-server". This package will get you the latest version of the server kernel, and also make sure that you will get all the updates for this kernel in the future.

cycle_mycle: Make sure you are actually using the server kernel, as it doesn't replace the generic one but instead becomes selectable option in the Grub menu when you boot the machine.

---

### Post by cycle_mycle on 2009-05-08
This is weird because the package dependency "linux-restricted-modules-server" is in the repository. (???) But this is what I get:

The following packages have unmet dependencies:
  linux-server: Depends: linux-restricted-modules-server (= 2.6.28.12.16) but it is not going to be installed
E: Broken packages

I even went to synaptic and checked the properties and the dependencies are all there.

And: 

~$ sudo apt-get -f install 

doesn't have anything to fix

Off we go on another adventure indeed...

---

### Post by cycle_mycle on 2009-05-08
I'm on to something, I may have figured it out. Just posting this to keep anybody from going any further on it... (unless you want to)

Thanks!

---

### Post by Corelogik on 2009-05-08
> **mcduck said:**
> Corelogik: Yes, you can install the server kernel later. And it runs the same software normal kernel does, so it doesn't matter if you install programs before or after the server kernel.

To install the sever kernel just install the "linux-server"-package with Synaptic, or by running "sudo apt-get install liux-server". This package will get you the latest version of the server kernel, and also make sure that you will get all the updates for this kernel in the future.

Thank you very much. Is there a thanks button or something somewhere?

---

### Post by newman on 2009-05-10
I was running 8.10 32 bit and my 4GB showed at 3.2GB. I tried installing 8.10 64bit but I got a blank screen, nvidia restricted not working! tried 8.04 64, same problem. 9.04 randomly locks system up. after 6 or 7 fresh installs I gave up and just stuck to 8.10 32bit and using 3.2GB ram. 64 bit is too much hassle anyway.

---

