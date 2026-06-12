---
title: "Black screen (with cursor) at boot"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by psychlopath on 2009-11-12
I began having this problem after I determined (via these forums) that the kernel has mysteriously vanished after an update;  It would only go to the memtest.  

SO, I use my USB drive to reinstall 9.10 (NBR).  Several installs later (swapping between NBR and standard) I FINALLY get the thing to boot.

BUT, I find out that about every 2nd or 3rd boot, it will revert back to this black screen with the flashing cursor.  

When it does this, I reboot, get a GRUB menu and some times get it to boot normally.  It'll typically take two or three shots to load properly.  

Once it decides to work, I then seem to have about 2 or 3 more boots before getting the black screen.  

Before reinstalling this, I never had this problem, even once.  So, I'd guess it wouldnt be a graphics driver, as one search suggested.

I'm not finding a ton of info on this problem?? Ideas, anyone?

Ok, I'm off to post on another problem I have when it DOES decide to boot.

If my hardware matters, it's a new Acer Aspire 1 D250-1842.

Thanks for any help.

---

### Post by psychlopath on 2009-11-12
If it matters, the pattern is just about down to a science.

It will go something like this: Boot fine, boot fine, blank screen, grub menu (and blank screen after), grub menu (and blank screen after, boot fine, boot fine, etc, etc.

And bump.

---

### Post by Bunnybugs on 2009-11-12
> **psychlopath said:**
> If it matters, the pattern is just about down to a science.

It will go something like this: Boot fine, boot fine, blank screen, grub menu (and blank screen after), grub menu (and blank screen after, boot fine, boot fine, etc, etc.

And bump.

Have you completely reinstalled???

I think that GRUB is broken...

Make some back-ups and reinstall from scratch! format your drives, and leave the partitions!

---

### Post by psychlopath on 2009-11-12
I have reinstalled several times, using a USB drive.  I thought maybe I'd had a corruption of the ISO files (I WANT the NBR, but I have an ISO of standard and NBR), so I'd make a bootable usb and run the "Check CD for errors," and told that everything was peachy.  

So I'd reinstall.  Have the same problems (plus a few more), get frustrated and reinstall again.  I've done it over and over.

As of now, I have a standard desktop thats on there and it's still doing something.  

Am I missing some crucial part of the install?  When it comes time, I always select the option to have the installer format the drive.

-David

---

### Post by Bunnybugs on 2009-11-14
Weird, never seen this problem before...

What kind of computer do you use?

---

### Post by psychlopath on 2009-11-14
I'm using a shiney new Aspire One d-250.  

Erg, this thing is giving some crazy problems.  It's funny how smoothly it went the first time.  When I had access to wired connections, it installed right away..never a problem...found my wireless cards...connected to access points.

NOW that I have a painfully slow connection and no wired connection at all as well as very little time, it munched the kernel, wont do a proper install to save my life, took DAYS to get it to find the wireless card and then it wouldnt connect to access points after it found the card.

I'm in process of doing a 50th install as I type.

I think that as soon as I get my restore DVDs, windows is going right back on and once I cool down, I'll dual boot it so I can fool with it and not have to rely on it.

---

### Post by pootan on 2009-11-14
I installed Ubuntu on my mothers Acer and had a lot of issues. I eventually found this:

[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

It worked out of the box with no problems. Have a look in the FAQ in particular the second from last QA.

---

### Post by psychlopath on 2009-11-14
Thanks for that hint.  That's what I had decided to use first..I cant remember why I decided against it.  I think I, at the time, had some kind of thought of "Well, if it's designed for an eeepc..maybe it wont do so well on the acer?  Oh, lookie! Here's a Ubuntu, Net Book Remix! THAT will be what I need!"  

And...for a time...it was.

---

### Post by Bunnybugs on 2009-11-14
Well, I've heard some trouble about eeebuntu... And I really think that you should stay at the real distributions, not the copied versions of a distro...

I don't know what the problem is... I guess that Grub is broken... have you tried to redownload the .Iso from ubuntu.org?

---

### Post by psychlopath on 2009-11-14
I would like to try to download it again, but it has the file listed as "2y31d1h remaining," and I'll be out of this country by then.  The live cd should be here by then anyhow.

:D

---

### Post by webless on 2009-11-19
Same problem, same machine. I've installed both UNR and the standard desktop from scratch and have the same problem.  

I've also noticed that sometimes in GRUB the timeout will be there and sometimes it is missing.

I'm dual booting with Windows 7 Starter right now just to have a reliable OS, and 7 Starter sucks.

If a solution is found, please someone post it.

---

### Post by webless on 2009-11-20
Bump?

---

### Post by webless on 2009-11-20
I've also noted that if you boot in recovery mode you can see that it usually hangs right after IRQ 16 

Whatever that means?

---

### Post by psychlopath on 2009-11-20
Ok, it's working now.  After what I thought was working before, it decided to revert back to it's old tomfoolery.

Anyhow.  SO, I spent the last 5 days (yah, yah.  It's THAT slow of a connection) downloading a shiny new copy of the NBR.

Installed several times with a USB.  

No go.  In fact, it seemed to progress further and further in to the realm of not working.  My computer was a paperweight.  A brick.  A lump, etc, etc.

WELL, I had ordered an external DVD burner in the mean time and it showed up.  So after doing a checksum on the new download, I made a live CD of my very own. 

Installing off of that took some doing.  

BUT, I now have a (for now) working copy of Ubuntu.  I dont need to re-boot several times to get it to work.  It's just boots right up and gives me a Ubuntu screen.  Good for me!!

I EVEN was able to install the drivers for my wireless card off of the CD.  Something that, with the USB version, took a bit of fenageling.  

Now...to figure out why it wont log onto any of these access points.  Again.  

So far, I'm finding out that it may be "Set to the wrong region."

If I knew how to mark this as "Solved," I would.  And add that the CD install seems much more stable than the USB.

---

### Post by webless on 2009-11-20
> **psychlopath said:**
> Ok, it's working now.  After what I thought was working before, it decided to revert back to it's old tomfoolery.

Anyhow.  SO, I spent the last 5 days (yah, yah.  It's THAT slow of a connection) downloading a shiny new copy of the NBR.

Installed several times with a USB.  

No go.  In fact, it seemed to progress further and further in to the realm of not working.  My computer was a paperweight.  A brick.  A lump, etc, etc.

WELL, I had ordered an external DVD burner in the mean time and it showed up.  So after doing a checksum on the new download, I made a live CD of my very own. 

Installing off of that took some doing.  

BUT, I now have a (for now) working copy of Ubuntu.  I dont need to re-boot several times to get it to work.  It's just boots right up and gives me a Ubuntu screen.  Good for me!!

I EVEN was able to install the drivers for my wireless card off of the CD.  Something that, with the USB version, took a bit of fenageling.  

Now...to figure out why it wont log onto any of these access points.  Again.  

So far, I'm finding out that it may be "Set to the wrong region."

If I knew how to mark this as "Solved," I would.  And add that the CD install seems much more stable than the USB.

I guess I'll round up a USB CD drive and give that a go. It is extremely frustrating and I never had the option to install any drivers during the installation process. I did enable the wireless drivers during one of the rare boots and it works fine, LED light and all.

---

