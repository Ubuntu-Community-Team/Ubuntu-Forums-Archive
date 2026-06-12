---
title: "[SOLVED] view remote files as local"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Kellemora on 2009-01-04
Hi Gang
Wasn't sure how to title this, so let me explain.

I recently set up a new file server, rather than have the data files each user uses on their own computers.

But I discovered something this morning and would like to have it fixed before everyone shows up for work tomorrow morning.

When a file is on the computer it's used on, when you view these files in File Manager (nautilus) you SEE just what these files are.  For example:  Fonts show up in the font STYLE, Images show up as a thumbnail, music files will play just by placing the mouse over them, etc.  Music isn't that important of course.
But being able to VIEW things without loading them is a MUST HAVE FEATURE.
By using a File Server it appears we have lost the most useful features of Ubuntu?
Or is there a setting I'm missing somewhere?

I'll be up all night AGAIN moving all the files back to the computers they came from so we can get some work done tomorrow and abandoning the new file server if this doesn't have a simple fix, like a setting somewhere to change it.

Ubuntu Hardy 8.04 LTS is our system here.

TTUL
Gary

---

### Post by northern lights on 2009-01-04
Previewing remote files will obviously always be a tidbit slower (network speed versus SATA speed) than previewing local files, but is possible.

It's a mere question of nautilus preferences.

Open nautilus and select "Preferences" from the "Edit" menu. Under the "Preview" tab you can change file specific options: "Never", "Local Files Only" or "Always".

I'm guessing your workstations are set to "Local Files Only".

---

