---
title: "[SOLVED] Can NFS and Samba run simultaneously?"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by sab0403 on 2007-07-02
I made [a thread]("http://ubuntuforums.org/showthread.php?t=481617") about a week ago regarding the use of samba or nfs on a particular computer (due to the fact that I still have to interact with Windows on a couple of boxes). However... I started thinking that it's very possible that the *only* machine that needs to be accessed by Windows is my desktop, which has all the peripherals. Yet I still want to access that machine from my lap. Both my desktop and my lap run Ubuntu 7.04. The question is, can that desktop run both NFS *and* Samba? Or should I just quit it and set up Samba on both machines?

In a related question... can I run an NFS server in my lap, and a Samba server on my desktop, and still access one from the other? That would work fine with me...

Thanks in advance. :popcorn:

---

### Post by netztier on 2007-07-02
> **sab0403 said:**
> The question is, can that desktop run both NFS *and* Samba?


Yes. My Ubuntu 6.06 LTS server has been doing exactly that for more than a year now, sometimes even serving the same directory with samba and NFS.

best regards

Marc

---

### Post by sab0403 on 2007-07-02
Great!

Should I just follow the "regular" instructions to set each one up, or do I have to do something special given they'll be running together?

Also, can both share the same peripheral (a printer, for instance)?

Thanks...

---

### Post by netztier on 2007-07-02
> **sab0403 said:**
> 
Should I just follow the "regular" instructions to set each one up, or do I have to do something special given they'll be running together?


Just set each one up according to the "standard" guides. For NFS, it is very helpful (if not mandatory) to have matching usernames, UID and GID numbers on the server and all clients. 

Also, in Ubuntu, the user can't mount an NFS drive via GUI means - NFS mounts are best must be done in /etc/fstab. But each user can access it afterwards - depending on the modes of the files and directories as they reside on the server - hence the requirement for matching UID/GID numbers.

When you define Samba shares, you can define the "create mask" and the "directory mask" for each share. If Samba and NFS share the same directory, you should make sure that these settings don't collide with the settings needed for NFS.

> **sab0403 said:**
> 
Also, can both share the same peripheral (a printer, for instance)?


NFS can't share printers - it's a Network **File** System.

best regards

Marc

---

### Post by sab0403 on 2007-07-10
Got it working a couple of days ago... Thanks! Marking it as solved now...

---

