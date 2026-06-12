---
title: "setup wired and wireless network"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by DrScum on 2009-09-13
I have a laptop (ubuntu 9.04) using wlan which I would like to connect to a desktop via ehternet. The wlan network is a windows network and the ethernet network would be a ubuntu network since the desktop is running ubuntu (8.04) as well.
I tried for about 12h now to get this to work, but couldnt. The problem seem to be the ip settings of the ethernet cards.
I assume I have to define one of the two as a server, preferably dhcp server, but don't know how.

---

### Post by mapes12 on 2009-09-13
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

BTW - if you're running Vista or whatever the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is my MS end of the line..........

---

