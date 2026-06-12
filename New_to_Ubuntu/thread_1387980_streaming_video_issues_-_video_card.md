---
title: "streaming video issues - video card?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by gwilkins82 on 2010-01-22
Hi all.  I was wanting to watch a video on hulu, and it was watchable, but noticeably choppy (sound was fine).  Seems like this must be a video card issue?  No real idea what to do, if anything.  I don't even know what kind of video card this laptop has (it was an old hand-me-down, and I wanted Linux on it to ensure some durability).  I do know it is a gateway m250.  Any thoughts on what I can do to fix this?

Thanks

---

### Post by halitech on 2010-01-22
quick search on google shows this:
```
Video
Graphics controller 	Intel® Extreme Graphics 2 integrated in Northbridge 915GM
```

you can confirm by opening a terminal and running ```
lspci
```

Not sure there is much that can be down with Intel chips (don't have one) but I know there were some issues with 9.04 and 9.10. Not sure if they have been sorted out yet or not.

---

### Post by gwilkins82 on 2010-01-22
right - i was about to update my post to say that i have run lspci and it came back w/:

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

Does this mean I am out of luck?  Can this be replaced/upgraded to something ubuntu friendly? Or is this something that there will be a fix for?

---

### Post by halitech on 2010-01-22
Typically video cards on laptops are integrated right into the motherboard so there is no way of upgrading or changing them.

Hopefully they will eventually fix the coding for this. In the meantime you could try other distros like Mint and see if they have better support for your card.

---

### Post by gwilkins82 on 2010-01-22
thanks for the info.  intel's site has a linux version of the drivers - i guess these just aren't ubuntu compatible though, huh.  bummer.

---

### Post by gwilkins82 on 2010-01-22
is there a way to tell which linux distros might be compatible?

---

### Post by halitech on 2010-01-22
pretty much hit or miss as far as I know. Maybe search their forums and see if people have the same issues with the card you have.

---

### Post by clhsharky on 2010-01-22
HI gwilkins82

I don't believe you have the intel issue with Ubuntu9.04, because you would have a blank screen 'X crash at startup'. There were work arounds to help, and 9.10 doesn't have that problem.

The problem is Flash, its very heavy on resources. Have a look at-

Adobe System requirements
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)
Higher than you would think!

Turn CPU speed up, while watching flash. Easy with 'CPU Frequency Scaling Monitor' will help get rid of choppy flash. Yes the CPU does the encoding of flash in Linux.
Installing newer drivers may also help, also easy with launchpad PPAs.
Mesa  -thats your 3D driver
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
video driver 
[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)


Sharky

---

### Post by gwilkins82 on 2010-01-22
certainly could all be true - im no expert on any of this.  added those reps, thanks.  as far as the cpu monitoring goes, it is already set to 'on demand' which bumps it up when watching videos. would it be more efficient use to turn it up to 'performance'?

thanks for the info

---

