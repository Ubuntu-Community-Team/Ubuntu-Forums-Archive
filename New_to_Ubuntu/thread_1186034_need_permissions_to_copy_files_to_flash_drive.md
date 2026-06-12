---
title: "need permissions to copy files to flash drive"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Twisthem488 on 2009-06-12
Recently my mothers laptop (running XP Pro) got a BSOD, causing the machine to not boot. After spending time trying to fix her machine, I decided it would be easier and quicker to just load up a livedisk to access and copy her files (2.1 gb in all) to a flash drive and then reinstall windows. I downloaded the ISO and burned it, and it is working fine. 

The problem I'm running into, is that I am unable to copy or move her files. I do not have permissions, and do not know how to get them. I know next to nothing about linux, so if this involves anything like the terminal, I may need to have hand held. Any help would be greatly appreciated, and if you need more info about the machine/situation feel free to ask. I don't even know enough to know what info I should provide.  

Joseph W.

---

### Post by Mykle87 on 2009-06-12
[This guide]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") should help you out. I have found myself in this position several times. Last time I recovered my parent's windows partition, I copied the data to my ubuntu laptop over the network. Worked out very nicely. Good luck.

---

### Post by Twisthem488 on 2009-06-13
Thanks for the response. That's a wonderful guide!
However, I like a few in the comments section am unable to copy the files thanks to a lack of permissions. My HD mounts just fine, and is easy enough to access, but I am not allowed to move or copy the files, simply look at them :(

---

### Post by Mykle87 on 2009-06-13
Ok I know see what you are saying. You don't have permission to write to the usb drive. Is it fat32 or ext3? If so, you are going to have to change the permissions of it either by right clicking the drive on your desktop or via command line. Hopefully these articles can help.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Hopefully someone else can give you a little more guidance.

---

### Post by SoftwareExplorer on 2009-06-13
You might try ```
Alt + F2
```
and then
```
gksudo nautilus
```

This will make you the "Administrator" in the file window that comes up. Usually you aren't allowed to write files to the root of the drive unless you are the root, or Administrator, user.

Hope That Helps

---

### Post by Crunchy the Headcrab on 2009-06-14
Using Linux to fix the Windows machine.  I love it :popcorn:

---

### Post by Mykle87 on 2009-06-14
> **Crunchy the Headcrab said:**
> Using Linux to fix the Windows machine.  I love it :popcorn:

Yeah man works like a charm :)

---

