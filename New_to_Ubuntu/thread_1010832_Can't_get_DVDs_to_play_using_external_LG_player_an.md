---
title: "Can't get DVDs to play using external LG player and movieplayer"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Hydie on 2008-12-14
Hi, I am completely new to Ubuntu.  I am trying to play a dvd and have connected by USB an LG external DVD player.  It shows up as existing, and the DVD I put into it shoes up in the File browser menu, but then when movieplayer opens up and I click on the dvd title and the play button it says "an error occurred- could not read from resource". I have the driver disc but same message comes up for this too.  So what do i do?

:)H

---

### Post by northern lights on 2008-12-14
Most likely your device is working just fine and you simply haven't added DVD support to Ubuntu. This is not available out of the box due to licensing restrictions in "some countries".

If you're on Intrepid, run ```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``` to add the medibuntu repositories. Replace *intrepid.list* by the respective release your on, if it's not 8.10.

Thereupon add DVD support via ```
sudo apt-get install libdvdcss2
```

---

