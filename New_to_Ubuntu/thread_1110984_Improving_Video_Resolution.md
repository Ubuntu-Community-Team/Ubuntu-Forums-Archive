---
title: "Improving Video Resolution"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by webtoed on 2009-03-30
Howdy all,  I am a real newbie, but have made a few strides.  I have two different machines running Ubuntu: 1 has 8.04, one has 8.10.  In both instances, I have rather limited video resolution.  The 8.10 machine is set up with a KVM switch so I can flip between the XP Pro environment on one network, and the Ubuntu environment on another.  Since I am sharing a monitor, the XP has really high resolution (1028x?).  The best I can get for Ubuntu is 800x600.  The monitor I set this machine up with had a little higher resolution settings when it was connected.

This is a p4 skt 478 with a full gig of RAM.  Apparently, Ubuntu does not like the video chipset on the motherboard, and the only way I could do the install was to use an old PCI video card from the parts box.

Basically, my internet windo is real big, requires scrolling across to view the whole message.  I'd like to squeeze this down to fit within the frame of the monitor.

All comments appreciated.

---

### Post by aeiah on 2009-03-30
what video card are you using? i doubt many people here are familair with the parts box that you got it from

---

### Post by WebToad on 2009-03-30
Well, it appears that the old "Parts Box" has a few antiques!  The Video card is a Diamond Stealth2000 3D...probably 12 or more years old.  Perhaps I should re-do the classification system to something other than working/not working!

So the new question is this:  Would a more modern Video card boost the resolution?  At 600x400 this looks to be pretty basic VGA performance from the mid 1990s.  Any thoughts on video cards that work better with Ubuntu?

Thanks again!

---

### Post by CatKiller on 2009-03-30
[This person]("http://ubuntuforums.org/showthread.php?t=1111005") has the same problem with the resolution through a KVM.

What was the onboard video that you were using before that Ubuntu "does not like?" It might be possible that someone here can help you get that working too.

---

### Post by WebToad on 2009-03-30
Hard to say.  This was a machine I built, specifically for learning Ubuntu.  The Motherboard is a Biostar M900M4 for Pentium4 Socket 478.  This board has onboard VGA graphics...called an S3 Unichrome Pro.  When I initially tried to load Ubuntu 8.04 and later 8.10, when I got to the command screens, EVERYTHING was out of whack.  The selection boxes were not aligned, and the entire screen was blurry and unreadable.  Then the entire rig froze up!

I have 8.04 on an old machine with an Athlon 1200, Socket A, and it doesn't have this problem...only this newer board.  In trouble shooting the problem, I figured the issue was with the video driver, and just grabbed the first working card I found in my spare parts.  This works, just has a big screen, and my max resolution setting isn't but 800x600 (can't select anything greater).  As mentioned, the other machine sharing this monitor is working at 1280x1024.  It, too is a P4 with XP Pro.

---

### Post by webtoed on 2009-04-07
I found some information that seemed to indicate certain ATI cards are more visible in Ubuntu 8.10.  I went searching on some of the bargain websites I regularly haunt, and found an ATI Rage XL 8MB PCI card for a wallet busting $10,00.  (Tested system pull)  Works like a charm, and my screen resolution immediately jumps to 1024x768.  This is fine for me, and far more usable.

I suppose the bottom line here is to experiment with different cards till you find one to your liking.  There are a bunch out there that are not the newest-latest-greatest that pack a wallop of performance, and those can be acquired for a little bit of cash!

---

### Post by spcwingo on 2009-04-07
If you ever run into that problem again, I would suggest using the vesa driver as opposed to the driver that is loaded by default.  The card I am using right now (GeForce2 MX/MX 400) was stuck at 800x600 (the nvidia driver under system>admin>hardware drivers reduced that to 640x480), but thanks to the vesa driver I now can go as far as 1280x1024 (although I use 1024x768 ).

---

### Post by theozzlives on 2009-04-07
> **webtoed said:**
> I found some information that seemed to indicate certain ATI cards are more visible in Ubuntu 8.10.  I went searching on some of the bargain websites I regularly haunt, and found an ATI Rage XL 8MB PCI card for a wallet busting $10,00.  (Tested system pull)  Works like a charm, and my screen resolution immediately jumps to 1024x768.  This is fine for me, and far more usable.

I suppose the bottom line here is to experiment with different cards till you find one to your liking.  There are a bunch out there that are not the newest-latest-greatest that pack a wallop of performance, and those can be acquired for a little bit of cash!

The Rage XL won't do compiz-fusion, I have the same card.

---

