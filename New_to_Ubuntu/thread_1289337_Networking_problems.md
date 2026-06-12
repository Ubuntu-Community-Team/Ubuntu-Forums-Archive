---
title: "Networking problems"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by tybee2 on 2009-10-12
Hello from an absolute Linux/Ubuntu newbie;

I installed Ubuntu on a spare desktop (named Linux) about a week ago. I was pleasantly surprised that it was as easy and automatic as advertised. I'm connected to the internet through a wireless connection to my home XP lan. The current problem is not being able to connect Linux to a lan printer or see Linux from the other (4) computers on the lan. Nor can they see Linux.

When I first got started I _could_ see at least one other computer on the lan _and_ find and install a lan printer. However, when I tried to print a test page, Ubuntu reported success, but nothing came out of the printer. I then tried to delete and reinstall the same printer. Then everything seemed to go away. Later (after who knows what I may have done) I could not  find any printer (there are 2) nor see any other computer.

I can ping to and from all computers.

The XP computers all have Zone Alarm which have had the Linux computer IP address added. I even tried shutting down ZA on one to see if that would help but no. I don't know enough at this point to troubleshoot the setup and I'm hoping to get some help??

Thanks in advance.

---

### Post by HarrisonNapper on 2009-10-12
[http://www.faqs.org/docs/linux_network/](http://www.faqs.org/docs/linux_network/)
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

Second link is less information, but, as a consequence, is less information. Networking with Windows is easier these days, but it's still a lot like searching for a needle in a needlestack.

---

### Post by mapes12 on 2009-10-12
This is how I got my Ubu box to share resources with my XP box:

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

