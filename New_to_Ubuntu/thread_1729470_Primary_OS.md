---
title: "Primary OS"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by IronMaidenMN on 2011-04-15
Hello, I'm a noob to this forum and linux, I have a friend who talks about it all the time with me. I'm currently building a new gaming rig. I'm not wanting to spend money to buy windows 7 (And I don't torrent). I'm currently using windows xp sp3 32-bit, would switching to linux ubunto from my current os be a smart move? I want a os that doesn't have all the useless crap that I never use. I also just started college classes for CIT. 

Would all I have to do is burn the os onto a blank dvd/cd and install it and I would be good to go?

Thank you for your time.
Iron.

---

### Post by mikewhatever on 2011-04-15
Linux is very easy to install and use these days, but it's probably not the best choice for a gaming rig. I am afraid you'll have to shell out some cash for W7.

---

### Post by 3rdalbum on 2011-04-15
> **IronMaidenMN said:**
> Hello, I'm a noob to this forum and linux, I have a friend who talks about it all the time with me. I'm currently building a new gaming rig. I'm not wanting to spend money to buy windows 7 (And I don't torrent). I'm currently using windows xp sp3 32-bit, would switching to linux ubunto from my current os be a smart move? I want a os that doesn't have all the useless crap that I never use. I also just started college classes for CIT. 

Would all I have to do is burn the os onto a blank dvd/cd and install it and I would be good to go?

Thank you for your time.
Iron.

Basically, yes. You download the ISO disc image and use your burning software's "burn image to disc" function to create the Ubuntu CD. Boot up your computer from CD (you might need to change your BIOS' boot order first) and you'll be given the option to try Ubuntu from CD, or to install it. Click Try Ubuntu, try it out and check that wifi and sound work. Don't worry if MP3s and stuff don't play, support for these can be easily added.

Once you know that your computer works with Ubuntu, then double-click the Install icon on the desktop and install it. You can do a "dual-boot" setup where Ubuntu and Windows coexist independently and you can choose which to boot into every time you turn the computer on; or if you really don't want Windows on there you can erase your hard disk in the installer and have Ubuntu as the only operating system.

***_Either way, make sure you have a backup of all your important files first._***

---

### Post by rosencrantz on 2011-04-15
If you consider gaming on Ubuntu you'll have to run the Windows executables via the Wine emulator. Depending on the game, this works well or doesn't. Check wine's appDB to see what works.
What are your planned hardware specs? People around here should know whether anything causes trouble with Ubuntu. 

On the whole, go for it, at least for a dual boot. Ubuntu comes with tons of extremely useful crap, all for free and nicely organised ;-)

---

### Post by deconstrained on 2011-04-15
> **IronMaidenMN said:**
> Hello, I'm a noob to this forum and linux, I have a friend who talks about it all the time with me. I'm currently building a new **gaming rig**. I'm not wanting to spend money to buy windows 7 (And I don't torrent). I'm currently using windows xp sp3 32-bit, would switching to linux ubunto from my current os be a smart move?
...
I also just started college classes for CIT. 
The short and simple: if you're going into college, **don't** (with gaming-related stuff). Don't spend any more than you need to on computer parts for making games run better, and don't play games, for that matter. Save money and time, focusing it instead on finding research and development opportunities at the undergraduate level at CIT, to get your career started early. I sure wish I had. Linux doesn't need high-end hardware to run well, so that should be the least of your concerns.

If you've already purchased a high-end graphics card and it's ATI, you're going to run into problems with Linux; NVidia has much better 64-bit support that's been around for years, while stable & reliable 64-bit support in Linux for ATI graphics is just beginning to coalesce. Graphics are sort of important on Linux (compiz!!!*) but not very important.

If you haven't bought the hardware yet, splurge with the CPU; you'll be able to compile code faster, run your code faster, and if you get a 4+ core CPU you'll be able to do more extensive testing of parallel and multithreaded programs (if you're into that sort of thing; I for one develop simulations that use MPI, and having an Athlon II X4 640 in my beast of burden is a tremendous convenience).

Also, get 2+ hard drives and make a software RAID, so that you are less likely to lose all your hard work to a hard drive failure. Linux is way better than Windows at managing software RAID. Or...get a motherboard with reputable RAID capabilities, or a decent controller, and set up a hardware RAID, which would perform better (especially if the array you want to set up does striping/parity blocks, such as RAIDs 3-5 & 1+0).

* Compiz has tremendous advantages for productivity (i.e. window-juggling and such), provided you have the maturity to not play with it all the time (it took me a few months to get over it). Once you customize all the key/mouse shortcuts and grow used to it you'll wonder how you ever got by without it before.

---

### Post by Learning Linux 2011 on 2011-04-15
> **IronMaidenMN said:**
> Hello, I'm a noob to this forum and linux, I have a friend who talks about it all the time with me. I'm currently building a new gaming rig. I'm not wanting to spend money to buy windows 7 (And I don't torrent). I'm currently using windows xp sp3 32-bit, would switching to linux ubunto from my current os be a smart move? I want a os that doesn't have all the useless crap that I never use. I also just started college classes for CIT. 

Would all I have to do is burn the os onto a blank dvd/cd and install it and I would be good to go?

Thank you for your time.
Iron.

I would think your college would dictate what kind of operating system to use.  It probably uses Windows.

Linux isn't much for gaming, especially if every frame per second (fps) matters to you.  You can install Windows games using WINE, which actually allows you to run many Windows programs inside Linux.  WINE also has an extension called "Play on Linux" that is specially designed for Windows game playing.

---

### Post by deconstrained on 2011-04-15
> **Learning Linux 2011 said:**
> I would think your college would dictate what kind of operating system to use.  It probably uses Windows.
Why the heck would it?

Going to UCSC I remember that Windows computers were all required to connect to the wireless AND wired LANs using a terrible, terrible program called Cisco Clean Access that would crash, die, and crash some more. I went through undergrad studies using a PowerBook G4 and never had to experience that horror, but my friends always bitched about it.

So, I'm inclined to think that the potential for worms and malware to spread over networks often prompts more strict rules to apply to Windows clients connecting to them.

---

### Post by Learning Linux 2011 on 2011-04-15
> **deconstrained said:**
> Why the heck would it?

Going to UCSC I remember that Windows computers were all required to connect to the wireless AND wired LANs using a terrible, terrible program called Cisco Clean Access that would crash, die, and crash some more. I went through undergrad studies using a PowerBook G4 and never had to experience that horror, but my friends always bitched about it.

So, I'm inclined to think that the potential for worms and malware to spread over networks often prompts more strict rules to apply to Windows clients connecting to them.

I think UC Santa Cruz, as almost all UC campuses, use Unix/Linux.  I used to live near there :-)

The poster mentioned he was entering a Computer Information Technology program, which usually teaches Windows networking.  You almost always have to use what the college recommends, especially in a program that specifically teaches computers.

---

### Post by beew on 2011-04-15
> **rosencrantz said:**
> If you consider gaming on Ubuntu you'll have to run the Windows executables via the Wine emulator. Depending on the game, this works well or doesn't. Check wine's appDB to see what works.
What are your planned hardware specs? People around here should know whether anything causes trouble with Ubuntu. 



Why? there are quality games that run natively in Linux as well. Why assume OP has to  run Windows games?

---

### Post by K_45 on 2011-04-15
> **Learning Linux 2011 said:**
> I think UC Santa Cruz, as almost all UC campuses, use Unix/Linux.  I used to live near there :-)

The poster mentioned he was entering a Computer Information Technology program, which usually teaches Windows networking.  You almost always have to use what the college recommends, especially in a program that specifically teaches computers.

Not necessarily. The world does not revolve around Windows or the Ipad. And networking implies connections to other OS's. If the instructor is any good, he would have no problem with a linux slant, so to speak.

---

### Post by rosencrantz on 2011-04-15
@deconstrained: cut the kid some slack ;-) Other people just waste their time on forums...

I've never been to a US college in a student capacity -  my old university cared a rat's *** about what we were running and even offered Linux Howtos. Still, you should be allowed to install what you like on your home desktop.
Iron, if you need Windows (for homework and such!) and can't afford it, check whether your college is a MSDN Academic Alliance member or whether there are any special student deals - Microsoft should have an interest in binding all the geeks to their platform.

---

### Post by Learning Linux 2011 on 2011-04-15
> **rosencrantz said:**
> @deconstrained: cut the kid some slack ;-) Other people just waste their time on forums...

I've never been to a US college in a student capacity -  my old university cared a rat's *** about what we were running and even offered Linux Howtos. Still, you should be allowed to install what you like on your home desktop.
Iron, if you need Windows (for homework and such!) and can't afford it, check whether your college is a MSDN Academic Alliance member or whether there are any special student deals - Microsoft should have an interest in binding all the geeks to their platform.

Yeah, that is a good point.  If your college requires MS, you can usually either get a free copy through the school, or you can purchase a copy online for like $29 (last time I checked).

---

### Post by Learning Linux 2011 on 2011-04-15
Don't get me wrong, I'm not advocating MS, I'm simply saying that many schools don't allow you to use any products other than what they teach, and most colleges (especially Information Technology programs) teach Microsoft.  If anyone here genuinely had a choice in what operating system and software you used in college, consider yourself lucky as that is unusual in my experience, mostly due to the fact that the faculty doesn't know enough about other operating systems.  Most faculty believe that corporations will be using MS products, therefore that is what they teach.  That has been my experience.

---

### Post by Locke_99GS on 2011-04-15
I'm curious what the OS on your personal computer has anything to do with school? I'm a Computer Science major at Indiana University, and have only for one language class (Spanish) required Windows. Most of my professors never know what OS I'm using, and the ones that do have no issue with it. 

Furthermore, in the U.S., a school does not have the right to dictate what software you choose to run on your personal computer. Though, if you choose an OS that isn't capable of performing the work you're required to do, you'll have problems getting your work done, which is also true in a business environment.

---

