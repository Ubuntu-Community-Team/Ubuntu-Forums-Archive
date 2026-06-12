---
title: "Simple(?) file/folder permission issue"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by pcal on 2011-02-23
Sorry for having to ask -it seems too far below my pay grade, but there must a simple solution hiding from me...

If I create a folder on a cifs mounted nas drive from within nautilus on my desktop - that new folder I just created becomes unwritable because apparently, I don't own it! The exact same procedure on a local drive works fine - it's only an issue creating folders on remote drives.

If I then re-boot the machine into windoze - I can access the new folder without issue.

Any folders on said drive that were created in windoze, seem to be recognised and accessible just fine in nautilus - it's only the ones I create myself with nautilus that I don't own.?!

I understand the basics of the linux file permission structure - but how can I not own something I just created? 

Regards,

Pcal

---

### Post by nothingspecial on 2011-02-23
Because windows file systems have to be assiged linux permissions at mount.

I have no experience with cifs but you might try mounting with the noperm option, if this drive is on a secure lan

Read this

[https://help.ubuntu.com/community/MountWindowsSharesPermanently#CIFS%20remote%20ownership%20enforcement](https://help.ubuntu.com/community/MountWindowsSharesPermanently#CIFS%20remote%20ownership%20enforcement)

---

### Post by Morbius1 on 2011-02-23
Take possession of the mounted share in your mount expression. For example:

Let's say you are mounting the remote share this way:

Command: sudo mount -t cifs -o guest //192.168.0.104/nas /home/pcal/Music
Or in fstab: //192.168.0.104/nas /home/pcal/Music cifs guest 0 0

When you add a file to that mountpoint it will save as owner = nobody. pcal isn't nobody so although you can add the file you can't edit the file.

Take possession of the mounted share:
```
sudo mount -t cifs -o guest,uid=1000 //192.168.0.104/nas /home/pcal/Music
```Or in fstab:
```
//192.168.0.104/nas /home/pcal/Music cifs guest,uid=1000 0 0
```Now when you save the file it will save as owner = pcal

*This assumes your uid = 1000 - to find out run [COLOR=Blue]**id**[/COLOR] from the terminal.*

---

### Post by pcal on 2011-02-25
Thanks guys! I'll have a play with that in my next minute slice of free time...

One question that immediately springs to mind however...

The proposed solution makes changes to the mount command - which makes sense. There are however only 1 or 2 shares that get mounted at boot time (1 in most user accounts, but 2 in some).

What is the equivalent procedure for shares that are mounted only on an ad-hoc basis within nautilus after boot? Eg - if I navigate in nautilus to "network" and drill down to the share required (there are 4 discrete nas drives in various locations on the lan, 2 for streaming different types of media, one for general backup purposes, and another with "per user" file storage - most have multiple share points).

Is there a configuration file for nautilus that defines the format of the mount command to use by default?

Thanks again..


Pcal

---

### Post by Morbius1 on 2011-02-25
>  Is there a configuration file for nautilus that defines the format of the mount command to use by default?There's no need. Nautilus uses "gvfs-mount smb://" which automatically mount's the share in your home folder ( /home/username/.gvfs/sharename on servername ) with you as owner of the mount point.

In fact you could have avoided the original issue entirely by using the "gvfs-mount smb://" method via Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Gigolo can be used to automount and has a couple of advantages over the fstab method. The only disadvantage is th ".gvfs" mount point. But you can always create a symlink to a "non-hidden" directory. Just a thought.

---

