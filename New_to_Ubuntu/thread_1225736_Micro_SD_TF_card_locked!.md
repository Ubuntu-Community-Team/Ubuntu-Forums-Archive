---
title: "Micro SD TF card locked!"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by SPARTAN-118 on 2009-07-28
Darn it.

Somehow, I did something on ubuntu that caused my MicroSD card for my R4DS to become read-only...
and that's after I tried deleting everything and formatting it, to do a clean install of the newest firmware.

My files are stuck in the .Trash-1000 folder...

how do I change permissions so I can write/delete stuff again?

Don't tell me I'm screwed!

SPARTAN-118

---

### Post by esalnoj on 2009-07-28
Relax, you aren't "screwed" yet.

Firstly, does it automatically load when plugged in?

If so, right click the desktop icon, ->properties,->permissions and see if you can change settings there.

---

### Post by SPARTAN-118 on 2009-07-28
Can't, but for some reason, the SD card adapter works... so it's not the actual MicroSD card itself, but the USB adapter.

1) Can I change the USB adapter's permissions? I use it more than the SD adapter....
2) Do I have to buy another USB adapter? This one worked fine until I did... whatever I did.

Also, I could get to the "Permissions" window from right-click "/media/disk/", but couldn't change anything...

SPARTAN-118

---

### Post by esalnoj on 2009-07-28
For clarification, are we talking "MicroSD" plugs into "USB adapter" plugs into "USB port"?

Also, as a point of interest, do you have a "fatal-modprobe couldn't load module.dep" error at boot-up? 
That was preventing my USB connected SD multi-reader from functioning in my laptop.

---

### Post by kevin_mon on 2009-07-28
did you move the little lock at the USB adapter's side?
it's very small.last time.i move it by accident.

---

### Post by SPARTAN-118 on 2009-07-28
> **kevin_mon said:**
> did you move the little lock at the USB adapter's side?
it's very small.last time.i move it by accident.

Well, it's the USB adapter that came with the R4, and it came from China. And, as we all know, products from China are not always the best quality. So no, there is no lock at the side. However, if I bought a USB adapter from, say, Staples, I presume it would have a lock at the side?
_................................................................................................................................_
esalnoj:

1) Yes.
2) No. And what the heck does that even mean?
Besides, I use (well, usually) my laptop's built-in SD card reader (of which I believe is the only type of card that works in it, conveniently).

-Note: Not trying to diss China, it's just true, and that *is* where you can most often find "fakes" of these types of products.

---

### Post by esalnoj on 2009-07-29
You are better off using the SD card adapter instead of the USB adapter for now, seeing that your SD reader works properly.

I cannot help you further on this issue.

That error at boot meant the kernel wasn't automatically loading a module necessary for some USB connected devices to function.

Even Staples sells a lot of chinese made merchandise.

---

### Post by SPARTAN-118 on 2009-08-01
> **esalnoj said:**
> 
Even Staples sells a lot of chinese made merchandise.

I know a lot of products are "made in China".
However, I meant products that aren't cleared for stores (ie the R4, or some other DS card) aren't always reliable.

I myself have many things that are "Made in China", including the R4. But they don't always have to include top-quality accessories with the main product, such as a too-small wrist strap that would only fit a small child, or a faulty USB adapter, like mine.

Again, I know China sometimes comes out with things that are better than their North-American or European counterpart. I'm just saying that some parts may not be as reliable as you might think.

SPARTAN-118

PS: Yes, I think I will use the SD adapter; that is what I've *been* doing. However, I am wondering why Best Buy/Future Shop never have any USB (or even SD) adapters in their flyers? It seems kind of odd that I have never seen any in a [recent] flyer.

---

### Post by SPARTAN-118 on 2009-08-06
Well, looks like I did it again.
 
Now the SD adapter is locked - I tried replacing _DS_MSHL.NDS, since I thought that would mean replacing Moonshell (a multi-media player for DS), and now I got the same problem. 
 
However, this time it's a little different:
 
When I try to delete a file, first it displays and input/output error, *then* the "Read-only filesystem" error.
 
Looks like I'll have to buy new adapters, if formatting it in Windows doesn't work, eh?
 
EDIT: Strange, everything works fine in Vista, can read/write fine....
 
When I inserted the USB adapter into Windows, it asked me if I wanted to scan for and fix file system errors - and it said that automatically, so maybe it's moonshl2 that's causing the problem. 
Will keep you posted regarding this issue.
 
EDIT 1: Well, the Windows "Auto-detect-and-fix" worked, it fixed whatever "bad sectors" there were and I deleted moonshl2.
Will check if it works in Ubuntu now. (I highly doubt it, since Moonshl2 wasn't on the card when I first had this problem...)
 
EDIT 2: Great news! Whatever Windows did, plugging in the two adapters fixed both the USB and SD adapters! Now, I can read/write without a problem!

Advice for anyone using Ubuntu:
If you ever have any permission problems with any of your devices, and also have Windows/Mac installed, plug the device(s) into Windows, and try it out again in Ubuntu.

I guarantee you'll be surprised.

SPARTAN-118

PS I'll keep this thread open as a consideration for other users who have similar problems.

---

