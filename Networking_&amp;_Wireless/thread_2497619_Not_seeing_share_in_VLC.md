---
title: "Not seeing share in VLC"
date: 2024-05-12
forum: Networking &amp; Wireless
---

### Post by bkz81 on 2024-05-12
I have a folder on my desktop that i would like VLC player to see from my firestick.   I am not too familiar with setting up samba in Ubuntu.  Also i just don't want to turn it on and be exposed for having SMB opened externally.   Any assistance on this would be appreciated, thanks.

---

### Post by TheFu on 2024-05-13
What, exactly, do you mean by 
> "I have a folder on my desktop"

Is that in the Ubuntu computer or some other computer?  "Desktop" can be the main window seen after logging into Ubuntu.  The GUI there is usually a DE - "Desktop Environment".  See the confusion?

Is the VLC installed on your system a snap package or a deb package?  You can clearly see which packages are "snaps" by opening a terminal and running **snap list**.  I ask because snap versions of VLC run under constraints that don't automatically allow access outside your HOME directory and the storage there.  Mounting other storage under your HOME over the network doesn't make network storage access work.

So, there are too solutions.

[LIST=1]
[*]Remove the snap version of VLC and install a debian package from a trusted PPA. This will remove all snap constraints, since the software would no longer be a snap package.
[*]Provided the external storage is in 1 of 2 snap approved locations, many snap packages allow access if a specific snap command is run, once.
[*]
[/LIST]

**Option 1** is easy, so I won't bother with more instructions. Google should find a reputable PPA directly from the VLC team that can be trusted.

**Option 2 follows:**

[https://askubuntu.com/questions/1034030/how-to-get-access-to-usb-storage-from-an-application-installed-as-snap](https://askubuntu.com/questions/1034030/how-to-get-access-to-usb-storage-from-an-application-installed-as-snap) explains how to allow vlc access to storage mounted under /media/.  

There are other snap programs that allow this extra access. It is a security constraint enabled by all snaps, by default.  You only need to relax the constraint once per snap package per OS install.

Also, only storage mounted under /media/ or /mnt/ are supported.  If you mount storage under some other place like I do, see below:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs 
Filesystem                               Type  Size  Used Avail Use% Mounted on
istar:/d/D1                              nfs4  3.5T  3.5T   21G 100% /d/D1
istar:/d/D2                              nfs4  3.6T  3.6T  5.2G 100% /d/D2
istar:/d/D3                              nfs4  3.6T  3.6T   33G 100% /d/D3
istar:/d/D6                              nfs4  3.6T  3.3T  136G  97% /d/D6
istar:/d/D7                              nfs4  3.6T  1.4T  2.1T  40% /d/D7
```

Then none of that storage can be accessed by any snap packaged program. There is no override to allow access via snaps either.

**Option 3** ... yes, there are more options.  You can do like I did on my desktop and switch from Ubuntu to Linux Mint.  Mint doesn't have snaps by default, so the VLC on it will be using the APT ecosystem. No constraints.  For the most part, Mint is very similar to Ubuntu. You'll be at home, just without added constraints that snaps bring.   There are lots of other distros that don't use snap packages too.

Snap packaged VLC also has constraints around plugins which may or may not provide work-arounds in the snap commands.  Many plugins for VLC are known and "approved" by the snap team, so those will be allowed.  Most people should be fine.  I've never had this issue, but I will admit that I stopped using VLC because Ubuntu distributed it as a snap and as you can see I have about 20TB of storage mounted in places that the VLC snap cannot access.

So, you have a few options.

---

