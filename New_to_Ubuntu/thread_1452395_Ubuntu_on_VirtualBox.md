---
title: "Ubuntu on VirtualBox"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Twitch04 on 2010-04-11
Hello, everyone. I've posted here before about dial-up stuff, but... Thought I have another question. 

I dual-boot XP and Ubuntu, but I haven't used Ubuntu much since it takes rebooting to switch  between them. So a friend of mine suggested that I use Sun Virtualbox to have a dynamic Ubuntu partition on my brand-new 1 TB hard drive, so I did so. I'm on it right now, typing this. >_>

So I suppose my question is what would be the difference(s) between running Ubuntu this way and just running the dual-booted one? This one is FAR easier to use the internet with. I managed to get Dial-Up working on the other one with I believe KPPP, but... It was fairly slow. On this I can just connect in XP, run VirtualBox, and Ubuntu is already connected. 

However, I know that running Ubuntu through Virtualbox splits my CPU and ram (I have a 2.7 ghz CPU and 2 gigs of ram), making running it a tad slower. 

I was just wondering if this would be a good idea for now since I'm not REALLY considering using Ubuntu full-time. 

Any thoughts, pros, or cons would be appreciated. Thanks, everyone.

---

### Post by JiuJitsu500 on 2010-04-11
In my opinion I think you're doing a great thing... I ALWAYS tell others to virtualize things, both because it's cool to do, and mostly because it is in a sense better than dual-booting (stops GRUB and other boot-up monsters from fighting).

I'd say pros include it's easier than a dual boot, you'll notice a billion threads over a million forums about dual-booting screwing things up, just because of the way Windows/Mac/BSD/Linux, etc store files on a hard disc, and boot. With a LAN-line internet, the ethernet cable needs virtually no adjustment to be online. And certainly, for testing an OS, something in development especially (i.e. Ubuntu 10.04, or a modified Windows), it lets nothing into the core computer. So, if you were to get a virus on the virtualized OS, it would keep your computer absolutely safe.

Some cons could be it can sometimes be difficult to share files, and the stress on the CPU sometimes can be a noticable pain. Unless you have a quad-core, you will almost always see a difference. A good computer though, with little usage on the actual machine, and it pretty much gets rid of all these problems (my laptop sees almost no issues, 9.10 as my main OS, virtualized Mac OS X and Windows XP Vienna... off 4 GB of RAM and a dual-core 2.1GHZ CPU). It can be slow to boot though, my windows takes anywhere from 30 seconds to almost half an hour to boot.... maybe it's mood?

To test and play, definately go with what you're doing. But, I would recommend the other way around, virtualize Windows and always save the machine state instead of turning it off (with mine anyway, screws things up sometimes). Linux on your machine means a whole hell of a lot of stress relief on the computer, the virtualized windows will be smooth as butter if you keep it up do date and secure :)

It's hard to write a list like this though, and mine is extremely rough, but play and see what you like....

Oh, and dual-booting in my mind sucks (or has never worked right for me, with or without Wubi).

---

### Post by Twitch04 on 2010-04-11
Oh, dual-booting worked fine for me the maybe 10-20 times I did it to boot into Ubuntu.My CPU is dual-core, if that helps with the Virt Machine at all, haha. 

Yeah, the Linux on my actual HD [which, by the way, is just an old 80 gig that I made last for 4 years, hence why I bought a 1 TB and hooked her up as a slave drive] is only like an 8-10 gig partition, so it's not much anyway. I've been meaning to get rid of it, but I'd have no boot loader due to a lack of GRUB, so... I haven't done it yet since I don't know what to do. That same friend from the first post can help me out with that, though.

But apart from that, running it virtually has been pretty smooth sailing. Installing packages basically has to be done overnight, since having to install all of the dependencies [or whatever the prerequisite files are called] makes a pretty hefty download for a 2-3 kbs download connection speed [when it connects it says 28.8 kbs, yet when I download a file, it maxes at 3 kbs. >_<], so I basically haven't done much of that yet. I did at my friend's house. Actually, it was the very first time I had installed anything the terminal way. I just remembered, so... "sudo apt-get install kppp" was the first thing into the terminal, haha. It felt great. XD. 

Heck, I just like how human Ubuntu is. Easy. I shared my whole 1 TB hard drive between my XP host and Ubuntu guest, and all it was was going to where the 1 TB was mounted in /mnt and dragging the folder to the top toolbar thing. Bam. Folder shortcut. I honestly wish Linux gets more support in general. 

I'm rambling anyway. My computer seems to handle it fine, just my internet is horrid. If I had better internet, I'd probably use the Virtual Machine more often, downloading packages and plugins for everything to help with it working.

---

### Post by Twitch04 on 2010-04-12
I've another question related to VirtualBox.

Is there any way to share my 80gig hard drive's Ubuntu partition with it? The thing is that Windows can't even see the partition, aside from in the disk management utility. And even there it says that it is "Healthy (Unknown Partition)" and I can't do anything with it besides delete it [which would be a bad idea since GRUB is my boot loader]

I don't suppose there's some way around this? >_>

---

