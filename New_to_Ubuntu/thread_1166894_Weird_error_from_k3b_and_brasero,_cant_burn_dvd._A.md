---
title: "Weird error from k3b and brasero, cant burn dvd. Anyone seen this before."
date: 2009-05-22
forum: New to Ubuntu
---

### Post by philinux on 2009-05-22
These are from the messages log. Burning takes place but always end up with blank dvd. Trying to burn an iso file. 2.5gig. Anyone seen these type of errors? DVD burner plays dvd's and reads other disks ok.

```

philcb-desktop kernel: [ 8395.678435] sr 4:0:0:0: [sr0] Add. Sense: Unrecovered read error
May 21 17:50:40 philcb-desktop kernel: [ 8398.548772] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
May 21 17:50:40 philcb-desktop kernel: [ 8398.548783] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
May 21 17:50:40 philcb-desktop kernel: [ 8398.548792] Info fld=0x20
May 21 17:50:40 philcb-desktop kernel: [ 8398.548795] sr 4:0:0:0: [sr0] Add. Sense: Unrecovered read error
May 21 17:50:40 philcb-desktop kernel: [ 8398.548813] __ratelimit: 19 callbacks suppressed
May 21 17:50:43 philcb-desktop kernel: [ 8401.549907] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
May 21 17:50:43 philcb-desktop kernel: [ 8401.549918] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
May 21 17:50:43 philcb-desktop kernel: [ 8401.549927] Info fld=0x20
May 21 17:50:43 philcb-desktop kernel: [ 8401.549930] sr 4:0:0:0: [sr0] Add. Sense: Unrecovered read error
May 21 17:50:47 philcb-desktop kernel: [ 8404.898273] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
May 21 17:50:47 philcb-desktop kernel: [ 8404.898284] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
May 21 17:50:47 philcb-desktop kernel: [ 8404.898293] Info fld=0x20
May 21 17:50:47 philcb-desktop kernel: [ 8404.898295] sr 4:0:0:0: [sr0] Add. Sense: Unrecovered read error
```

---

### Post by HereInOz on 2009-05-22
I haven't see this, but I would tend to suspect hardware, Phil.  Possible cable issue.  I assume you have already replaced the dvd burner with another known good one.

Looks very like a hardware problem.

---

### Post by philinux on 2009-05-22
Successfully burned my iso to dvd. I found a dvd rw that was able to be written to. No errors.

Out of 10 walmart/asda dvd rw's 4 are now coasters. Is there any way to force blank them. They've only been written to a couple of times.

---

### Post by philinux on 2009-05-22
Managed to rescue/revive these dvd rw's. They either came up as blank or not mounted but would not burn to. Always failed.

Using a bit of trial and error with these commands.
Try this to blank problem dvd
growisofs -Z /dev/dvd=/dev/zero

Then this with or without lead-out
dvd+rw-format -force -lead-out /dev/dvd

and this to change the format of the disk to UDF
mkudffs /dev/dvd
[http://mindspill.net/computing/linux-notes/how-to-format-a-dvd-with-udf.html](http://mindspill.net/computing/linux-notes/how-to-format-a-dvd-with-udf.html)

---

