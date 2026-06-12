---
title: "Unison or Synkron and Ubuntu??"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by rgotten on 2009-05-12
I am trying to find a way to syncronize my files from my ubuntu server into a linksys NAS (storage device)that i have on my network. i have being looking online and came accross Unison and Synkron...My plann is to unistall the Desktop version of Ubuntu and only use the server edition...so:

1) Will this be possible with the server edition
2) Which one is recomended Unison or Synkron
3) Any other idea on whow to syncronize/backup/copy automatically my Ubuntu server data files into my windows NAS

Thanks

Rgotten

---

### Post by yeats on 2009-05-12
Are you able to access the storage device from your current Ubuntu installation?  Storage devices are not usually OS-specific, meaning that Ubuntu is able to interact with FAT and NTFS filesystems pretty well.  Is there a specific reason to uninstall?  Any Ubuntu installation can act as a server (depending on the data needs).

---

### Post by rgotten on 2009-05-12
> **chrissharp123 said:**
> Are you able to access the storage device from your current Ubuntu installation?  Storage devices are not usually OS-specific, meaning that Ubuntu is able to interact with FAT and NTFS filesystems pretty well.  Is there a specific reason to uninstall?  Any Ubuntu installation can act as a server (depending on the data needs).

Yes I am able to access the storage device from my current ubuntu installation (desktop), even though i would like ot know how to do the same thing from the command prompt (server). Reason to unistall desktop is that the box is going to be in a closet, so why waste resources on the system?.

---

### Post by rgotten on 2009-05-14
Anybody can give me an opinion if i should use Unison, Syncron or something else to do the backups/syncronization as i have describre above..Thanks

---

### Post by xfran on 2010-01-11
Hi,

I answered you about unison vs. synkron in an old thread:

[http://ubuntuforums.org/showthread.php?p=864890http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=72753961#post8648901](http://ubuntuforums.org/showthread.php?p=864890http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=72753961#post8648901)

In sum I used Synctoy on windows and wanted something at least as fast for Ubuntu. Unison turned out to be slow and having problems with file permissions, I have installed and run today Synkron 1.6.0 and I am quite happy with the tool.

It took like half an hour for the first analysis but for successive analysis and syncs, I think it is as fast if not faster than Synctoy, so I am quite satisfied with this one.

I think it must be easy to use it with your NAS, if you can share a folder in the network from it (kind of Samba server ???). I am not sure about this, but I am sure other people in the forum know better.

Good luck!!!

---

### Post by jonbonjovi on 2011-01-12
> **xfran said:**
> Hi,

I answered you about unison vs. synkron in an old thread:

[http://ubuntuforums.org/showthread.php?p=864890http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=72753961#post8648901](http://ubuntuforums.org/showthread.php?p=864890http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=72753961#post8648901)

In sum I used Synctoy on windows and wanted something at least as fast for Ubuntu. Unison turned out to be slow and having problems with file permissions, I have installed and run today Synkron 1.6.0 and I am quite happy with the tool.

It took like half an hour for the first analysis but for successive analysis and syncs, I think it is as fast if not faster than Synctoy, so I am quite satisfied with this one.

I think it must be easy to use it with your NAS, if you can share a folder in the network from it (kind of Samba server ???). I am not sure about this, but I am sure other people in the forum know better.

Good luck!!!
Hi! Could you explain how did you install Synkron? I use Ubuntu 10.10 64bit.

---

