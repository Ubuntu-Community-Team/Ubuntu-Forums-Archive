---
title: "External hard drives (or other extra storage)"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by selablad on 2008-12-17
Okay, I'm not too sure about how to start this, so I guess I'll just say hi and launch straight into it.

Basically I am fairly new to linux in general, but very eager to learn as much as I can about it all :) so with that in mind, I've been trying out a whole lot of different distros.  However, I've found quite a few that I like and want to dual/triple/whatever boot, but I don't have that much hard drive space on my laptop.  I've been looking at a lot of threads and other stuff on the internet about it, but it just looks like a lot of jargon to me and I need someone to explain it all to me...

I have a dell inspiron 1520 laptop, which only has usb 1.1 which apparently isn't that great for speed - so I've been considering that an external hard drive might not be best?  Anyway, can anyone please explain to me the different options for adding hard drive space to my laptop?  Sorry about posting something which obviously comes up a lot, but I'm just so confused and would appreciate any help :)

---

### Post by lovelyvik293 on 2008-12-17
I think the best is replace your system harddrive with a more capacity one.

---

### Post by howefield on 2008-12-17
What is the capacity of you current drive, it might surprise you how small the drive can be and still dual boot, if you keep all your documents and files on a separate USB drive.

---

### Post by selablad on 2008-12-17
> **howefield said:**
> What is the capacity of you current drive, it might surprise you how small the drive can be and still dual boot, if you keep all your documents and files on a separate USB drive.

My hard drive now is pretty big - 160gb - but it's pretty much all used up with videos and music, so there's not much space for dual-booting.  I have thought about storing all of that on a USB drive or something, but it's quite a large collection, so...

---

### Post by drs305 on 2008-12-17
Your two options have been mentioned - an external drive or a larger internal drive. If you have usb 1.1, you must have an older laptop. I would not bother trying to replace the drive on an older computer, but that is just me. If you are happy with all the other features of the laptop maybe it would be worthwhile. If you decide to replace the harddrive, do you have all the necessary install/recovery disks?

A better option might be to purchase an external drive. I believe most of them, like the WD Passport series, *will* work with usb 1.1, but at reduced transfer speeds as you know. *Be sure to confirm this before purchasing one.* The good thing about this option is that the external drive can be used with other computers, can act as a backup to your laptop drive, and when the laptop screen or other component finally dies, you will still have a fully-usable external drive.

---

### Post by howefield on 2008-12-17
Incidentally, are you sure it_is_usb 1.1 ?

Just thinking way back when usb was in the realms of 1.1 that you wouldn't have a 160 gig hard drive. Could well be wrong though.

---

### Post by selablad on 2008-12-17
> **howefield said:**
> Incidentally, are you sure it_is_usb 1.1 ?

Just thinking way back when usb was in the realms of 1.1 that you wouldn't have a 160 gig hard drive. Could well be wrong though.

Actually, I have no idea :) but I was trying to find out, and followed the suggestions of some other thread, and basically got a whole lot of gibberish (in the terminal) with a couple of "1.10"s written out, so I just assumed it was.  My laptop is pretty new (a year or two old) so I was a bit confused about that.  Do you know how I can find out for sure?

---

### Post by xjcannonx on 2008-12-17
post the out put of ```
lsusb
```
to see what usb 1.1 or 2.0 you have

---

### Post by selablad on 2008-12-17
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 413c:3016 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by xjcannonx on 2008-12-17
well i looked up your dell and it has 4 usb 2.0 ports, does yours have 4 ports, so i think its safe to say you have 2.0

Also if you really wanted to dual boot, xp and ubuntu only needs 5 - 8 gigs at most i think, maybe less so im sure you could make room for it but ideally id agree with the others and get a external hd

---

### Post by TransitMan on 2008-12-18
If you have all that video and music on your laptop drive, my suggestion is to get an extrenal drive, in the range of 250 to 500 gb. Then you could back-up or transfer those files over to the external drive, thereby freeing up space on your laptop for other things.

---

### Post by selablad on 2008-12-18
Yeah, it has 4 ports, and as others have said it is a pretty new computer, so I guess I could assume that it has 2.0?  So that would mean that speed/performance/whatever isn't an issue, right?

Okay, I just have a couple more questions.  I've been looking up a whole lot of "things to consider" websites and that, and a couple of things still confused me.  Is that revolutions-per-minute thing likely to be important?  I don't want to do anything special that would require anything out of the ordinary, right, so whatever the normal rpm thing is should be okay?  And 2.5" vs 3.5" - what is that all about?

Thank you all so much for your help, I feel a lot better about everything now...

edit - transitman, thanks for that, that's certainly a very good idea and I will definitely consider it :D

---

### Post by xjcannonx on 2008-12-18
7,200 is fine, 5,400rpm is usually what you find in a laptop and 7200 in desktop and external, faster is better but for everyday stuff 7200 is the way to go and memory cache is something else to look for, most new drives these days will probably be 16mb im guessing which is also good

3.5" VS. 2.5" - the size of the hard drive [http://www.digitaldingus.com/articles/2005sep/25dilemma.php]("http://www.digitaldingus.com/articles/2005sep/25dilemma.php")

---

