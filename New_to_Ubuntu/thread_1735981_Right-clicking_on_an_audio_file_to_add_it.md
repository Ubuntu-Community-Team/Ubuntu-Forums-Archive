---
title: "Right-clicking on an audio file to add it?"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-22
Is there a media player in Ubuntu/Linux that allows you to right click on an audio file and add it to a playlist?

Windows XP allows you to right click on an audio file and choose to "Queue It Up" which adds the audio file to the currently running media player without going into the media player itself, which is pretty cool once you get used to using it.

My Ubuntu 10.10 installation doesn't seem to have that by default.  Is there an audio program or some other feature/program that will allow give me that functionality?  It sounds trivial, but I miss it.

---

### Post by ohadcn on 2011-04-22
for nautilus file manager and totem media player folow this:
open terminal and run those commands:

sudo apt-get install nautilus-actions
nautilus-actions-config-tool

in the opened window's menu, enter file->new action
on action tab, set contex label to (whatever you want to see in the contex menu)
on command tab, set path to"totem --enqueue" and set parameters to %M
under conditions tab change mimetypes to "*/*" (why it's not default? i think it's a bug, but it doesn't work for me when i kept the default *) and set filenames to the media filenames (something like *.mp*;*.m4a;*.ogg;*.wm*;*.m3u)
file -> save
 
restart nautilus (run nautilus -q and then nautilus)

---

### Post by Learning Linux 2011 on 2011-04-23
> **ohadcn said:**
> for nautilus file manager and totem media player follow this:
open terminal and run those commands:

sudo apt-get install nautilus-actions
nautilus-actions-config-tool

in the opened window's menu, enter file->new action
on action tab, set context label to (whatever you want to see in the context menu)
on command tab, set path to"totem --enqueue" and set parameters to %M
under conditions tab change mimetypes to "*/*" (why it's not default? i think it's a bug, but it doesn't work for me when i kept the default *) and set filenames to the media filenames (something like *.mp*;*.m4a;*.ogg;*.wm*;*.m3u)
file -> save
 
restart nautilus (run nautilus -q and then nautilus)

Cool, thank you!

---

