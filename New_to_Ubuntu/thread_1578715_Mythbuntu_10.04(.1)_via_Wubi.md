---
title: "Mythbuntu 10.04(.1?) via Wubi"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by ubforumsnow on 2010-09-20
Hi, 

I'm trying to install Mythbuntu using Wubi.  When I run Wubi and select "Mythbuntu" it downloads mythbuntu-10.04.amd64.iso.  When finished it says there was an error and to see the log for more details.  In the log it says that it couldn't finish because it was trying to install 10.04.1, but only found 10.04 media.

I've tried placing a mythbuntu-10.04.i386.iso and a mythbuntu-10.04.amd64.iso in the same directory and even tried renaming them to be ...10.04.1..., but every time I run Wubi it downloads an ISO and then fails.

---

### Post by sandyd on 2010-09-20
> **ubforumsnow said:**
> Hi, 

I'm trying to install Mythbuntu using Wubi.  When I run Wubi and select "Mythbuntu" it downloads mythbuntu-10.04.amd64.iso.  When finished it says there was an error and to see the log for more details.  In the log it says that it couldn't finish because it was trying to install 10.04.1, but only found 10.04 media.

I've tried placing a mythbuntu-10.04.i386.iso and a mythbuntu-10.04.amd64.iso in the same directory and even tried renaming them to be ...10.04.1..., but every time I run Wubi it downloads an ISO and then fails.
Seems to be a bug, since there is no mythubuntu 10.04.1

Install ubuntu, then follow instructions here -> [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)

---

### Post by bcbc on 2010-09-20
wubi.exe is very particular about the version - the latest available is 10.04.1 but this doesn't seem to work on those flavours that weren't updated e.g. netbook edition, xubuntu and I guess mythbuntu too.

You can either pull the wubi.exe off the .iso (mount it and extract it) or just find the old wubi.exe from the web somewhere. This is one place: [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/) (you want r189 I believe)

---

### Post by ubforumsnow on 2010-09-28
Thanks for all the help.  

I first tried bcbc's method and it seemed to work, but after the install (or what seemed to be the install) it appeared to crash while moving on to another step.  Subsequent restarts never showed a Windows Boot Manager screen to allow me to choose OSes.

Next I tried sandyd's method and it worked great.  The only oddity was MythTV didn't start full screen.  Or maybe it did, but the panels on the top and bottom of the screen were covering it.  Setting the panels to auto-hide solved that.

Thanks again!

---

