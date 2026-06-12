---
title: "Running a Mac Program"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Socinus on 2011-05-13
I have a program that only functions on a Mac with Mac OS X 10.5 or later. 

Is there a way to run this program on my Linux machine?

---

### Post by astex on 2011-05-13
There may be a port.

What is the program?

---

### Post by Socinus on 2011-05-13
[http://petteri.kamppuri.fidisk.fi/spellbookmaster/mac/](http://petteri.kamppuri.fidisk.fi/spellbookmaster/mac/)

Yes, I'm a huge nerd.

Ideally I want to run it on Windows, but I've been informed that trying to run a Mac program on a Windows computer is not terribly feasible. 

I've emailed the creator and he has no plans to make the program available for Windows.

---

### Post by dniMretsaM on 2011-05-13
AFAIK there is no way to run a Mac program on Linux. I would think this could be possible with a WINE-like app (maybe even easier than Windows programs since Mac is UNIX-like), but it has not been done yet. If you want to look for an alternative, use [AlternativeTo]("http://alternativeto.net"). You could also dual boot or use a VM.

---

### Post by astex on 2011-05-13
OP, you're on a linux forum.  We're all nerds in some way.

The main problem with porting that application to mac is that it uses aqua as a display manager rather than X11 as is done in Ubuntu.  The GUI programming is a little hard to port.  I would be amazed if there is not a native linux version of this program though.  You may try this thread: [http://ubuntuforums.org/showthread.php?t=777427](http://ubuntuforums.org/showthread.php?t=777427).

---

### Post by dniMretsaM on 2011-05-13
> **astex said:**
> OP, you're on a linux forum.  We're all nerds in some way.

We are geeks. Geek =/= nerd. (<-personal opinion)

---

### Post by srs5694 on 2011-05-13
A virtual machine is your only option for running the program in Linux. That option is a bit dodgey from a license standpoint, since Apple's OS X license states that it's only good for running the software on Apple-branded hardware. (Of course, if you're running Linux on a Mac, that's another matter, but then you'd probably be better of dual-booting.) Running OS X on non-Mac hardware (either directly or in a virtual machine) is a topic that's frowned upon by the moderators here, so if you want to pursue this option, I recommend you take it to a Hackintosh forum.

If you happen to have network-able access to a Mac but just want the user interface on your Linux box, you could use VNC to control the Mac's desktop from the Linux box. I've done this, although not recently. It works tolerably well for casual purposes (and maybe better than that now; I've not really kept up with VNC developments).

If you're desperate enough for it, you could pick up the cheapest Mac you can find that's capable of running OS X 10.5 (the minimum OS for that software). You could even then dual-boot that machine with Linux, if you have any use for two Linux boxes. If you're short on space, a KVM switch is a wonderful thing. I've got three PCs and a Mac hooked up to mine, and I switch between them and use one monitor, one keyboard, and one mouse for all four boxes. This works quite nicely for me.

---

