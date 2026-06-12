---
title: "Trying to install on an old machine with little memory..."
date: 2009-04-08
forum: New to Ubuntu
---

### Post by joe m. on 2009-04-08
Sorry for the simple question. I have been searching the forums, and read many pages. So i am not just asking willy nilly. but here is my problem... (also, i posted this in the install section, if one of the moderators wants to consolidate the threads...)

I have a very old Gateway solo laptop (it was the top of the line when i bought it). I don't know the exact system specs, because there is no operating system on it, but it is a pentium 3, and i think has about 1g harddrive (or something). It was running windows 98 last time it was working.

So i have tried to install Ubuntu on it, and obviously that didn't work (because it requires more system than my computer has to offer, i assume. it just went black during the install). Next i tried to install xubuntu. That seemed to go better, getting all the way to the part of the install where it partitions the hard drive, but then gets stuck on the blue screen. (also, on the way to the partition it would show a red screen saying it could not detect any network options, and i would just make it continue anyway)

So Im not sure what to do next. I just want to get a basic operating system on it, that allows me to do word processing and email. I tried this, but it was obviously not applicable because i don't have any operating system on the machine now.:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

what can i do? please advise.

Thanks.

---

### Post by lisati on 2009-04-08
How much ram does your system have? As I understand it, under 128Mb can be problematical.

---

### Post by kerry_s on 2009-04-08
use this guide: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

you can look in your bios for the specs, cpu, memory.

---

### Post by joe m. on 2009-04-08
trying the barebones version now.  i'll let you know how it works out.  thanks.

---

### Post by joe m. on 2009-04-08
ok, so here is a problem.  after this page:
[http://www.psychocats.net/ubuntu/images/minimalintrepid09.png](http://www.psychocats.net/ubuntu/images/minimalintrepid09.png)
i get a red screen that says:

[!] configure the network
no network interfaces detected
no network interfaces were found.  the installation system was unable to find a network device.
you may need to load a specific module for your network card, if you have one.  for this, go back to the network hardware detection step.


what do i do?  the computer was made for dialup?

ok, edit:

so i just continued from that screen.  went through a few more, and got to this one and then got another warning screen:
[http://www.psychocats.net/ubuntu/images/minimalintrepid13.png](http://www.psychocats.net/ubuntu/images/minimalintrepid13.png)

[!] choose a mirror of the ubuntu archive
bad archive mirror
the specified ubuntu archive mirror is either not available, or does not have a valid release file on it.  please try a different mirror.

---

### Post by kerry_s on 2009-04-08
that's a net installer, you need to have internet, it installs over the internet. you don't have a pcmcia ethernet card?
how were you planning on emailing?

---

### Post by 3rdalbum on 2009-04-08
For something like that, I'd recommend Puppy Linux. Ubuntu requires way more RAM and hard disk space than you say that machine has; even Xubuntu does. Xubuntu is made for machines that need upgrading, not machines that are hopelessly obsolete.

Puppy Linux should do well; it's built from the ground-up for computers like yours.

---

### Post by Penguin Guy on 2009-04-08
You could try DSL Linux, I believe that uses very low RAM (around 35MB), or maybe that is going too far.

---

### Post by Bearly Able on 2009-04-08
I installed Xubuntu 8.04 on an old XP machine with only 128MB RAM and no ethernet card.  I used the alternative install CD with no problems, although unsurprisingly it was very slow.  It ran OK, although I later managed to get second-hand RAM to upgrade it to 256MB which made quite a difference.

---

### Post by cjv8888 on 2009-04-08
+1 for Puppy Linux.
Does the machine has USB ports?
If it does , you can buy a USB wireless adapter for the internet. 
I know a couple which works with little configuration.

---

### Post by neofreud on 2009-04-08
I would also recomend Damn Small Linux [http://damnsmalllinux.org/](http://damnsmalllinux.org/) 

I have used it in the past on some Legacy Hardware and it worked pretty decently. I would not use it on a main computer or as a primary OS by any means but if you just want to do email and editing it should do the trick.

---

### Post by joe m. on 2009-04-08
Thank you everyone for the suggestions.  I might have to go with puppy linux.  

but i do have a netgear wireless pc card.  the problem is that since i don't have an operating system, i have not downloaded the software for it and I guess the ubuntu can't recognize the hardware without it.

Also, the computer does have usb ports, and i have tried to connect it directly through my dsl to the usb port.  but again, i guess the ubuntu simply does not recognize it.

I know the computer is pretty old, but it used to run windows 98 perfectly well, and i am surprised that it is this hard to get it running ubuntu...  there are a lot of people out there with less then current computers who could benefit a lot from a fresh operating system..

thanks everyone.

---

### Post by oldos2er on 2009-04-08
"I know the computer is pretty old, but it used to run windows 98 perfectly well, and i am surprised that it is this hard to get it running ubuntu.."

 Ubuntu is a modern OS with the requirements of a modern OS; Win98 is 11 years old, you're comparing apples to oranges.

 There are plenty of Linux distros available that will run acceptably well on older systems (as has been mentioned in this thread), Ubuntu just isn't one of them.

---

