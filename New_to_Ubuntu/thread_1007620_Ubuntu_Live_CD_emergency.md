---
title: "Ubuntu Live CD emergency"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by jaydeesan on 2008-12-10
So I was playing with the newest version for just over a day, and seeing how things went well and I thought that I was finally ready to install it and start using it full time - I got a bit carried away... and ended up with about 40 tabs opened in Firefox. That of course shouldn't be a problem in itself, but I just clicked on an embedded youtube video in one of those tabs and long story short, the computer locked up. And byt that I mean locked up so hard like I've never seen a computer do before. Certainly not something I expected with a Linux distro. It doesn't seem to respond to absolutely anything.

I don't know if there's anything that can be done to revive this thing, but there was a bunch of links opened that I have no idea how I ended up at that I would really like to bookmark...

... and more importantly, I started to take some notes into a TXT file that I haven't yet saved to the HDD partition and I really REALLY don't want to lose that.

Any suggestions? :confused:

---

### Post by Michael.Godawski on 2008-12-10
Do you mean you installed Ubuntu to the harddrive or was still in the Live Session?

---

### Post by jaydeesan on 2008-12-10
Sorry I could have written that part more clearly... _it's still the live cd session_ (I just meant that I have decided to install it later on today once I cleaned some HDD space up)

---

### Post by Michael.Godawski on 2008-12-10
The live CD uses only your RAM. So... Firefox is a RAM eater by itself and when you decided to open so many tabs, the RAM probably did not suffice.

Secondly, you cannot save any changes to the harddrive, since the Live CD uses only the RAM, as mentioned above. Use a real-life pencil and paper instead :p.

When you install the system to the hard drive, you will see a remarkable speed boost compared to the Live CD.

---

### Post by bobnutfield on 2008-12-10
> **jaydeesan said:**
> Sorry I could have written that part more clearly... _it's still the live cd session_ (I just meant that I have decided to install it later on today once I cleaned some HDD space up)

With that much activity from a live session, I am guessing that you have overloaded your memory and/or graphics memory.  You are not likely (unless someone advises you differently) to "unfreeze" it under those circumstances.  The live cd does not touch your hard drive so no real harm has been done, so I would cut your losses on that session and do a hard shutdown (power switch held down for about 10 seconds).  Unless you save your work to a USB stick or cd, everything is gone on reboot after a live cd session.

---

### Post by jaydeesan on 2008-12-10
I had the system monitor running to see how the resources are doing (one of the things I was watching). I know that what I was doing with Firefox would basically kill the comp on Windows (this has been my pet peeve with Firefox for a looooong time now) but everything was running fine, low CPU util and memory usage was only 480 MB out of 1 GB (it would have been 100% and well over  a gig on Win) until of course I clicked on that stupid youtube video...

I was planning to bookmark all the tabs and then export and save bookmarks onto HDD.

As for the TXT file -  that's the thing, the FFX window is on top and I can't do ANYthing (that I can figure out) to at least bring the editor up to copy the stuff manually. :(

Was hoping there might be some secret Linux ctrl-alt-del alternative or something that would at least allow me to kill FFX (I guess this is where my Linux noob-ness show up real well, hehe)

* or better yet, some way to just kill Flash/java or whatever it is that's hung...

---

### Post by roger_1960 on 2008-12-10
Hi

If alt-F2 gives you a command GUI, type the command xkill and then click on the firefox window with the mouse to kill the process.

---

### Post by jaydeesan on 2008-12-10
Thanks, but no response. I think I'm gonna give up... :(

---

### Post by Michael.Godawski on 2008-12-10
Usually you cannot save anything to hdd during the live cd session. Or do are you planning to dual-boot? If you somehow manage to break the crash status save the bookmarks to an usb stick.

---

### Post by jaydeesan on 2008-12-10
Yeah, it's gonna be dual boot with XP Pro (on Toughbook 51)

(I don't see any reason why I wouldn't have been able to save to either USB or storage partition on HDD... ?)

Anyways, thanks guys but I'm gonna hard-restart it now, it seems pointless... (and this noob here thought Linux is not supposed to get killed so easily... hm)

---

### Post by sneeks on 2008-12-10
hi mate,have just done exactly what you said you were doing just to see how my old system did in the same scenario,i opened 32 tabs,some with video,and then a you tube page and ran the video,it used about 350mb of ram but my poor old p4 3ghz was a struggling,and the graphics card also was having a hard time.
please bear in mind that the live session has to go back to the cd to re-read some stuff as well,so it is no wonder it gave up the ghost.
remember that the live cd is just for test purposes,before a full install,to give you an idea of what it is all about.
if you want to run Linux from a CD please use or try one of the smaller distro's like puppy as this has a lot smaller footprint,so will be quicker from the disk,,plus puppy loads everything into ram,as it is only about 80mb now,(used to be 60mb a while ago,but now has more apps).

or if you want,put Ubuntu on a usb drive,and run it from that,8 gig sticks are really cheap now,so off you go.

---

### Post by handydan918 on 2008-12-10
> **jaydeesan said:**
> (and this noob here thought Linux is not supposed to get killed so easily... hm)

I guess it's all relative...try running Windows from a live cd!

:p

---

