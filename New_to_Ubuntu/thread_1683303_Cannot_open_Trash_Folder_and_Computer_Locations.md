---
title: "Cannot open Trash Folder and Computer Locations"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by VivekT on 2011-02-07
I managed to install nautilus-elementary on my system lured by the beautiful "coverflow" thing (which is working well). However even before I had installed it, but after installing some dependencies like gtk+, glib, pango etc, nautilus stopped showing the trash can in the bottom panel and when i try to open it, the window i am in closes by itself. It cannot be added to bottom panel either

Also, partitions are not showing like they usually do in Places. Not even pen drives. Earlier it was showing the message that nautilus cannot handle computer locations after clicking on the computer icon in Places on the top panel. 

In the case that the situation is hopeless, could you tell me how to go back to the original nautilus and regain the stuff. 

Thank You

---

### Post by madjr on 2011-02-07
what instructions did you use to install nautilus-elementary?

---

### Post by VivekT on 2011-02-07
I did the bzr thing. I started off by trying ./configure, that was listing a lot of dependencies which I installed one by one although I do not know if I did this properly. mainly it was the the gtk+, glib and pango thing. After all this ./configure worked but make didn't. By this time, nautilus had started giving troubles. Then I did **sudo apt-get build-dep nautilus** and I realized that I should have run ./autogen.sh. This worked finally. and make and make install worked too. and here I am. 

Thanks for replying

PS: I also have unity installed

---

### Post by madjr on 2011-02-07
oh, i thought you had installed from the nautilus-elementary ppa, which in that case using *purge ppa*, would revert things to normal automatically.

now the way you did it *manually* is more difficult to revert...

you should probably ask first in the elementary forums, which am pretty sure they may spot a fix, else they will give you instructions to revert back.

---

### Post by VivekT on 2011-02-07
Thanks, I shall try that.

---

