---
title: "Rhythmbox won't import my folder"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by tegnoto89 on 2009-04-03
I just put an album in my music folder, which Rhythmbox is set up to automatically check.  It won't import the folder (they're mp3's), even after several restarts of the program, and a restart of the OS.  I've tried removing the folder and putting it back in, moving the files to a new folder, etc.  Also, manually importing them doesn't work either...  Nothing happens.

Any suggestions?

---

### Post by asmoore82 on 2009-04-03
I would run the command line utility `file` on one of the mp3's...
open a terminal, type "file " - no quotes but note the space at the end,
click and drag an mp3 to the terminal, and press enter in the terminal.

on a real, normal mp3 the result should look like this:
```
**~$** file test.mp3 
test.mp3: MPEG ADTS, layer III, v1, 128 kBits, 44.1 kHz, JntStereo
```

---

### Post by tegnoto89 on 2009-04-03
It actually imported them on its own...  Just took a long time.  Thanks for the response!

---

