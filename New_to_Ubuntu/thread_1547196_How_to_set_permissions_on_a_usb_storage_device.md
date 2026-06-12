---
title: "How to set permissions on a usb storage device?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by willwin on 2010-08-06
I wonder if anyone has been able to do this: I would like any usb storage device (flash key, mp3 player, cell phone) that is plugged in to be accessible only to a user with administrative privileges. An ordinary user should not be able to read or write to the given usb storage device. I'm trying to set this up in a community drop-in centre with many computers. I've been able to "lockdown" every aspect of Lucid except for this.

---

### Post by Zorgoth on 2010-08-06
gconf-editor for 

/apps/nautilus/preferences/media_automount should be set as mandatory and turned off in gconf-editor.

I'm not sure how to then automount them as root though...  You could of course manually mount them.

---

### Post by wjwing_40 on 2010-08-06
Thanks, but I've tried that already and it doesn't stop usb device from mounting with rw permissions for all users when plugged in.

---

### Post by The Cog on 2010-08-06
The mount options you need to play with are **umask**, **uid** and **gid**. Use the command **man mount** for details, look at special options for ntfs filesystems. I guess uid and gid need to be 0, and umask needs to be 077. But I have no idea how to configure automount to set these values. If you can't find how to configure automount as you want, you may have to configure not to automount at all, and then have the admin users manually mount the usb devices with the correct options.

---

### Post by willwin on 2010-08-06
Thanks, I'll look into all of that and see what I can do.

---

