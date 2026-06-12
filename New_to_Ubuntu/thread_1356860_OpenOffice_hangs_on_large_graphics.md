---
title: "OpenOffice hangs on large graphics"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-12-16
I use Ubuntu Hardy 8.04 with Open Office 3.1.1.

I have a bit of a problem. Every month, I create a document with Open Office (40-44 pages).

Then, I add a number of JPG pictures (around 15-25Mb) into the document.

It seems that when the document gets too "full" (around three-quarters of the JPGs in the document), OpenOffice won't let me save.

[LIST]
[*]1Gb RAM, 2Gb swap: When I save, OO thinks for a bit, then the hard drive goes crazy and the machine comes to a standstill, non-responsive. Even after a long time, the hard drive is still going mad, and the only way to get out is to cut the power to the machine.
[*]I increased the swap to 4Gb. Now, when I save, OO thinks for a bit and then crashes.
[*]I tried this on a different machine (Jaunty 9.04) with 2Gb Ram, 2Gb swap, and it worked successfully.
[/LIST]

So. It seems that Open Office won't save a large file even with a big swap partition if the RAM is too small.

Does anyone have any idea how to overcome this -- apart from buying new hardware?

---

### Post by wojox on 2009-12-17
How about if you go to Tools > Options > Memory and adjust the Graphics cache ?

---

### Post by audiomick on 2009-12-17
Have a look at your disc space usage.
On a friend#s machine, OO started having problems with pictures ( albeit different to yours ).

The cause turned out to be that the / partition was full. (4.8 GB in a nearly 5GB partition).

---

### Post by Paddy Landau on 2009-12-17
> **wojox said:**
> How about if you go to Tools > Options > Memory and adjust the Graphics cache ?
Thanks for the idea.

I've tried this, making it big enough to easily fit all the graphics, but it doesn't help.
Hang on, I'll try some more changes.

---

### Post by Paddy Landau on 2009-12-17
> **audiomick said:**
> Have a look at your disc space usage...
According to System Monitor:
/ partiton 22% (4.3 out of 14.7Gib)
/home partition 13% (10.8 out of 71.9GiB)

So, thanks, I don't think that's the problem.

---

### Post by Paddy Landau on 2009-12-17
> **wojox said:**
> How about if you go to Tools > Options > Memory and adjust the Graphics cache ?
I did this:
Total cache: 100Mb
Per object: 1.5Mb (the largest I have is 0.85Mb)
Remove after: 00:20
Number of objects: 60 (my document has 44 according to the Navigator)

I closed all other windows, loaded the document, added a single letter, and saved.

Same problem, sadly.

---

### Post by Spiritof76 on 2009-12-17
You ,might try reducing the resolution of the images If you are printing on plain paper or viewing on a monitor, resolutions of more than 640 horiz is mostly a waste of bitage.  You can use gimp to shrink the images

---

### Post by Paddy Landau on 2009-12-17
> **Spiritof76 said:**
> You might try reducing the resolution of the images...
This is for a printed magazine, so unfortunately the quality needs to be higher. I already shrink large photos to the required size, retaining the needed quality.

Edit: I think I'll post this on the [Open Office forum]("http://user.services.openoffice.org/").

---

### Post by Paddy Landau on 2009-12-17
I've posted this on the Open Office forum.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=25723](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=25723)

---

