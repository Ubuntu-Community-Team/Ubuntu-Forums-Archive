---
title: "DVD to hard disk for a media center?"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by wep940 on 2011-05-24
I am thinking about making an old PC into a media center, but I don't know anything about them, so I have 2 questions:
 
(1) What do I have to do to copy my DVD's to the hard drive so I don't have to keep inserting them?  I already know how to copy a DVD, but I have no idea how to put 1 on the hard disk and what the file structure(s) would look like.
 
(2) Currently I have a 8 year old non-digital TV - it uses a cable connector or composite for input.  The PC is older, so the best I could probably do for video on it is either AGP 4x or regular PCI.  Is there a video card still available for that?  How would I go about connecting VGA to some sort of converter, or do I need something special in the way of a video card?
 
Thanks in advance!

---

### Post by Grenage on 2011-05-24
> **wep940 said:**
> I am thinking about making an old PC into a media center, but I don't know anything about them, so I have 2 questions:
 
(1) What do I have to do to copy my DVD's to the hard drive so I don't have to keep inserting them?  I already know how to copy a DVD, but I have no idea how to put 1 on the hard disk and what the file structure(s) would look like.
 
(2) Currently I have a 8 year old non-digital TV - it uses a cable connector or composite for input.  The PC is older, so the best I could probably do for video on it is either AGP 4x or regular PCI.  Is there a video card still available for that?  How would I go about connecting VGA to some sort of converter, or do I need something special in the way of a video card?
 
Thanks in advance!

The DVD part should be the easy part; you can either rip them using something like handbrake, or just copy the disc to an ISO.  I'd probably recommend the ISO for DVDs.

While I doubt you can get AGP or PCI cards new, you can almost certainly find some on Ebay.  I don't know what kind of video power would be required for DVD playback, but I doubt it's much - what does your machine have at the moment?  I've not used a non-digital TV or media centre of that age.

---

### Post by wep940 on 2011-05-24
> **Grenage said:**
> The DVD part should be the easy part; you can either rip them using something like handbrake, or just copy the disc to an ISO. I'd probably recommend the ISO for DVDs.
 
While I doubt you can get AGP or PCI cards new, you can almost certainly find some on Ebay. I don't know what kind of video power would be required for DVD playback, but I doubt it's much - what does your machine have at the moment? I've not used a non-digital TV or media centre of that age.
 
I rebuilt an ancient Compaq a year ago for my brother in-laws backup.  Now he doesn't need it so I get it back.  I replaced the power supply, put in a DVD-rom/CD-RW, a used emachines motherboard with a Celeron that runs somewhere around 2.7 or something ghz, 512 memory.  It has been using just the built-in video (some sort of Intel graphics - when the control software for it starts in Windows it comes up and says Intel Extreme Graphics, so I would imagine it's just an 845 - maybe less.
 
I'm also putting in a spare disk I have around here - the 1 that's in there is ancient and only running in PIO mode.  I know the motherboard supports ATA100, and the drive I have is ATA100.  My brother inlaw never understood when I told him I'd swap it out so the dang system wouldn't seem slow (barely touches the CPU, but the hard disk rattles around like it's on an olympic hard drive marathon).

---

### Post by Grenage on 2011-05-24
2.7Ghz, that could be worse; I'd actually plug the TV in and see how it fares.  Some extra RAM would be a plus, it really depends how much you care about the initial speed.

Media centre interfaces such as xbmc would probably be asking a bit much, but something light should work fine.  Either way, try it all and see what you can get out of the old girl.

---

### Post by Paqman on 2011-05-24
> **Grenage said:**
> 
Media centre interfaces such as xbmc would probably be asking a bit much, but something light should work fine.  Either way, try it all and see what you can get out of the old girl.

Actually XBMC might be a good choice. It can use VDPAU, so if you slap a cheap Nvidia card in it then it'll render all the output with the graphics card and leave the CPU pretty lightly loaded. More RAM might help, but my media centre only has 1GB and it runs XBMC fine, so you'd only need to find another 512MB stick at most.

---

### Post by wep940 on 2011-05-24
Well, I thought I'd start with the video first, so I just purchased a [SIZE=1]eVGA.com e-GeForce FX 5600 off EBay.  My winning bid was only $1.09 - the shipping $5, so it's not much lost if it doesn't work out.  This card is PCI and has a composite output, so it would work with my TV.  Going to swap the drives this weekend and load the OS so I can see if it performs.  I'm really not too worried about CPU speed - "back in the day" I had an old 486-100 that played DVD's fine.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I can't update the memory for a little while, but will try that as well.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]BTW - if I want to watch Hulu TV, Netflix TV and Movies, plus my DVD's, do I need (or maybe would it work better to have) the media center software?  For some reason I was thinking that was only if you had a TV tuner in your PC but I have a feeling now that I'm wrong on that.  Being so naive about any of this I'm probably asking some stupid question, eh?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Thanks again![/SIZE]

---

### Post by Grenage on 2011-05-25
> **Paqman said:**
> Actually XBMC might be a good choice. It can use VDPAU, so if you slap a cheap Nvidia card in it then it'll render all the output with the graphics card and leave the CPU pretty lightly loaded. More RAM might help, but my media centre only has 1GB and it runs XBMC fine, so you'd only need to find another 512MB stick at most.

I agree, with a replacement graphics card; I was just talking about the old intel in the existing system.  I love my xbmc machine.

> **wep940 said:**
> Well, I thought I'd start with the video first, so I just purchased a [SIZE=1]eVGA.com e-GeForce FX 5600 off EBay.  My winning bid was only $1.09 - the shipping $5, so it's not much lost if it doesn't work out.  This card is PCI and has a composite output, so it would work with my TV.  Going to swap the drives this weekend and load the OS so I can see if it performs.  I'm really not too worried about CPU speed - "back in the day" I had an old 486-100 that played DVD's fine.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I can't update the memory for a little while, but will try that as well.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]BTW - if I want to watch Hulu TV, Netflix TV and Movies, plus my DVD's, do I need (or maybe would it work better to have) the media center software?  For some reason I was thinking that was only if you had a TV tuner in your PC but I have a feeling now that I'm wrong on that.  Being so naive about any of this I'm probably asking some stupid question, eh?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Thanks again![/SIZE]

There are various plugins for media centres such as xbmc, but I have no idea about Hulu and Netflix (I'm in the UK).  A tuner card would only be required for 'real' TV broadcasts coming in via an aerial or dish - not for internet streams.

---

### Post by wep940 on 2011-05-26
For now I'm going to mark this as solved.  I think I have a lot of online reading and research to do before I can tackle this, and I don't want to waste people's time by asking uneducated questions. ;)
 
Thanks to all who have replied - you've given me a lot to research and think about!!

---

