---
title: "[SOLVED] LiveCD won't work on my Dell"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Tu1J4kXk8NUhMz on 2009-01-08
I'm trying to load up my Ubuntu Live CD on a Dell Dimension 4600 (an older model, but not too old). Specs live up to System Requirements no problem, but for some reason the disk gets through everything, then stops at loading the background and the mouse cursor. No top bar, nothing.

I happen to have a Knoppix distro disk as well, and that won't even load up the X Windows session properly. It just loads into the session, it seems to struggle through properly dimensioning the screen, then takes a dump.

I just tried loading the Ubuntu Live CD again in Safe Graphics mode, and all I got was a billion lines of errors. Something about line fragment, a cache maybe. Hard to read because they scroll so fast.

---

### Post by MyR on 2009-01-08
if you downloaded & burned the disc:
You could
1. check the md5 of the download
2. have the disc check itself for errors or
3. burn the disc again (after checking the md5)

Or you could try just starting the panel. once the desktop loads, type alt+F2 and enter gnome-panel

peace

---

### Post by kk0sse54 on 2009-01-08
> **MyR said:**
> if you downloaded & burned the disc:
You could
1. check the md5 of the download
2. have the disc check itself for errors or
3. burn the disc again (after checking the md5)

Or you could try just starting the panel. once the desktop loads, type alt+F2 and enter gnome-panel

peace

You can try that or try the alternative text based installer cd
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by handydan918 on 2009-01-08
Looking at the specs on your box, it seems that it came with either an ATI or an Nvidia graphics card. Once you know which (lspci) you might indeed try the alternative installer, or you might try Mint, or Mepis, both of which include some drivers for these cards.

---

### Post by Tu1J4kXk8NUhMz on 2009-01-08
> **handydan918 said:**
> Looking at the specs on your box, it seems that it came with either an ATI or an Nvidia graphics card. Once you know which (lspci) you might indeed try the alternative installer, or you might try Mint, or Mepis, both of which include some drivers for these cards.

As far as the disk goes, the disk is great. I've installed using the Ubuntu CD on a MacBook Pro already and it's worked fine. 

Additionally, I just realized I didn't mention I'm doing some data recovery work, so I'm not installing. As far as the specs, I've upgraded the video card, though I think it's still Nvidia.

Oh, and as an update, I've tried a Damn Small Linux LiveCD and it didn't work either.

---

### Post by Tu1J4kXk8NUhMz on 2009-01-09
bump

---

### Post by handydan918 on 2009-01-09
If you have an nvidia card, I'm not sure you are going to be able to get it to run without an install. As I mentioned before, Mepis can allow you to load the O/S into memory, and install the nvidia driver via the mepis x-assistant. I really don't think Ubu is capable...
perhaps someone will show you the error of my ways.
:)

---

### Post by Tu1J4kXk8NUhMz on 2009-01-09
> **handydan918 said:**
> If you have an nvidia card, I'm not sure you are going to be able to get it to run without an install. As I mentioned before, Mepis can allow you to load the O/S into memory, and install the nvidia driver via the mepis x-assistant. I really don't think Ubu is capable...
perhaps someone will show you the error of my ways.
:)

I was afraid that was the case. If nothing else, I'd like to know what distro(s) WILL run off the LiveCD...

---

### Post by WitchCraft on 2009-01-09
> **teamjh14 said:**
> 
Additionally, I just realized I didn't mention I'm doing some data recovery work, so I'm not installing. 


You said you have installed it previously on a MacBook. 

So if you have a working system, why don't you just take out the hard-disk from the system you have to recover, and read it out and backup the data via your MacBook?
That way you don't have to install anything...


> **MyR said:**
> 
2. have the disc check itself for errors


How do you do that ?

---

### Post by Tu1J4kXk8NUhMz on 2009-01-09
> **WitchCraft said:**
> You said you have installed it previously on a MacBook. 

So if you have a working system, why don't you just take out the hard-disk from the system you have to recover, and read it out and backup the data via your MacBook?
That way you don't have to install anything...

Oddly enough, the disk I'm using the LiveCD on is the "good" disc which I am backing up TO. The data I'm trying to recover is on an external hard drive. Long story short, I put the "good" disc into my Dell, then found out I may have the disc formatted in HFS+, which Windows can't read. Basically, I'm trying to avoid having to pull apart my Dell again, put the disc in the external enclosure, reformat, and reinstall (which it's looking like I'll have to do anyways). That's all assuming, of course, there's no good data in this HDD.

> **WitchCraft said:**
> 

How do you do that ?

Load up the disc, and there's an option that says "Check Disc For Errors" on the bottom, after language selection.

---

### Post by Tu1J4kXk8NUhMz on 2009-01-09
Nevermind. Went through the annoying process, as trying to find something that WILL work with my Dell would probably be more effort than just swapping and reformatting. Thanks!

---

