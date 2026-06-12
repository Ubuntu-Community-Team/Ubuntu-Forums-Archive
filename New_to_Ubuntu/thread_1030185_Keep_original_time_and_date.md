---
title: "Keep original time and date"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Toontje on 2009-01-04
When I move files to my Ubuntu PC (e.g. pictures from SD card to HD), the ´Date modified´ changes to the current date & time.

Is there a way to keep the original date? Because I didn't modify them, I only moved them.

Thanks!

---

### Post by albinootje on 2009-01-04
> **Toontje said:**
> When I move files to my Ubuntu PC (e.g. pictures from SD card to HD), the ´Date modified´ changes to the current date & time.

Is there a way to keep the original date? Because I didn't modify them, I only moved them.


Which program did you use ? f-spot ?

For copying on the commandline I use "cp -arv" and "rsync -avzu".

The manual page of "mv" doesn't mention permissions.

---

### Post by Toontje on 2009-01-04
I just used ´Cut & Paste´ :) Sorry, I'm an ex-XP user.

When I put my SD card in the reader, I choose ´Open folder´, CTRL-A (to select all), CTRL-X (to cut), then I go to the destination folder and do CTRL-V (to paste).

All is done in Nautilus.

---

### Post by albinootje on 2009-01-04
> **Toontje said:**
> I just used ´Cut & Paste´ :) Sorry, I'm an ex-XP user.

No problem, I only showed the command line options because I don't know how GUI apps handle this.
> 
When I put my SD card in the reader, I choose ´Open folder´, CTRL-A (to select all), CTRL-X (to cut), then I go to the destination folder and do CTRL-V (to paste).

All is done in Nautilus.

Can you test this with other filemanagers like Thunar, Pcmanfs and Konqueror ? 
For Konqueror you will need to open another Konqueror window to drag and drop.

---

### Post by Toontje on 2009-01-04
It looks like GNOME Commander does it ´correctly´. I´ll see with other programs as well.

Bedankt voor de tip!

---

### Post by albinootje on 2009-01-04
> **Toontje said:**
> It looks like GNOME Commander does it ´correctly´. I´ll see with other programs as well.

Bedankt voor de tip!

OK :)

Perhaps you can search to see whether there's already a bug-report about this. If not, you have the honor to create a new bug-report for this.
[http://launchpad.net](http://launchpad.net)

---

### Post by Toontje on 2009-01-08
I tested some more and found that the problem only happens when copying to a NTFS partition.
Both Nautlilus and GNOME Commander have the same behavior: When copying to an Ext3 partition, the timestamp is copied from the original file, when copying to an NTFS partition, a new timestamp is generated.

I checked Launchpad and found several similar problems, but no bug dedicated to the NTFS partition and not to Ubuntu 8.10 64bit, so I opened a new bug: [https://bugs.launchpad.net/bugs/314860](https://bugs.launchpad.net/bugs/314860)

---

