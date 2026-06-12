---
title: "my goal: a simple, pc with a stable system capable of networking and watching video"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by maccer on 2008-12-17
Hello,

Some of you might find my aim a little stupid and a luxury, nevertheless I would really like to achieve it :)

Now let me summarize what I would like, and what I have: 

Firs of all I am completely new to Linux.

I have a simple, Intel Celeron 2.4 PC, with an nVidia GeForce 5xxx graphics card. I want to use this computer solely for watching video and connecting to internet and a network of Apple computers.

Moreover, I would like to connect the computer to a TV via s-video and if possible to a regular VGA display at the same time (mirrored).

I am a Mac user and I really dislike Windows + I want a stable system thus I thought of Ubuntu Linux.

So:
1. I am interested in whether this Linux solution is a competent solution for what I want at all.

2. Will Ubuntu support my graphics card (it has an s-video output, a VGA output and a DVI output. I think it is an nVidia GeForce 5200)

Thanks for the answers!

---

### Post by Captain_tux on 2008-12-17
Run the LiveCD of whatever version of Ubuntu you want to try... at the very least, that will allow you to see if your system can operate with Ubuntu. Once you've done that and are satisfied and begin to install, the usual disclaimers about backups and data loss apply... the only guarantee being that if you break it, you get to keep the pieces.

You will have to tweak your system a bit to permit workability with your specific requirements, but therein lies the beauty of Linux/Ubuntu.

Good luck!

---

### Post by Dadsgé on 2008-12-17
with linux you probably have to be busy with your pc because linux is an operating system which always changes...
although after you installed ubuntu and had some tweeks to make it work properly on your pc, it does work fine.
i would suggest a LTS version like 8.04, this version is stable and will be supported till 2012 i think

about the graphical card, i don't know if it would work but remember that there are always other people who have had the same problem, so there will always be a solution ;)

---

### Post by redseventyseven on 2008-12-17
Hello maccer!

That doesn't sound stupid at all! A very good use of an old computer if you ask me.

I would suggest trying Linux Mint ([http://www.linuxmint.com](http://www.linuxmint.com)) - it's heavily based on Ubuntu, but one key advantage is that support for proprietary and patented codecs (such as mp3 for example) is included directly. Ubuntu doesn't include these because the direct distribution of these technologies is not legal in some countries. Hungary, fortunately, is not (to my knowledge) one of them.

I'm sure some would disagree with me and say Ubuntu's the way to go, but I've had good experiences of Linux Mint with in terms of getting networking and video set up with minimal fuss and I recommend it. You can still get support for DVD and mp3 and so on for Ubuntu - the method for doing so is well documented - so if you decide to use Ubuntu then you should still be able to achieve your goals.

---

### Post by philinux on 2008-12-17
The nvidia-glx-173 driver supports the 5200.

---

### Post by maccer on 2008-12-18
Thank you for the responses everyone! This is a really helpful forum community.


redseventyseven:

Thank you very much for Linux Mint. I checked it out and really liked it. Than I installed and everything went like a charm. It could flawlessly access the Macs and it detected the nVidia card and asked whether to activate the driver. Seems like a great system so far.

Only one problem. Yet I'm unable to make Mint recognize the s-video output to the TV but I think if I fool around with it a little and read some more posts I'll make it work.

So I am really glad. It is the perfect solution for a stable Linux system for someone not wanting too much "code involvement."

---

### Post by hailukah on 2008-12-18
You should already have nvidia-settings on you computer.  Check in the menu under administration.  You should be able to configure the tv-out there.

If nvidia-settings isn't available it is in package nvidia-glx.

sudo apt-get install nvidia-glx

---

