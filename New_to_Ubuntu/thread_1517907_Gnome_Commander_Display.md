---
title: "Gnome Commander Display"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by edzell on 2010-06-25
I've just downloaded Gnome Commander and want to use it to compare directory details. Haven't read all the help files yet but right away I have a question about how it displays information at the top. A snapshot is attached. Look in the spaces where it shows what directory is open in each window. They both display large alphanumeric strings and the one on the right is unreadable, maybe because the one on the left overlaps it.

What are these strings and how can I get rid of them or make them readable?

---

### Post by edzell on 2010-06-25
> **edzell said:**
> I've just downloaded Gnome Commander and want to use it to compare directory details. Haven't read all the help files yet but right away I have a question about how it displays information at the top. A snapshot is attached. Look in the spaces where it shows what directory is open in each window. They both display large alphanumeric strings and the one on the right is unreadable, maybe because the one on the left overlaps it.

What are these strings and how can I get rid of them or make them readable?

Sorry that was another case of the famous lost attachment. Trying again.

---

### Post by oldos2er on 2010-06-25
Those "strings" are UUIDs. [http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)

---

### Post by edzell on 2010-06-26
> **oldos2er said:**
> Those "strings" are UUIDs. [http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)
Not sure why you put "strings" in quotes like that. They are strings aren't they?

Why does it take 30-or-so (didn't actually count them) characters to uniquely identify my drives and partitions; and what would be wrong with using labels that I uniquely define and that can can be recorded & recognised by both the OS and myself?

Some of this stuff seems way too ubergeeky to be usable by ordinary folks.

Sorry for the mini-rant but it sometimes seems as if the concept of user-friendliness is actually despised out there.

---

### Post by warfacegod on 2010-06-26
You can use the System> Admin.> Disk Utility to change the HDD and/or Partition labels. Make sure the volume is mounted first. Doing this should make the "strings" appear as the labels you have created for the drives.

---

### Post by edzell on 2010-06-26
Re my query about GnomeCommander: After an overnight shutdown, on re-start the GC display has re-set itself and no longer shows the UUIDs, Just the directory paths. What happened? I had previously tried all the "View" options to get rid of those unreadable overlapping UUIDs, with no success. Now they're gone.

Will they come back when I'm not looking? Suspense, suspense!

Any clues appreciated.

---

### Post by warfacegod on 2010-06-26
> **edzell said:**
> Re my query about GnomeCommander: After an overnight shutdown, on re-start the GC display has re-set itself and no longer shows the UUIDs, Just the directory paths. What happened? I had previously tried all the "View" options to get rid of those unreadable overlapping UUIDs, with no success. Now they're gone.

Will they come back when I'm not looking? Suspense, suspense!

Any clues appreciated.

One of the view options you selected/deselected probably just didn't "take" until gdm was restarted.

---

### Post by edzell on 2010-06-26
> **warfacegod said:**
> You can use the System> Admin.> Disk Utility to change the HDD and/or Partition labels. Make sure the volume is mounted first. Doing this should make the "strings" appear as the labels you have created for the drives.

Thanks, I'll do that. I don't think my previous v8.04 would allow it somehow.

"*Things should be made as simple as possible but not simpler*" - A. Einstein.

---

### Post by edzell on 2010-06-26
Found the problem with overlaps in the GnomeCommander top display when comparing directories:

Enabling View->Device Buttons puts up a row of device icons with labels - or UUIDs - which, if it's long (e.g. lots of devices mounted,) can overlap from the left pane over the row on the right pane.

Deselecting Dev Buttons & enabling Dev List instead, puts them in a drop-down menu; problem solved.

A source of confusion for me was that the View menu options didn't always take effect right away, but sometimes did. Repeating the select-deselect-select sequence seems to force them to work.

Don't know why/how mine switched from displaying UUIDs to labels - anybody??

---

### Post by oldos2er on 2010-06-26
Which version of GC are you using? As far as I know, mine has never displayed UUIDs in place of labels (I'm running 1.2.8.5, btw). I don't use the program very often though.

---

### Post by edzell on 2010-06-26
> **oldos2er said:**
> Which version of GC are you using? As far as I know, mine has never displayed UUIDs in place of labels (I'm running 1.2.8.5, btw). I don't use the program very often though.

It's version 1.2.8.5. Haven't used it to do anything yet; I'm still exploring how. It only put up the UUIDs once, when I first opened it. Don't care if it never does it again :)

Is your name really Ann? Is that really your picture? :eek:

---

### Post by edzell on 2010-06-26
Hmmm....

Giving up on GnomeCommander. I'm too dumb to figure out how it works all by myself. Downloaded Diffmerge on the strength of its extensive documentation, which suggests it will do what I want & tells me how.

Thanks all for help & comments.

---

### Post by oldos2er on 2010-06-27
> **edzell said:**
> Is your name really Ann? Is that really your picture? :eek:

Yes, my name's Ann; no, that's a pic of the late great Vivian Stanshall.

---

