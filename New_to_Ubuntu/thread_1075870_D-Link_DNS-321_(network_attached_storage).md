---
title: "D-Link DNS-321 (network attached storage)"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by ogger on 2009-02-20
Can anybody help me to install the DNS-321. It work once so far after restarting the drive, but not since then. I can work with it from my Windows computers. What do I need to read etc.? I posted this earlier in the this week in the forum under hardware, but hopefully in this more appropriate category for me, I get a response. 

Thks

---

### Post by yeats on 2009-02-20
So is this attached to your computer that is running Ubuntu, or on a Windows computer on your network?  Either way it won't hurt to install Samba through Synaptic or do

```
sudo apt-get update
sudo apt-get install samba
```

in the terminal.  Try accessing it again after the install and it may "just work."  If the issue is that it's attached to your Ubuntu station and the Windows computers can't see it, you'll have to do some configuration, but maybe someone here can help.

---

### Post by ogger on 2009-02-20
Thanks very much for responding. 


samba was up-to-date. the storage device I try to install connects to my wireless netgear router. Other computers (windows) using this router see the device and can read/write files on it. My Ubuntu 8.10 computer doesn't 

... actually right now it does again after restarting the device. I am afraid however when I restart the computer it will be gone again like before. [EDIT: YEP, I JUST RESTARTED AND AGAIN I CANNOT ACCESS THIS NETWORK DRIVE.] 

The mount entry is:
gvfs-fuse-daemon on /home/[username]/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=[username])

Maybe I can automount it in fstab to force it to not go away again? What would the entry be?

---

