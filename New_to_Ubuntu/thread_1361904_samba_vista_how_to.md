---
title: "samba vista how to"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by aprillia99 on 2009-12-22
Anyone know of a RECENT "how to" set up samba with vista to share folders im having trouble with them.
Thx

---

### Post by audiomick on 2009-12-22
Hi. Don't know of any how-tos, only this thread. Start by looking at the links in dmizers signature.
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by mapes12 on 2009-12-23
If you're looking to share files etc. from a MS machine with a Ubu machine the simplest method I found was to use PyNeighbourhood. Samba was too complicated to configure. Here's a guide I wrote which worked for me:

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

BTW - if you're running Vista or whatever the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is the MS end of line from now on..........

---

### Post by Morbius1 on 2009-12-23
Are you still having problems or was this resolved by the "too long of a host name" problem you had in an earlier post?

---

