---
title: "Hopefully Last Post about Random Kernel Panics"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by zorbama on 2011-08-03
Hello people,
I'm sorry about creating three threads in the same subject, but I think it's better to start from the beginning, because nothing is clear to me yet.
Since the very first day I installed Ubuntu, I'm having a problem of kernel panics happening at random points. I tried several solutions, including trying different graphic drivers, cleaning the tower from dust, running memtest for errors, installing extra programs and more, but nothing seems to have solved it, as to this very day my kernel panics every so often.
on the proprietary nvidia graphic driver, I only see the screen frozen and the caps lock and num lock leds blinking, but on the freeware experimental driver I can see an error message, and I managed to take a photo: [http://oi53.tinypic.com/be639g.jpg](http://oi53.tinypic.com/be639g.jpg)
The session that started right after this photo panicked rather quickly after it loaded, and I saw there was a longer message, but I wasn't ready and didn't manage to take a good photo.
From running a little bit of information on mcelog and some Internet searching (and also because it was written in the kernel panic error text), I found it might be a problem related to the hardware, although I'm not sure what that means or if it's even right.
Does anyone have any idea what this might be? It's the only serious problem I'm having with Ubuntu. Once it's off, I'll be a very happy user. :)

Note that while I'm not completely void of computer education, there are many things I don't know. I'll appreciate it very much if you explain the different terms to me so that I'm completely sure about what I'm doing.

Thanks in advance!

---

### Post by Jouke S on 2011-08-03
could you post the output of terminal command ```
uname -a
```?

---

### Post by zorbama on 2011-08-03
Yes, this is what I see:
Linux amir-desktop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by gandaran on 2011-08-03
you should try other Linux distributions just to see if they work without problems on your PC and rule out if your hardware can work or not with Linux.

---

### Post by zorbama on 2011-08-03
Okay, I will.
I did try Kubuntu for a while, but I'll go and see if Fedora does the same problems.
I'll reply again once I see how it works.
Since it's getting late, it probably won't be today.
Thanks for the idea, and I'll see what happens next. :)

---

### Post by Jouke S on 2011-08-03
I assume you've picked and installed the right Ubuntu version (X86), it is possible that some of your other hardware isn't supported, though. 
[http://hardinfo.berlios.de/HomePage](http://hardinfo.berlios.de/HomePage)
this piece of software will give you a list of installed hardware which you can then use to check if they are supported. 
Old and rare hardware is most likely to not be supported

---

### Post by zorbama on 2011-08-03
By X86, what do you mean? If it means 32bit, then that's what I have.

---

### Post by zorbama on 2011-08-03
Whoops, seems like I might have stumbled upon the problem: while running the computer through Fedora's installation disc, the "Disk Utility" program suddenly popped up and warned me that there was an error with my disk. When I opened it up I saw that there are 149 bad sectors on my hard drive. When loading back to Ubuntu, it seems to say in most places that there are only a few bad sectors, but in the area where it showed the bad sectors in Fedora, it shows the same amount and gives the same warning. I'm now running a long checkout to make sure about it, and I might also try windows' tools to check hard drives in order to make sure about it.

---

### Post by zorbama on 2011-08-04
Okay, here's the situation as of now:
After trying to install Ubuntu on another hard drive, one that didn't seem to have any problems, the kernel panicked again, while I was trying to make Synaptic read the markings from my previous installation. Since this already happened to me several times and I had to go through hell to get Synaptic to work again, I decided to leave my computer alone for the time being. I'm now using my father's Windows 7 computer. I can't possibly fathom what might be the cause of those panics, and while I can handle the computer with them, it's getting very tiring and I have no idea what to do, or what's causeing this. Any idea how I can figure this out? I'm completely clueless here.

---

### Post by zorbama on 2011-08-04
> **Jouke S said:**
> I assume you've picked and installed the right Ubuntu version (X86), it is possible that some of your other hardware isn't supported, though. 
[http://hardinfo.berlios.de/HomePage](http://hardinfo.berlios.de/HomePage)
this piece of software will give you a list of installed hardware which you can then use to check if they are supported. 
Old and rare hardware is most likely to not be supported

Sorry for posting 4 messages in a row, but I tried what you said and made a report of my hardware and I have no idea what to make of it, since there's a lot of information and it's quite confusing. What should I do with it?

---

### Post by zorbama on 2011-08-17
Gonna have to bump this. After trying to switch a power supply and a hard drive there's no luck: I'm still getting kernel panics at random. I'm not sure what to do next, though I'm quite certain it's a hardware problem. Any idea, anyone?

---

### Post by korb on 2011-08-21
I'm seeing a similar issue. I'm installing on a Dell XPS M1730 that has been running 32-bit 10.04 for over a year. I just upgraded to 8GB RAM, and decided I would need a 64-bit install if I wanted to use all of that memory (and why wouldn't I?).

After about 10 attempts, I got the installer to work and got 11.04 installed, but now I am trying to boot from the installation CD again so that I can run gparted to move my root partition. I have tried booting about another ten times, and just about every attempt has ended with "panic occurred, switching back to text console" and the caps & num lock LEDs flashing.

I've seen some posts that imply this is a bug and/or related to "unsupported hardware."

[LIST]
[*][One very similar to this that was allegedly fixed back during alpha]("https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/712082")
[*][URL="http://ubuntuforums.org
/showthread.php?t=1744154"]This one has a photo of the user's screen, and it looks virtually identical to mine[/URL][/LIST]

I also tried to boot from the 10.04 64-bit desktop CD that I used to build several non-laptop systems, (including the one I am typing this message on) and see the same problem.

I'm guessing it is indeed 64-bit and hardware related, and I am very disappointed as I really need that additional RAM. :(

---

