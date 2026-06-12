---
title: "Move Home Folder to My Samba Server"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by msimon1960 on 2009-10-12
I have a Dlink DNS-323 which is a Samba 3.x server.

I am running 9.04 Ubuntu on my laptop.  It's a clean install.

How do I move my home folder to the network server?

---

### Post by mapes12 on 2009-10-13
Not sure if this is what you're looking for but a good HowTo to help you on your way:

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by Boondoklife on 2009-10-13
While I see how this could be useful, but in reality you would have all sorts of issues if you only have it on the server. The best thing to do would be some sort of a sync that way your files are backed up. If you device supports it you could do an rsync to back up the home dir to the server.

---

### Post by msimon1960 on 2009-10-13
> **mapes12 said:**
> Not sure if this is what you're looking for but a good HowTo to help you on your way:

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Thank you for the link -- I had trouble finding anything relevent on this topic.  From bitter, bitter experience I've learned to always keep my data on a separate drive or partition from the system files.  

I will read this link in detail -- I'm hoping to put my home folder on my NAS Server so that my family can access it from their Windows machines too.

Matt.

---

### Post by msimon1960 on 2009-10-13
> **Boondoklife said:**
> While I see how this could be useful, but in reality you would have all sorts of issues if you only have it on the server. The best thing to do would be some sort of a sync that way your files are backed up. If you device supports it you could do an rsync to back up the home dir to the server.

Can't sync -- my laptop has only 100Gig -- I have nearly a 1/2 terabyte on my server (Samba 3.0.24 on a D-Link DNS-323 NAS.

Matt.

---

### Post by beastrace91 on 2009-10-13
Might I suggest creating symlinks for all your important data folders? (Such as Documents, Downloads, ect) this is what I do to keep all my important data going when my system dies hehehe

~Jeff

---

### Post by Boondoklife on 2009-10-13
> **msimon1960 said:**
> Can't sync -- my laptop has only 100Gig -- I have nearly a 1/2 terabyte on my server (Samba 3.0.24 on a D-Link DNS-323 NAS.

Matt.

While I don't think you would need to "sync" the entire 500GB, the only real suggestion to fit close to this would be to mount the samba share via the fstab at boot, and then setup symlinks as the other person said for the relevant files. Though this still leaves the issue of if you are not on the network then you will not have access to the files.

---

### Post by msimon1960 on 2009-10-14
Thanks for the feedback...

I'm fine with leaving my stuff on the server.  The rest of my family accesses those files from their Windoze workstations (music, videos, pictures, etc.).  It's also safer than having it on my laptop.

I use the same model at my office -- I set up a server and all the desktops connect to it for file service.  I'd like to use a linux file serve at work but my experience with SAMBA has been abysmal from Dapper through Jaunty.  I find most of the Samba system doesn't work -- never been able to get it functioning properly.  I can tweak it to get partial functionality after days of work -- not the experience I'm looking for in an OS.

Please don't jump all over me for my criticism of Samba.  The apparent inability to get simple networking running is the only reason I don't embrace Linux wholeheartedly.  Ironic since Unix was designed at a networking system.

Matt.

---

### Post by Boondoklife on 2009-10-14
Ehh everyone has their own opinion of different apps so I'll let you slide with that one =P.

Samba can be a bear somedays but it is not impossible especially if you look into just manually configuring via the smb.conf. I just dont see a way to have the "Roaming Profile" effect with a linux client, unfortunately the best you could do would be to sync your data when connected to the server. You could do this with a script. Good luck and post back if you find another option!

---

### Post by mapes12 on 2009-10-15
> **msimon1960 said:**
> Thanks for the feedback...

I'm fine with leaving my stuff on the server.  The rest of my family accesses those files from their Windoze workstations (music, videos, pictures, etc.).  It's also safer than having it on my laptop.

I use the same model at my office -- I set up a server and all the desktops connect to it for file service.  I'd like to use a linux file serve at work but my experience with SAMBA has been abysmal from Dapper through Jaunty.  I find most of the Samba system doesn't work -- never been able to get it functioning properly.  I can tweak it to get partial functionality after days of work -- not the experience I'm looking for in an OS.

Please don't jump all over me for my criticism of Samba.  The apparent inability to get simple networking running is the only reason I don't embrace Linux wholeheartedly.  Ironic since Unix was designed at a networking system.

Matt.

Hi Matt

Many people have reported issues using Samba. For my Home LAN I use PyNeighbourhood. For me the set up is really easy and goes like this:

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

### Post by msimon1960 on 2009-10-19
I'm not sure I'm being clear here...

I'd like to have /home on my server -- not on my local machine at all.  I assumed this would be no problem for linux/unix.

My server is a dlink DNS-323 (Samba 3.x server) which mimics a Windows SMB share.

Can '/home' be relocated there?

---

### Post by Boondoklife on 2009-10-20
As mentioned the only way to do it would be with fstab, and that would be "experimental" at best. You would need to mount the share via your fstab and mount it to the /home location.

Again, never tried this and I think you would run into issues but give it a go.

---

