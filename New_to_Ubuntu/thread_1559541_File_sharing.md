---
title: "File sharing"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Paul A C on 2010-08-23
How do I set up file sharing with Lubuntu?

In Ubuntu, I can use Nautilus and right click for Share Directory.  This does not (yet) exist in Lubuntu.

Do I use pyNeighborhood?  If so, I could do with a step by step guide to:-

1.) Enable me to see my Lubuntu directories on Windows Workgroup machines

2.) Enable me to see shared Windows (workgroup)directories on my Lubuntu machine

---

### Post by mapes12 on 2010-08-23
This is my Ubu Xp PyNeighbourhood HowTo. I don't know about Lubuntu.

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

### Post by roger_1960 on 2010-08-23
Hi

I think its in menu>preferences>sharedfolders (at least it is in peppermintos which is based on lubuntu)

---

### Post by JC Cheloven on 2010-08-23
I believe I've read elsewhere that pyNeighborhood had a bug in Lubuntu, but can't find the link right now. Anyway, pyNeighborhood didin't work at all for me in Lubuntu (that's why I did a search in the first place). 

It seems that people over there is installing nautilus to see the others machines in the network, and have no problems (other than the heavier weight of nautilus): 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9301908](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9301908)

Also it seems that pyNeighborhood is removed in the alpha3 of lubuntu:
[https://wiki.kubuntu.org/Lubuntu/Developers/Maverick/Alpha/3](https://wiki.kubuntu.org/Lubuntu/Developers/Maverick/Alpha/3)

Hope this inspires ;)
JC

---

### Post by Paul A C on 2010-08-25
Thanks for your suggestions.

I have updated Lubuntu with all outstanding upgrades, and will probably have a go at installing Nautilus tonight.  I had considered doing that anyway.  I'll post again once I've given that a go

---

### Post by Morbius1 on 2010-08-25
>  In Ubuntu, I can use Nautilus and right click for Share Directory.  This does not (yet) exist in Lubuntu.LXDE has no implementation for "sharing options" which is called usershares in samba. [COLOR=Blue]EDIT: I'm sorry that was not technically correct. Usershare itself is alive and well in LXDE but there is no implementation of it in the file manager.[/COLOR] But you can create classic shares by installing the following package:
```
system-config-samba
```As far as accessing windows shares I would suggest gigolo. You may have to install a supporting package as well so the two packages you want if you want to try it are:
```
gigolo
gvfs-fuse

```Gigolo is a network browser / mounter and can do some remarkable things like auto mount at startup and even remount if the connection is lost.

---

### Post by Paul A C on 2010-08-25
I have now installed Nautilus.  This has got me part way there.  I can now see my Windows shares on my Lubuntu box.  However, I now have two more things I need to do.

1.) How do I add Nautilus to the Accessories  program Group (& or make it my default File Manager
2.) How do I share my Lubuntu locations?  If I right click on a directory in Nautilus I DO NOT have share as one of my options.  I seem to remember that this was an option with Ubuntu.

---

### Post by Morbius1 on 2010-08-25
> If I right click on a directory in Nautilus I DO NOT have share as one  of my options.  I seem to remember that this was an option with Ubuntu.
Do you have the following package installed:
```
nautilus-share
```

---

### Post by Paul A C on 2010-08-25
> **Morbius1 said:**
> LXDE has no implementation for "sharing options" which is called usershares in samba. [COLOR=Blue]EDIT: I'm sorry that was not technically correct. Usershare itself is alive and well in LXDE but there is no implementation of it in the file manager.[/COLOR] But you can create classic shares by installing the following package:
```
system-config-samba
```As far as accessing windows shares I would suggest gigolo. You may have to install a supporting package as well so the two packages you want if you want to try it are:
```
gigolo
gvfs-fuse

```Gigolo is a network browser / mounter and can do some remarkable things like auto mount at startup and even remount if the connection is lost.

Morbius, thanks for your ideas, as usual with Linux half the problem is too much choice!
As already mentioned Nautilus allows me to see my windows shares.

Looks like to do the reverse I need to install Samba.  Will I then need to set up the share using Terminal, or will I get a GUI?

Paul

---

### Post by Morbius1 on 2010-08-25
If adding "nautilus-share" fixes the "Sharing Options" problem in nautilus it will automatically install Samba the first time you use it.

If it doesn't work the system-config-samba is a GUI and should install samba since it's a dependency.

---

### Post by Paul A C on 2010-08-25
Thanks Morbius1, adding nautilus-share seems to have done the trick (although a reboot was needed to see the sharing options box).  Interestingly pcmanfm (Default file manager) can now see the Network drives. (On the 'Go' tab. Bet I could remove nautilus after defining my shares if I wanted!

I'll play with it tomorrow.  Now I must walk the dog!

---

### Post by Paul A C on 2010-08-26
Thanks, I now have file sharing working both ways, just one problem, my Linux machine is a member of WORKGROUP, and I annot find any way of changing the (Windows) Workgroup name.

Any ideas?

---

### Post by Paul A C on 2010-08-26
> **Paul A C said:**
> Thanks, I now have file sharing working both ways, just one problem, my Linux machine is a member of WORKGROUP, and I annot find any way of changing the (Windows) Workgroup name.

Any ideas?
[COLOR=DarkRed]
I have now managed to specify the Windows Workgroup my Linux machine belongs to, I had to edit the[/COLOR] /etc/samba/smb.conf. [COLOR=DarkRed]file to do this.

[/COLOR]```
sudo leafpad /etc/samba/smb.conf 
```[COLOR=DarkRed]Then search for workgroup = WORKGROUP and replace WORKGROUP with the Windows Workgroup you wish to join.

Save your file, and reboot, you should now be in the specified Windows workgroup

Of course it would be nice if there were an easy GUI method of specifing the Workgroup(s) you want to belong to, I suppose ideally this would be an advanced Tab under folder sharing.[/COLOR]

---

