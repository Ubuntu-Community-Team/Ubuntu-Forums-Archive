---
title: "How do I share a drive in Ubuntu?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by TheMustangZone on 2010-01-21
I've been using Ubuntu exclusively for a while now and I'm starting to get the hang of it.  However, I have an external hard drive that I store music and backup files on that I want to share so my wife can see it from her Windows XP machine over our network.  Is this possible?  I've been searching through the menus, but I can't seem to find anything that has to do with "sharing" files or drives.  I stopped using Windows completely about a year ago on my machine, so no dual boot or anything like that.  Thanks in advance for any help.
 
Rob

---

### Post by uncle-c on 2010-01-21
A forum guru and moderator called dmizer has written  various tutorials on this subject. You will have to install software called SAMBA. I read all his notes / posts and achieved file-sharing relatively painlessly. Just do a search on this forum for dmizer + samba + windows and I'm sure something will come up. I do not have his links on hand but  some kind soul will post them up.

A link to help :

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by ibuclaw on 2010-01-21
I'm pretty certain there should be a sharing option. ;)

Right-click on the folder you wish to share, and go into its "Properties".

You should see a "Share" tab. Select and check the box "Share this folder".
If you don't have Samba installed, it will prompt you to download + install it the service.

That is the easy part. The hard part is connecting the Windows workstation to your Linux computer.

If I recall correctly, you edit /etc/samba/smb.conf
```
gksu gedit /etc/samba/smb.conf
```
Find **workgroup =** and change it to:
```
workgroup = your_windows_workgroup
```

Then on Windows, I think it is:
```
\\linux_hostname
```
in a Run Cmd box.

Regards
Iain

---

### Post by blackened on 2010-01-21
Setting up samba can look intimidating. Here is just about the simplest thread, and the one I often refer to, for getting started: [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605").

---

### Post by uncle-c on 2010-01-21
> **blackened said:**
> Setting up samba can look intimidating. Here is just about the simplest thread, and the one I often refer to, for getting started: [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605").

Ah yes a true classic !

---

### Post by TheMustangZone on 2010-01-21
Thanks a lot guys!  With this kind of support system, why would anybody use Windows?  :D  It looks like I have a project to work on when I get home.

---

### Post by blackened on 2010-01-21
> **tinivole said:**
> I'm pretty certain there should be a sharing option. ;)

Right-click on the folder you wish to share, and go into its "Properties"...

Nice, I'd never noticed this. That's about as dead simple as you can get I suppose.

---

### Post by theozzlives on 2010-01-21
The only "tricky" thing is setting up a mount point, other than that sharing is as simple as installing Samba and right-clicking on the folder (mount point).

---

### Post by TheMustangZone on 2010-01-21
> **blackened said:**
> Nice, I'd never noticed this. That's about as dead simple as you can get I suppose.
 
I hadn't tried that, yet.  I was trying to right click on the drive and go to properties to share it, which doesn't work.  I never thought of trying a folder IN the drive.  Oh well, that's why I love Ubuntu so much, things just "work".

---

### Post by TheMustangZone on 2010-01-22
Hey guys,
I've been working on this sharing thing and everything installed just fine.  However when I click the "share this folder" box and the the "create share" button I get this message:

> net usershare' returned error 255: net usershare add: cannot share path /media/disk/Complete Albums as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.
How do I resolve this?  Thanks again.

Rob

---

### Post by TheMustangZone on 2010-01-25
I was hoping someone saw my last post.  I'm still stumped.  Thanks.

---

