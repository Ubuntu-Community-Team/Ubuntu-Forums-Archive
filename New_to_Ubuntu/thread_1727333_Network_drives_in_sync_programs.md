---
title: "Network drives in sync programs"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by indusarts on 2011-04-12
I am attempting to sync folders from Unbuntu to folders on a network server.  Samba is setup and working properly.  I can see the server in Nautilus, can mount the folders(I am assuming) by the right click option - the network folders show on my desktop.  I have also bookmarked them in Gigolo and if I unmount them, they get remounted.

However, these folders are not available in any of the sync/background programs I have installed via Synaptic.  I can not see them in my media folder and I can't find the .gvfs folder.

How do I access these folders for back up or sync?

Thanks
Mark Springer
industrial arts

BU - Sync programs on my computer
back in time
deja dup
grsync
lucky backup
simply backup
unison

---

### Post by QLee on 2011-04-12
You'll likely find the .gvfs folder in your home folder. It will be a hidden folder as signified by the leading "." (dot). Does the command, mount, entered in a terminal show you the folders?

Are you trying to do the backup as root? I do see this launchpad bug about .gvfs that is old but won't be fixed. It appears that others don't have access to the .gvfs and that this was by design.
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361)

---

### Post by indusarts on 2011-04-13
After searching some other threads I found out how to view the .gvfs folder.  I was then able to select the folders in the backup program.

This seems kind of convoluted.  Is this the usual way for programs (like backup or sync programs) to access network folders?  It's strikes me as not very intuitive.

Thanks

Mark Springer
industrial arts

---

### Post by QLee on 2011-04-13
[QUOTE=indusarts]...
This seems kind of convoluted.  Is this the usual way for programs (like backup or sync programs) to access network folders?  It's strikes me as not very intuitive.[/QUOTE]

I think that what is hanging you up is your familarity with Windows systems and trying to make GNU/Linux things fit into that mindset. In another thread, another poster gave you a link which makes me think he also thinks the same. 

Even though you post here, clearly you are not an absolute beginner and I'm not going to treat you like one. From other posts, I believe you are resourceful, confident and try things on your own before posting questions (I'm sure of that because your system changes so much between questions).

The topic you'd likely be interested in is, mounting a network drive. Currently you're relying on the GUI to mount it for you and your troubles stemmed from the location that that automagic uses. You're going to want your backup NAS to have a mountpoint that whatever backup solution you choose can find and you might want it automounted at boot from fstab and automate your backup, or include a mount and unmount command in a script. In any case you might benefit from reading this manual page, enter the command, man mount.cifs, in a terminal window.

So, try to get that folder mounted somewhere (I like to create a folder, /mnt/BkUp, but you could put it anywhere it is available to the the user doing backup) 

Next time you post, show us the actual commands you entered and the exact error message when you have a failure, GNU/Linux error messages often have good clues and people looking at your post will point out any errors in your command or fstab line. Believe me, the samba experts here will point out any mistakes or possible security issues. ...and you can always ask a moderator to move your thread to the Networking and Wireless sub forum if you aren't getting the help you need here. I'm writing to you in general terms because I am not a samba expert and might not think of all posibilities at first glance and also because what I've mentioned above is not the only way. The "best" way for an individual is related to the way that person works and what they understand.

So, back to your question, "usual", no, for example I have an entry in fstab for my backup drive but optioned as noauto, thus to backup I mount it, then rsync to it, then unmount it.

The more detail you post about the exact commands you are using the more chance that lookers will offer changes or corrections and the fact that you are showing so much effort will encourage people to help you, even if you complain some. Once you understand about the differences in a Linux and a Windows filesystem and how to mount things as you want them, I expect your evaluation of backup solutions to go smoothly.

---

### Post by indusarts on 2011-04-14
I thought I had posted this reply last nite, but I don't see it in the thread so I am re-replying.

Thanks for you vote of confidence, however your reply...

[I]you're relying on the GUI to mount it for you and your troubles stemmed from the location that that automagic uses. You're going to want your backup NAS to have a mountpoint that whatever backup solution you choose can find and you might want it automounted at boot from fstab and automate your backup, or include a mount and unmount command in a script. In any case you might benefit from reading this manual page, enter the command, man mount.cifs, in a terminal window.

So, try to get that folder mounted somewhere (I like to create a folder, /mnt/BkUp, but you could put it anywhere it is available to the the user doing backup[/I]

is a big "huh" for me. As for the exact commands, I am working solely from a GUI.  I understand that Linux is different from Windows, but my confusion stems from the fact that the GUI seems to indicate that I have accomplished the task (mounting the network folder) but obviously this is not the case as the backup/ sync programs don't see these drives.

I have searched for how to mount a network drive and have read this document - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) - but still do not understand how to mount the folders I need properly.

Could you please point me to info on how to mount a network drive?

Thanks

Mark Springer
industrial arts

---

### Post by linuxrev on 2011-12-19
> **indusarts said:**
>  ...but my confusion stems from the fact that the GUI seems to indicate that I have accomplished the task (mounting the network folder) but obviously this is not the case as the backup/ sync programs don't see these drives.


Very interesting thread! I think I find myself in similar confusion as Mark. My NAS (Buffalo Drive Station) is mounted automagically, I can access it read/write through Nautilus, but I don't have a clue where exactly it is mounted. Not in ~/.gvfs, not in /media, not in /mnt, nor anywhere else I could think of. I also searched these places as root to be sure it was not simply a matter of permissions. I am on Ubuntus 10.04 LTS with GNOME 2.30.

The NAS appears in Nautilus as 'share on [IP_address]'. If I go to Places > Network, I can also access the NAS as 'share on [hostname]'. But to setup Grsync I do need a clear mount point. How the hack...? Editing /etc/fstab didn't work so far, but I'll give it another try.

(As for Windows & finding out your network connections: total confusion is the *only* thing I could say about that -- if that is of any comfort to those struggling here.)

---

### Post by gandaran on 2011-12-19
> **linuxrev said:**
> Very interesting thread! I think I find myself in similar confusion as Mark. My NAS (Buffalo Drive Station) is mounted automagically, I can access it read/write through Nautilus, but I don't have a clue where exactly it is mounted. Not in ~/.gvfs, not in /media, not in /mnt, nor anywhere else I could think of. I also searched these places as root to be sure it was not simply a matter of permissions. I am on Ubuntus 10.04 LTS with GNOME 2.30.

The NAS appears in Nautilus as 'share on [IP_address]'. If I go to Places > Network, I can also access the NAS as 'share on [hostname]'. But to setup Grsync I do need a clear mount point. How the hack...? Editing /etc/fstab didn't work so far, but I'll give it another try.

(As for Windows & finding out your network connections: total confusion is the *only* thing I could say about that -- if that is of any comfort to those struggling here.)
[http://r3dux.org/2009/02/how-to-mount-a-nas-in-linux-via-samba/](http://r3dux.org/2009/02/how-to-mount-a-nas-in-linux-via-samba/)

---

