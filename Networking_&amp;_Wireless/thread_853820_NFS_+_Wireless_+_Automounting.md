---
title: "NFS + Wireless + Automounting?"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by xianthax on 2008-07-08
As i've officially removed the last windows machine from my home network i've tried to move my server to NFS and ran into a bit of an issue...

The server shares a RAID 5 array under NFS and this data is accessed by multiple machines 2 of which are laptops rest are perma-wired.  All run Hardy or other flavors of nix.

In theory i have NFS setup fine, i get great performance, wired performance is basically harddrive limited as I have gigabit links with jumbo frames.

Now the problems: if i'm on a laptop the wireless doesn't come up in time to mount the shares in the fstab, i'm pretty sure i can solve this with autofs or amd. But before i do this, heres the real issue, when a laptop is plugged in to the wired ethernet and the nfs share is mounted, if the network cable is unplugged the laptop switches to my wireless automatically, but if i try to open the nfs share (i have a link under places on gnome-panel), it crashes gnome, locks the panel, alt-f2 doesn't work, basically complete puke.  In fact i'm typing this with a locked gnome-panel right now.  To make this situation worse, since i have my session restore as it was when i logged out, rebooting or restarting x does not fix the problem, i have to log into failsafe gnome and wipe out the session file in my home folder to get the process to reset.

Any thoughts on a smooth solution to this? would auofs or amd solve this problem or do i need to approach this some other way?

thanks

-Xian

---

