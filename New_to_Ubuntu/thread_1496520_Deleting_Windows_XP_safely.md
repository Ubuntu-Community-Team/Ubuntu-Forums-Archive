---
title: "Deleting Windows XP safely?"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by OpalGirl on 2010-05-29
Hello, community gurus. My situtation is this:

I'm running 9.10 on an Asus Eee 900HA, dual-booting with the factory-installed Windows XP Home. I have no Windows-specific applications tying me to XP on this particular computer, and now that I know Ubuntu works reliably and well, I'd like to scrap XP and get my disk space back.

My thought was to delete the Windows partition via Disk Utility or boot from my flash drive and use Gparted. Is it safe to do this, or will I break things, namely GRUB?

---

### Post by kaldor on 2010-05-29
All I ever did was use the Gparted live CD and remove the Windows partition. I then resized the blank space and merged it with the Linux partition; pretty easy to do, and it never messed up my grub.

But remember, partitioning is still risky... back up some of your important stuff first (maybe upload to Ubuntu One if you have no other way)

I'd also recommend using 10.04 instead of 9.10; the Koala has a lot of problems with multimedia and audio which may drive you insane.

---

### Post by OpalGirl on 2010-05-29
@kaldor:

Thank you!

Actually, my audio and multimedia playback in 9.10 is fantastic, and I'm a bit leery that 10.04 may break some things.

---

### Post by kaldor on 2010-05-29
You're a lucky one with Karmic then. Sound issues abundant for me and lots of others! Couldn't even play a DVD even with the right codecs installed :(

Word of advice though.. don't bother upgrading Ubuntu from the update manager. Back up, wipe your hard drive, and install new versions fresh. That way there are no problems related to clashes between new and old.

---

### Post by OpalGirl on 2010-05-29
@kaldor: My netbook has no optical drive, so I can't speak for disc playback, but Karmic handled my digital collection of music and videos swimmingly.

---

### Post by kaldor on 2010-05-29
> **OpalGirl said:**
> @kaldor: My netbook has no optical drive, so I can't speak for disc playback, but Karmic handled my digital collection of music and videos swimmingly.

Very lucky indeed! What netbook do you have? I'll be needing one soon and want to be sure Linux will work out of the box. ( [http://ubuntuforums.org/showthread.php?t=1492119](http://ubuntuforums.org/showthread.php?t=1492119) )

---

### Post by OpalGirl on 2010-05-29
It's an Asus Eee PC 900HA, 8.9" display, 1.6Ghz Intel Atom, 1GB RAM, 160GB HDD. It comes with Win XP Home by default. Depending on what I'm doing, I average about 2--2 1/2 hours battery life(but I can stretch it). I picked it up in March of '09 for about 350$ CAD. (From your thread, your budget is going to be the killer, unless you get a really good sale).

They're lovely little machines, this model of Eee, but I don't know if they're still sold new.

---

### Post by kaldor on 2010-05-29
I guess I'll have to make my budget a bit higher; too hard to get what I want, I thought they'd be cheaper due to their size/performance :(

Love the eeePC line.. great little laptops. Their bundling of Xandros killed Linux for a while though I think lol

---

### Post by OpalGirl on 2010-05-29
Okay, so Windows is gone and I have some 80GB+ of unallocated space. Yay. GRUB is un-broken and all is well.

Two questions, o community:

1. Is there any way to remove the Windows entries from GRUB?

2. When I load up Gparted from the LiveUSB, this is what I see:

[IMG]http://i45.tinypic.com/34470j5.png[/IMG]

Apologizes for the hugeness of the image. Anyway, can someone be so kind as to walk me through merging that unallocated space with sda5?

---

### Post by aktiwers on 2010-05-29
Have a look here:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

or here
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

:)

---

### Post by OpalGirl on 2010-05-30
Thank you, aktiwers. ;)

Still not quite resolved--how about removing the Windows entries from GRUB?

---

### Post by bumanie on 2010-05-30
Try > sudo update-grubIn theory it should remove the windows entries, but I am not completely comfortable with grub2 as yet. If that doesn't work, you should be able to reinstall grub from a live cd as per [here]("http://ubuntuforums.org/showthread.php?t=1195275") point number 13.

---

### Post by OpalGirl on 2010-05-30
> **bumanie said:**
> Try In theory it should remove the windows entries, but I am not completely comfortable with grub2 as yet. If that doesn't work, you should be able to reinstall grub from a live cd as per [here]("http://ubuntuforums.org/showthread.php?t=1195275") point number 13.

That command worked--I ran it, then promptly restarted the computer to check it out. :P

Thank you kindly, everyone!

---

