---
title: "Cannot connect to existing Samba share from 8.04"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by piersb on 2008-04-25
I'm experiencing a problem connecting to a Samba share on my main storage server (Ubuntu 7.10) from my laptop since upgrading the laptop to 8.04.

Error message:
[I]Can't display location "smb://192.168.23.13/homes/"

The specified location is not mounted[/I]

There is a desktop shortcut for the Samba share on the desktop after the error, which if you look at the properties of, it starts counting the amount of files etc on the share. So it does look like it can see the share, just can't mount it.

All my other ubuntu systems (all running 7.10) can connect fine.

Has anyone else experienced this issue and does anyone have an idea of what might be causing this.

Piersb

---

### Post by bhold on 2008-04-25
> **piersb said:**
> I'm experiencing a problem connecting to a Samba share on my main storage server (Ubuntu 7.10) from my laptop since upgrading the laptop to 8.04.

Error message:
[I]Can't display location "smb://192.168.23.13/homes/"

The specified location is not mounted[/I]

There is a desktop shortcut for the Samba share on the desktop after the error, which if you look at the properties of, it starts counting the amount of files etc on the share. So it does look like it can see the share, just can't mount it.

All my other ubuntu systems (all running 7.10) can connect fine.

Has anyone else experienced this issue and does anyone have an idea of what might be causing this.

Piersb

Similar problem here. Since installing 8.04 I cannot access any disk shares on  my XP system from my Ubuntu system. Strange thing is that the shared printer on XP works fine. When I go to Places -> Network, I can see the Windows Network icon, then double-clicking on that shows the MSHOME workgroup, then double-clicking again shows the KARENH XP server. But thats as far as I get, another double-click shows none of the shared folders. This worked fine on 7.10, so maybe there is some configuration step I have forgotten on the 8.04 system??

(I just tested accessing these disk shares from Linux Mint and Debian - works fine.)

---

### Post by piersb on 2008-04-25
Looks like this might be a bug that was not fixed before release  of 8.04. The following link details exactly the same issues I have, mounting an authenticated homes share. 

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520")

Hopefully this will get fixed soon!

---

### Post by bhold on 2008-04-25
Thanks for posting the link to the bug. After reading it I came up with a workaround using smbfs. Here is what I did, although maybe there is a better way - I am far from a networking expert.

1. Used synaptic to install smbfs.

2. Added my XP system to /etc/hosts

3. Use extensions to the mount command, enabled by smbfs, as follows...

sudo mount -t cifs //karenh/mydocs /mnt --verbose -o user=bhold

where karenh is the XP system name in /etc/hosts, mydocs is the XP share name, /mnt is the directory at which to make the shared files available, and bhold is the XP user name. 

You will be prompted for a password - supply the XP password, not your linux password.

4. When done, you can umount with the following syntax...

sudo umount -t cifs //karenh/mydocs

---

