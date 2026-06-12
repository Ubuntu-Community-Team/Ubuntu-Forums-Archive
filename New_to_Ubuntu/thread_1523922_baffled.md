---
title: "baffled"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by jaeedy on 2010-07-04
Hello everyone!!
 
I am very new to unbuntu.  I just installed 10.04 on my laptop yesterday with no problems.  I was able to figure out everything I needed so far, but, I need to be able to remote desktop to my desktop which runs xp pro.  I search the forums the best I knew how and didn't really find anything.  this is just on my home network.  I like to sit outside in the gazebo and work there.
 
Please help!
 
Julie:confused:

---

### Post by kimikrishna on 2010-07-04
Team viewer for ubuntu :

[http://teamviewer.com/download/index.aspx#downloadAreaLinux](http://teamviewer.com/download/index.aspx#downloadAreaLinux)

Team viewer for windows :

[http://download.cnet.com/TeamViewer/3000-7240_4-10398150.html](http://download.cnet.com/TeamViewer/3000-7240_4-10398150.html)

---

### Post by jaeedy on 2010-07-04
Which one do I download for just a workgroup.  
 
Also is there any way I can get the unbuntu to join my workgroup?
 
Julie:KS

---

### Post by mapes12 on 2010-07-04
To access my XP box from my Ubu box I use Pyneighborhood like this:-

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

