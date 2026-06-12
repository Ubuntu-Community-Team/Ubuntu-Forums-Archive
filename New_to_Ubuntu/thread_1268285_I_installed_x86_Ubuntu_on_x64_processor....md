---
title: "I installed x86 Ubuntu on x64 processor..."
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Remagen on 2009-09-16
Hey guys, just 2 quick questions.


I've been using Ubuntu for about a month now and I like it very much, but I have one pet peeve.  
1. Whenever I open any application, from terminal to firefox, there is about 3-5 seconds of delay before it actually opens.  Any ideas on how to eliminate that?

2.  I have a 64 bit processor, but was a stupid prick and installed a 32bit copy of Ubuntu.  Is it possible for me to install a 64bit copy of ubuntu w/o nuking my partition etc?

Could 2 be related/the cause of 1?

I would've posted in a different forum, but my account only lets me post here for now...
Also, my specs are:
6 gigs of ram (ubuntu only sees 3 go figure)
Intel 2.4 gHz dual core

Dell XPS 1640
fglrx video driver (ATI card)
I have compiz fuzion installed, plus gnome-do.

---

### Post by Theobalt on 2009-09-16
I might be wrong, but 32 bit OS can't see more than 3 or 4 Go of RAM. So, "upgrading" to a 64 bits OS will solve that problem. 

For the rest... I can't help...

---

### Post by Butthead on 2009-09-16
> **Remagen said:**
> 
1. Whenever I open any application, from terminal to firefox, there is about 3-5 seconds of delay before it actually opens.  Any ideas on how to eliminate that?


Why, are you de-fusing a bomb or something and waiting for the instructions on how to do that to come up? :confused:

Unless it's already loaded into memory, I'm afraid the 3-5 second delay is inevitable.

---

### Post by Remagen on 2009-09-16
Yeah, it's really a non-issue.. but being able to install a x64 copy of Ubuntu w/o nuking my partitions would be great, does anyone know if it's possible?

---

### Post by ElSlunko on 2009-09-16
> **Remagen said:**
> Yeah, it's really a non-issue.. but being able to install a x64 copy of Ubuntu w/o nuking my partitions would be great, does anyone know if it's possible?

Short answer is no. You'll best bet is to backup your home directory and do a fresh install.

---

### Post by 73ckn797 on 2009-09-16
You would have to re-install with the 64 bit. Back-up your data you want to keep. If you have a separate "/home" partition I believe that you could reload with 64 bit on the "/" partition. Do some searching to be certain.

---

### Post by louieb on 2009-09-16
> **Remagen said:**
> 2.  I have a 64 bit processor, but was a stupid prick and installed a 32bit copy of Ubuntu.  Is it possible for me to install a 64bit copy of ubuntu w/o nuking my partition etc?

Your looking a reinstall. You won't have to re-partition if you choose the manual partition option - just tell it to reuse the current install partition and format it - you will loose data,  programs and settings. 

> there is about 3-5 seconds of delay before it actually opens.  Any ideas on how to eliminate that?

Sounds like normal get it off the hard drive time. A faster hard drive would help or Can use something called pre-load that will load applications in advanced.

---

### Post by 73ckn797 on 2009-09-17
I have found that on an initial start-up of a program, that it is a 3-5 second lapse. This is after I have restarted the computer, for whatever reason. Subsequent application start-ups and it loads in about 2 seconds. This whole scenario repeats upon a later restart.

In Windows the same thing happens. A MS app is usually faster at loading but I attribute that to being an "at home" program in Windows.

---

### Post by nhasian on 2009-09-17
i think your talking about the time it takes for the hard disk to read the data from the drive.  The best way to cut the load time of applications is to install an SSD drive :)

alternatively if you have a 4800 or 5400 RPM drive, you can upgrade to a 7200 or 10K RPM drive.  But of course SSD is best if you can afford it :lolflag:

---

### Post by Paqman on 2009-09-17
One thing you can do to improve opening times for apps is install preload. It'll keep track of what stuff you use and start preloading them into RAM for you.

It's especially useful when you have titanic amounts of RAM. Using preload is about the only way you'll ever get any benefit from 6GB on Ubuntu unless you start caning ramdisks.

---

### Post by MrWES on 2009-09-17
> **73ckn797 said:**
> I have found that on an initial start-up of a program, that it is a 3-5 second lapse. This is after I have restarted the computer, for whatever reason. Subsequent application start-ups and it loads in about 2 seconds. This whole scenario repeats upon a later restart.

In Windows the same thing happens. A MS app is usually faster at loading but I attribute that to being an "at home" program in Windows.

I usually utilize that 3-5 seconds to blink a couple of times; when I'm done blinking the program is usually ready to go. Works for me :P

---

### Post by Remagen on 2009-09-17
Yeah, the program startup delay wasn't really an issue.

As for installing x64, the linux club I'm in is having an install fest soon, so I'll just time myself and see how fast I can get a new copy of linux up and going (plus all the tweaks of mine) :)

On an unrelated note, does anyone know how to unbind a gui app from the terminal that launched it?

say I do this in the terminal:
gedit /home/me/whateverfile.txt

If I close the terminal, I close gedit.  I'd like to be able to seperate the terminal from gedit (or whatever app), so I can close it independently, or keep on using the terminal.

The closest I've figured is like ctrl-z (suspending) but freezing gedit isn't exactly a winning option :)

---

### Post by Remagen on 2009-09-17
Yarr, grawity on IRC helped me out on the detaching gui's from the terminal deal.  

Using a function (bash function, so no man page):

function X { ( "$@" &) &> /dev/null; }

X = what you want to call it, I chose 'detach'

"$@" = the program that this function will act upon

I put that snippet into my .bashrc file, so all my bash shells start with it.

To use:

matthew@mlinux:~$ X vlc 
//launches vlc independent from the terminal.

in my .bashrc is:
function detach { ( "$@" &) &> /dev/null; }

So I have to type:
matthew@mlinux:~$ detach vlc

It even works regardless of any args for the apps you're launching too.


Linux :guitar:

---

### Post by 73ckn797 on 2009-09-17
> **MrWES said:**
> I usually utilize that 3-5 seconds to blink a couple of times; when I'm done blinking the program is usually ready to go. Works for me :P

What are several seconds anyway?? It is better than the older forms of communication or relaying info such as, Telephone, Telegraph or tell a woman. Actually the latter may be the fastest of those three (GRIN).

---

### Post by egalvan on 2009-09-17
> **Theobalt said:**
> I might be wrong, but 32 bit OS can't see more than 3 or 4 Go of RAM. So, "upgrading" to a 64 bits OS will solve that problem. 

32bit Ubuntu SERVER kernel will see up to 64GB or RAM.
Or any PAE-enable kernel, for that matter.


> but being able to install a x64 copy of Ubuntu w/o nuking my partitions would be great, does anyone know if it's possible?

> **ElSlunko said:**
> Short answer is no. You'll best bet is to backup your home directory and do a fresh install.


Even shorter answer, 

YES

This will take some work with the partitions, but it is absolutely possible to have multiple OS's.
The record is somewhere above 140 on one machine.

You can share "swap" partitions, but  'boot' 'root' & 'home' should be separate.
Note, they can be labeled something like 'boot64' 'root64' and 'home64' to keep them separate.

I've done this very thing, a 32bit and 64bit on the same machine.

---

### Post by fela on 2009-09-17
> **nhasian said:**
> i think your talking about the time it takes for the hard disk to read the data from the drive.  The best way to cut the load time of applications is to install an SSD drive :)

alternatively if you have a 4800 or 5400 RPM drive, you can upgrade to a 7200 or 10K RPM drive.  But of course SSD is best if you can afford it :lolflag:

10K is nothing. 15KRPM FTW! :)

---

### Post by egalvan on 2009-09-17
> **Remagen said:**
> 
I've been using Ubuntu...I like it very much, but I have one pet peeve.
1. Whenever I open any application, from terminal to firefox, there is about 3-5 seconds of delay before it actually opens.  Any ideas on how to eliminate that?


Well, get yourself a dual quad-core, with 128GB of RAM,
use 15k-RPM drives (as fela suggested)
create 128GB of swap
start up every program you will ever use
never re-boot
never shut down  :lolflag:

Sorry, I couldn't resist...

Seriously, as others have pointed out, when you launch a program for the first time,
the system has  to go to the drive and read it into RAM.
That is a (comparatively) lengthy operation.

A faster drive is about the only answer,
or my tongue-in-cheek one above...


And don't laugh too much, I knew a guy who did basically that...
started every program he used on a regular basis, 
and didn't reboot.
Power outages were his bane. :)

And many laptop users never shut down or re-boot..
they call it "hibernation"

---

### Post by corncob on 2009-09-17
> **Theobalt said:**
> I might be wrong, but 32 bit OS can't see more than 3 or 4 Go of RAM. So, "upgrading" to a 64 bits OS will solve that problem. 


I would say you're right.  3.5 is what I heard.

I seem to have noticed a couple second delay in opening Firefox, etc after I installed BOINC Manager.  Its supposed to relinquish the CPU when you start doing something but I guess it takes a couple seconds.  Actually, according to
```
top
```
its still running even after I shut it down.

---

### Post by fela on 2009-09-17
> **egalvan said:**
> <snipped>

And many laptop users never shut down or re-boot..
they call it "hibernation"

I often hibernate my desktop :P

Only Linux seems to do it right on my computer, but I never use windows except for GTAIV anyway so that don't matter.

> **corncob said:**
> I would say you're right.  3.5 is what I heard.

<snipped>

This will clear things up a little:

basically a 32 bit OS can address up to 2^32 bytes of memory, which is exactly 4 GiB (Gibibytes) - a GiB is 1024 MiB, which is 1024 KiB, which is 1024 bytes. However, this memory space includes anything on the system that has RAM or ROM memory on it, such as graphics cards and PCI cards. Generally the only component with a significant amount of RAM apart from the main RAM is the graphics card, so the general rule of thumb is that on a 32 bit OS without PAE enabled (which is an extension to enable 36 bits wide memory addressing, ie 2^36 bytes), the amount of accessible memory is 4GiB minus the amount of graphics memory. There's sometimes different factors though, but they are governed by the OS kernel.

PS. I'm not sure how PAE works but there's always wikipedia :)

---

