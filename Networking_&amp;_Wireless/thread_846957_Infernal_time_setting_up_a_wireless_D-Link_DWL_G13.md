---
title: "Infernal time setting up a wireless D-Link DWL G132"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by rasiel on 2008-07-02
i'm hoping some kind person can help this ubuntu newbie out.

i am a day one user of ubuntu. i have managed to install the OS successfully but the system does not recognize my wireless dongle. it does not appear on the device driver (only my mobo's ethernet which is unfortunately uselessly far from my router).

i looked through help, trying to be self-sufficient and not clutter up the forum.

help says to start by going to System > Preferences > Hardware Information

I don't have any such utility. nevertheless i'm assuming i will not find it there since i didn't see it in the network manager so the next viable troubleshooting step seemed to be to try installing package NDISWrapper. the help screen says to install the file ndisgtk on path System > Administration > Synaptic Package Manager

but there is no such file! (evidently the help screens were for a previous os version?)

no matter, i was a reasonably good techie in a past lifetime so i went and googled this ndisgtk on my pc, downloaded it and took my external drive to the ubuntu box. i tried opening the file but get this error:

Error: dependency is not satisfiable: ndiswrapper-utils-1.9

as a last resort i did a search here (admittedly not very in depth) but am at a loss. i suppose i can always go to best buy tomorrow and plunk down $50 for a new wireless card and then pray it works but if there's any chance to spare me having to waste the money, man, i'd be wicked grateful!

ras

---

### Post by alan34 on 2008-07-02
Hi Ras

ndiswrapper is on the Ubuntu install CD.

So go System - Adminstration - Synaptic Package Manager

Then on the top bar Settings - Repositories (on the Ubuntu tab)

Add a tick to the CD box (you may have to untick all the others for this to work, so make a note of them).

Then close and hit the search button and enter ndiswrapper.

You should find 3 packages, ndisgtk - ndiswrapper-common - ndiswrapper-utils-1.9, right mouse click and mark for installion and Apply.

You need the Windows drivers from the CD that came with your dongle, try the XP driver first (note I believe that Vista drivers do not work with ndiswrapper so do not waste your time with them).

Then go System - Administration - Windows Wireless Drivers.

Look at the help files. The lifebuoy on the top bar pretty good.

If you do not get on post again. Good luck

---

