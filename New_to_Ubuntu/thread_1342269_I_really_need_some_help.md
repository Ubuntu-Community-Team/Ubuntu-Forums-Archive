---
title: "I really need some help"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by sallow_carrot on 2009-11-30
I installed an old version of Ubuntu on my computer last night.  Now I can't get back into Windows so I'm locked out of my stuff.  I restart and hit Esc, but I don't get an to boot Windows, just the three Ubuntu options and nothing else.  I'm using windows vista and I installed Feisty Fawn.  Yeah.  Is there a solution to this or am I just screwed?

---

### Post by sandyd on 2009-11-30
> **sallow_carrot said:**
> I installed an old version of Ubuntu on my computer last night.  Now I can't get back into Windows so I'm locked out of my stuff.  I restart and hit Esc, but I don't get an to boot Windows, just the three Ubuntu options and nothing else.  I'm using windows vista and I installed Feisty Fawn.  Yeah.  Is there a solution to this or am I just screwed?
i believe this means you just wiped windows vista off your hard drive.
open up a terminal (not really sure how to do this in feisty fawn), and type in 
```

sudo fdisk -l

```

and post the output

---

### Post by ajgreeny on 2009-11-30
Certainly let's see the output of that command, but preferably from a Live CD, not your installed setup;  the less you do with that at the moment, the better the chance of getting at least some of your files back from the windows install, if you really have trashed it with ubuntu.

It is just possible, I suppose that grub did not find the windows install when it was installed on the disk, but that is unusual, so I also suspect that your windows has gone.  I hope you were backed up properly so you have not lost too much, if anything.  If not, let this be a lesson to you; never do this sort of major disk operation without a complete backup of your own personal files.

---

### Post by Geoff918 on 2009-11-30
The boot sector may have been altered. Ubuntu usually plays nice with Windows and defaults to running side-by-side. If, when you installed Ubuntu, you selected use entire hard disk. Well, you probably won't be finding Vista on your hard drive and need a new install.

---

### Post by sallow_carrot on 2009-11-30
When I type in sudo fdisk -1 it prompts me for my password but I can't type anything in.

---

### Post by NoaHall on 2009-11-30
You will type something in, but you won't see it. Then press enter.

---

### Post by Cheesemill on 2009-11-30
> **sallow_carrot said:**
> When I type in sudo fdisk -1 it prompts me for my password but I can't type anything in.

Also it's
```
sudo fdisk -l
```
That's a small L, not a one.

---

### Post by sallow_carrot on 2009-11-30
Okay.  This is what it says after I get my password in:

> Disk /dev/sda: 320.0 GB 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512=8225280 bytes

Device: /dev/sda1  Boot: *  Start: 1  End: 37872  Blocks: 304206808+  Id: 38  System: Linux
Device: /dev/sda2  Start: 37873  End: 38913  Blocks: 8361832+  Id: 5  System: Extended
Device: /dev/sda5  Start: 37873  End: 38913  Blocks: 8361801  Id: 82  System: Linux Swap/Solaris


---

### Post by NoaHall on 2009-11-30
It looks like it's gone, I'm afraid.

---

### Post by sallow_carrot on 2009-11-30
Okay.  Well, thanks anyway.

---

