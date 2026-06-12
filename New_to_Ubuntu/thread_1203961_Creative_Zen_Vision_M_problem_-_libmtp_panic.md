---
title: "Creative Zen Vision M problem - libmtp panic"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by kobudo on 2009-07-04
Hi all,

I am finally getting the kinks worked out and a little more comfortable with what I'm doing, so I decided to try and get the Creative Zen Vision M working with Jaunty. 

It seemed like most people are having good luck with Gnomad2, so I added that along with the mtp program. Well, I got the "no jukeboxes found on USB bus" error. Running lsusb shows that the player is detected. Running mtp-detect in terminal shows the following result:

```
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN Vision:M (041e:413e) @ bus 0, dev 14
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

```

I have no clue what this means or how to rectify the situation.

---

### Post by kobudo on 2009-07-04
Okay, updated libmtp to version 0.3.6. The "new" mtp-detect statement is thus:

```
libmtp version: 0.3.6

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN Vision:M (041e:413e) @ bus 0, dev 6
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

```

The problem seems to stem from the device appearing "busy" causing the LIBMTP panic??? Now it still doesn't work and I'm clueless... :(

---

### Post by kobudo on 2009-07-04
Well, I found the solution to my problem. [This webpage ]("http://www.ehow.com/how_5012085_sync-creative-zen-using-ubuntu.html")fixed the problem. It was coming up as a removable drive and confusing the whole mess.

I didn't find this solution proposed anywhere on the forums. But it worked for me.

Problem solved. :p

Though it seems I now have to unmount the volume each time I plug it in or it doesn't work...

---

### Post by Kvothe_The_Bloodless on 2009-09-03
> **kobudo said:**
> Well, I found the solution to my problem. [This webpage ]("http://www.ehow.com/how_5012085_sync-creative-zen-using-ubuntu.html")fixed the problem. It was coming up as a removable drive and confusing the whole mess.

I didn't find this solution proposed anywhere on the forums. But it worked for me.

Problem solved. :p

Though it seems I now have to unmount the volume each time I plug it in or it doesn't work...

Thaks Kobudo..!!!! This works great form too. Really works at first try..!!!!

---

