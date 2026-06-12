---
title: "trying to mount hdd connected to ee brightbox2 on usb"
date: 2017-10-08
forum: Networking &amp; Wireless
---

### Post by garethdunley on 2017-10-08
I have a 2 TB Seagate expansion drive connected to my ee brightbox2. router. I have 2 laptops and a desktop all running Ubuntu 16.04, all of which can read and write to the drive via the network. However, I would like to mount the drive so that it appears on each machine as a permanently mounted drive accessibly from all the "save as" menus etc. 
For a start I cannot find an IP address other than that of the router and it does not show up as a connected device in the router settings.
If someone could come up with detailed instructions to do this I would be more than grateful!

---

### Post by DuckHook on 2017-10-08
I'm not sure what your situation really is, so it's difficult to advise you.

You say that you: > can read and write to the drive via the network…but then imply that you can't "save as" any work. What, then, do you mean by "can …write to the drive?

Also: > I cannot find an IP address other than that of the router and it does not show up as a connected device in the router settings.What do you mean by this? Do you mean that you can't find the drive in the router's management page? I'm unfamiliar with the Brightbox, but it's hard to believe that it doesn't have a setup page for attaching drives. How else do you declare the drive's name and presence to the LAN? How do you define permissions and restrictions? How do you define new partitions, reformat the drive or permit/restrict users?

The drive will not have any IP address other than that of the router. If this router behaves like other such devices, then adding a USB drive simply converts the router into a NAS (Network Attached Storage) device.

---

### Post by garethdunley on 2017-10-09
The drive is accessible through *network/brightbox2/seagateexpansion *but it does not show up on the system as a drive. When I try to mount it I need an IP address which it does not have other than that of the router It does show on the router management page. If I want to use it as an ordinary drive I need to be able to see it in the list of available locations and as it is only on the network I can't do that. Sorry if it seems a little vague but I can't really explain it any clearer!
I have attached a screenshot of the save as dialog showing no sign of it!
[IMG]https://drive.google.com/open?id=0Bx9DNmzaFUc5NUNqbVhtaDVNN2M[/IMG][IMG]https://drive.google.com/open?id=0Bx9DNmzaFUc5NUNqbVhtaDVNN2M[/IMG]

---

### Post by DuckHook on 2017-10-09
> **garethdunley said:**
> The drive is accessible through *network/brightbox2/seagateexpansion *but it does not show up on the system as a drive…

Actually, it probably does.

You click "other location" on the navigation panel on the left, choose "Computer", and this should allow you to navigate to wherever you want. I don't know where your path begins: whether it is:```
/network/brightbox2/seagateexpansion
```…or:```
~/network/brightbox2/seagateexpansion
```…(that is: whether your path begins at root or in your home directory), but you should be able to navigate to either place by the above method.

Based on your self-professed Linux knowledge, my guess is that your path is:```
~/network/brightbox2/seagateexpansion
```…and begins in your home directory. A further guess is that this directory was created in the past using your file manager, which automatically created a FUSE connection. Since FUSE is only a user-space protocol, you may wish to create a classical mount at boot. Instructions for doing so are here: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I am assuming that you are connecting through Samba (the Windows network sharing format). If you want to use NFS (the format more traditional among the various 'nixes), then you must first make sure that your router/NAS is configured to export such network shares and then follow these instructions: [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client)

---

### Post by garethdunley on 2017-10-15
It appears to have made itself visible and available! I don't know why but assume it just needed time to settle down!! Thanks for your help.

---

### Post by DuckHook on 2017-10-15
That's odd. I doubt that time did the trick, but so long as it works.

Good luck and Happy Ubuntuing.

---

