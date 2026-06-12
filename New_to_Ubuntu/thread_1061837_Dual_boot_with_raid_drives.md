---
title: "Dual boot with raid drives"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Atallicus on 2009-02-06
My computer currently has 4 hard drives in it.  The 2 250 gigs used to be set up as a raid.  Unfortunate circumstances of wanted to dual boot broke the raid, so we set them up as single drives.  So I now have windows on C, D has all my wallpapers, games etc on it, one drive is Ubuntu, and one is unused.

The D drive(as I explained in my last post), seems to have a problem not being in a raid array, as sometimes windows tells me that it needs to be reformatted.  Anyways I'm sure you read that in my other post.

What I would like to know is, if I raid the 2 250gigs together again, and still want to boot Ubuntu on one of the other drives not in the raid, how difficult is that?  Do I have to reinstall Ubuntu?  If so, I'm sure I need to unplug the raid while it installs, but how do I reset up grub to show windows also?  Is it even recommended to dual boot with a raid array in the picture?

Sorry for so many questions, but I really don't want to break it again :D

---

### Post by blueridgedog on 2009-02-06
If the array is a hardware array and is exposed to the OS as a single disk, and you want it as a boot disk, you can install Ubuntu to another disk and is will work fine (I have Ubuntu installed to a third disk in my system).  You will need to reinstall and the creation of the array will wipe all data on the two drives.

In the way of general advice, I suggest you plan your system out on paper.  Thinking ahead what drives will be in what positions and what use you will put those drives too.

---

