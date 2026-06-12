---
title: "Files from a network drive"
date: 2018-12-20
forum: Networking &amp; Wireless
---

### Post by jbcohen on 2018-12-20
I have an Umbuntu laptop running Umbuntu 18.1 and a Windows 10 box both connecting to a Western Digital My Cloud server.  I have been able to read files from the file server on the Umbuntu laptop nautilus but not open the files on the file server in umbuntu software.  I am thinking that I need to install then configure Samba for the umbuntu laptop to be able to read the file server documents, because the Windows and Umbuntu laptops are sharing the drive.

---

### Post by TheFu on 2018-12-21
Samba is a server. You just need the client-side CIFS stuff.
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide) is a guide. Basically, install cifs-utils and restart nautilus, should work for many, but in some situations, some more stuff is required.

Is "umbuntu" a new ubuntu flavor?  

BTW, [https://www.techradar.com/news/wd-my-cloud-nas-boxes-found-to-be-vulnerable-to-online-hacks](https://www.techradar.com/news/wd-my-cloud-nas-boxes-found-to-be-vulnerable-to-online-hacks) Please be very careful with My Cloud access.

---

### Post by jbcohen on 2018-12-22
I see the section called clients, in Cinnamon I clicked on places but see no network icon.  Perhaps I need to install samba first

---

### Post by Morbius1 on 2018-12-22
Man am I confused.

Are you running Ubuntu or Linux Mint Cinnamon?

And what exactly does this mean:
> I have been able to read files from the file server on the Umbuntu  laptop nautilus but not open the files on the file server in umbuntu  software.
Does that mean Nautilus can access the server but a given application cannot?
Or does it mean something else?

And the samba client has been installed by default in Ubuntu ( and all other Desktop Linux distros ) for years and that's all you need to access a SMB share.

---

### Post by TheFu on 2018-12-22
Use smb://123.123.123.123/ into the URL for most file managers works once cifs-utils is loaded. Of course, you'll need to change the IP to match the IP of your My Cloud machine.  Browsing through the GUI didn't work.

There is a connection GUI tool called **gigolo**. Install that package and run that program.  Browsing of shares only works once a specific servername or IP is entered.  Once a connection is made, then it will show up in the file manger. It worked here.

It should be understood that gigolo and gfvs access isn't a real "mount", so it doesn't show up outside GUI programs.  Sometimes a program needs a real mount like provided by the fstab or autofs methods.

A MyCloud device should support NFS.  NFS is the native way that Unix-to-Unix storage is shared.  It is faster than CIFS, runs at kernel speed and supports native Unix permissions.  This is a good thing. NFS appears like local storage once mounted, which is pretty slick.  It is mounted for the entire machine, not just 1 userid.

The first answer here: [https://askubuntu.com/questions/469368/need-help-connecting-wd-my-cloud-nas-to-14-04](https://askubuntu.com/questions/469368/need-help-connecting-wd-my-cloud-nas-to-14-04) has NFS setup data. I'm happy to help with NFS.  Been using it for over 25 yrs.  Much easier to get working than CIFS/samba.  I'd setup NFS is the MyCloud supports it.

---

### Post by Morbius1 on 2018-12-22
cifs-utils has nothing to do with smbclient. 2 different things. cifs wouldn't know what to do with a smb:// .... The two don't even know the other exists.

Is this whole thing about Rawtherapee?

I installed it and now have 3 minutes experience with it. It doesn't appear to be able to initiate a connection to a remote share. But it is Gnome compliant.

I have a server ( vub1804 ) with a share ( public )

Step1: Connect to the share in Nautilus.

Step2: Open RawTherapee. Under Places is my share: "public on vub1804.local"
[ATTACH=CONFIG]282003[/ATTACH]

---

### Post by jbcohen on 2018-12-22
Natilus sees the share, Rawtherapee and Gimp don't.

---

### Post by Morbius1 on 2018-12-22
And here is the same share in Gimp:
[ATTACH=CONFIG]282004[/ATTACH]
By any chance did you install the snap version of these applications?

**EDIT**: Connect to the server in nautilus then run this command to see it's mount point:
```
ls -al /run/user/$UID/gvfs
```
Do you see your server listed?

---

### Post by TheFu on 2018-12-22
So cifs-utils is for mount.cifs and not smbclient?

The cifs-utils package description is this:
> description:    VFS to access servers complying with the SNIA CIFS Specification e.g. Samba and Windows
, hence my confusion.

The README included in the package says this:
```
$ more /usr/share/doc/cifs-utils/README 
This is the release version of cifs-utils, a package of utilities for
doing and managing mounts of the Linux CIFS filesystem. These programs
were originally part of Samba, but have now been split off into a
separate package.
....
``` Guess that clarifies it.  I looked at the installed files from the package and mount.cifs isn't listed, but the manpage for mount.cifs is included.  Confusing.

The only programs are these:```

/usr/bin/cifscreds
/usr/bin/getcifsacl
/usr/bin/setcifsacl
```
Interesting.

---

### Post by Morbius1 on 2018-12-22
cifs-utils is a "helper" package that connects to the cifs settings already in the Linux kernel. smbclient and samba ( as in the server package ) run independently of all this which is why any changes to smb.conf mean jack to cifs and visa versa.

---

### Post by TheFu on 2018-12-22
smb.conf is for the samba server, right?  The OP is trying to make a client-side connection from Ubuntu-something to a WD NAS.

But in this thread, the OP is primarily asking about "network browsing", not mounting. That's how I read it.  Don't know anything about other threads.  But if the issue is with some GUI programs not working, then setting up an NFS mount will 99.999% work, assuming the NFS server has a sufficient implementation. 

jbcohen probably hoped for it to work like it does in Windows where a list of all the possible CIFS servers comes up and by selecting any one of them, the list of possible shared directories is displayed.   I remember that worked sometime in the past for many years, but haven't attempted to use it recently, until today.  Found a few complaints that browsing stopped working after 14.04, but I haven't a clue.

I'm making lots of assumptions that haven't been verified, like both systems are on the same LAN and no firewall is in the way on either side and that either avahi or DNS or /etc/hosts has been setup to use name-based resolution.  I don't have 1st-hand knowledge about releases after 16.04, but most of the issues I've seen for 18.04 and later were with samba servers and Windows clients.  Nothing like what jb has.

Regardless, you have much more knowledge about this stuff than I do.

---

### Post by jbcohen on 2018-12-22
Yes I installed the snap version, does it matter which one, the snap or the command line?  No such directory found.

---

### Post by TheFu on 2018-12-23
> **jbcohen said:**
> Yes I installed the snap version, does it matter which one, the snap or the command line?  No such directory found.

A little info about snaps: [https://forum.snapcraft.io/t/snap-confinement/6233](https://forum.snapcraft.io/t/snap-confinement/6233)
There is a command to see which interfaces are allowed:
```
$ snap interfaces gimp
Slot                            Plug
:desktop                        gimp
:desktop-legacy                 gimp
:gsettings                      gimp
:home                           gimp
:network                        gimp
:opengl                         gimp
:unity7                         gimp
:wayland                        gimp
:x11                            gimp
gimp:dbus-gimp                  -
gtk-common-themes:gtk-3-themes  gimp
gtk-common-themes:icon-themes   gimp
gtk-common-themes:sound-themes  gimp
-                               gimp:cups-control
-                               gimp:removable-media

```
I don't know enough to say whether these are all the permissions needed for samba to work or not.

---

### Post by Morbius1 on 2018-12-23
> **jbcohen said:**
> No such directory found.
Confused again. Is that the result of this command:
```
ls -al /run/user/$UID/gvfs
```
If it is you aren't running Ubuntu. You may be running Kubuntu.

Side note:
>                           smb.conf is for the samba server, right?  The OP is trying to make a  client-side connection from Ubuntu-something to a WD NAS.
smb.conf controls ( it's actually an override file to default settings always present in every Linux desktop ) both server and client which is why it doesn't come from the samba server package but by the samba-common package. Some settings are not at all obvious that they control the smb client and some like the "client min/max protocol" set are clearer.

---

### Post by jbcohen on 2018-12-24
Is the problem that snaps can't get to network shares?

No morbuos I am using Ubuntu.

---

### Post by Morbius1 on 2018-12-24
>  No morbuos I am using Ubuntu.                 
If you were running Ubuntu you would have a /run/user/$UID/gvfs folder. THat's where the samba client from Files mounts samba shares.
>                           Is the problem that snaps can't get to network shares?
I don't know so I I installed the snaps version of Gimp to find out.

After using Nautilus to connect to the share I couldn't find it in Gimp. On the surface it looks like it can not.

So I went back to Nautilus and went to /run/user/1000/gvfs and bookmarked it so that the "gvfs" folder would show up on the side panel of Nautilus. 

That snap-Gimp could find:
[ATTACH=CONFIG]282015[/ATTACH]

But here's the problem for me. You say you are using Ubuntu yet you have no gvfs folder so there is nothing for you to bookmark. You also say that you can connect to the share in Nautilus yet you cannot without the same gvfs folder. In short I cannot help you.

---

### Post by SeijiSensei on 2018-12-24
Mount the remote filesystem directly into the directory structure via /etc/fstab as described here: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

