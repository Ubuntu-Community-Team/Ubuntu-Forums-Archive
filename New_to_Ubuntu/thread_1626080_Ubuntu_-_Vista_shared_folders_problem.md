---
title: "Ubuntu - Vista shared folders problem"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by sore_fingrr on 2010-11-19
Hi,

I'm trying to get my Vista machine to access drives and files that I'm sharing on my Ubuntu, across the LAN.

Unfortunately, I keep getting a "path not found" error whenever I attempt to access the shared folders under the Ubuntu machine's shared window in Vista.

I can access my NAS shares, all my networked machines are on the same workgroup, I can also access the Ubuntu machine via it's LAN IP address (again, if I try and access individual folders, I get the "path not found" error).

I downloaded and installed Samba, then used the **right-click > share options > share folder **procedure on each folder I wanted shared. I also created matching usernames/passwords on the Ubuntu machine.

The one quirk I did come across though, was when I attempted to add shares via the **terminal: *shares-admin* > add > share path-share through: *nfs | smb*** procedure, as for some reason the only option was **nfs**, even though I had installed Samba.

I have tested the shares from this (Vista) machine, by booting into an Ubuntu install and I can access, edit add and delete to the shares (as I had intended when setting them up).

I'm not sure if it's entirely relevant but, the drives/files I'm trying to get my Ubuntu to share with Vista are located on old NTFS formatted harddisks, formerly part of my previous Vista machine.

---

### Post by sore_fingrr on 2010-11-20
situation update: file sharing works, but more through trial and error and stupidity than enlightenment.

this is really bugging me now, I can't see how I attach user-accounts and permissions to the file-shares I've shared on Ubuntu (using the *right-click>shares options* method) on an individual level. I attempted to share volumes (the drive containing several of these folders) by uing the **shared folders** under **Administration**, but although this allowed me to attach "hostnames" and IP addresses, as well as give rudimentary permissions, it doesn't seem to have impacted at all.

so far, I have a mess as far as Vista is concerned, being able to access files & folders on the ubuntu using the username-password of the main user account on ubuntu (the one in which I created the shares), which doesn't exist (isn't mirrored) on the Vista machine. I cannot get the user-accounts that I set-up on Ubuntu to mirror my Vista machine, to work at all - each time they just present the "network path not found" error...

I think I need to remove Samba and nfs and start again, with a clean Ubuntu. I really don't like the feeling of muddling my way through a problem, I want to understand what I'm doing, why it works and (at some point in the future at least) how it works.

---

### Post by Morbius1 on 2010-11-20
There are two methods of sharing folders in samba and it looks like you'r e using both or maybe not it's hard to follow. If you post the output of the following commands it will let folks see what method you are using and how you are using it:
```
net usershare info --long
``````
testparm -s
```>  I'm not sure if it's entirely relevant but, the drives/files I'm trying  to get my Ubuntu to share with Vista are located on old NTFS formatted  harddisks, formerly part of my previous Vista machine.     It does indeed matter. If you are mounting it through Nautilus then it will mount so only you have access. You could set it up in Samba to allow guest access but Samba cannot overrule Linux file permissions.

---

