---
title: "network a windows and linux computer"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by computerguts on 2010-06-06
I have a windows computer and an Ubuntu Linux computer and I was wondering how you could network the two computers together with an Ethernet cable to transfer data between the two computer. 
Thanks

---

### Post by spiky001 on 2010-06-06
hi I think you will need a cross over cable to share between them, Ubuntu should be able to see the windows share but you will need to install samba on Ubuntu for windows to share

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mapes12 on 2010-06-06
I found Samba to be a nightmare. I use PyNeighborhood like this:-

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

### Post by rolnics on 2010-06-06
I found [this HOWTO thread]("http://ubuntuforums.org/showthread.php?t=202605&highlight=upgrade+samba") helpful with my samba setup. Although I know what mapes12 is talking about! I was pulling my hair out at one point, then suddenly it all worked......after that magic reboot?! ;)

---

