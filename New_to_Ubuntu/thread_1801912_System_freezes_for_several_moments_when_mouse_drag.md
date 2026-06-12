---
title: "System freezes for several moments when mouse dragged to bottom right of screen"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by mpro589 on 2011-07-11
Hi all,

First of all, I'm new to this forum and a bit new to Ubuntu (and Linux) as well - so I'm sorry in advance if I'm doing something wrong.

I've installed Ubuntu 11.04, installed gnome 3 (with help of a guide on the net) and updated my graphics card driver to the latest - ATI 11.6.

Because there is a know problem with my graphics card drivers and gnome 3 (I am using ATI Radeon 3470HD) I've shifted back to Unity.

And now for the reason of this post. As you have probably read in the title, I've encountered a strange behavior to which I couldn't find an explanation
When I'm moving my mouse to the bottom right of the screen and try to move it back to the center (or anywhere else), the whole system seems to freeze for a second or two.
Is it a bug or am I missing something here?

---

### Post by abybaddi on 2011-07-11
Install ubuntu-tweak. Open it. Desktop settings->Compiz settings. Look for the bottom-right corner of the miniature of the shown desktop. Click on the drop-down menu and select - (nil). That should solve the problem.

---

### Post by mpro589 on 2011-07-11
Thank you for your reply.

I've installed it but the setting was "-" (nil) already.

The problem, sadly, is still there...

---

### Post by mpro589 on 2011-07-12
Anyone?

---

### Post by kevinchui828 on 2011-08-17
I've got 2 solutions

1.fully uninstall ati drivers downloaded from ati then use the open source ati gfx driver shipped with ubuntu

2.fully uninstall ati drivers downloaded from ati then install catalyst 11.2

uninstall ati drivers how-to:[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

for further information about the open source ati drivers, have a look below

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

