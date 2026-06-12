---
title: "Printer Sharing Help Needed"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by zebraneo on 2009-09-16
I use Ubuntu but the printer is located on Xp, I have 2 computers on the network, How do I connect the Ubuntu computer to the printer.

---

### Post by wobin77 on 2009-09-16
Add a printer, with it's local IP. 
Worked for me

---

### Post by mapes12 on 2009-09-16
The following is how I share files between Ubu and XP. The same routine also picks up the printer connected to XP:

Go into Control panel in XP and enable "File and print sharing". Then go to the folder/printer you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders and printers. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

---

