---
title: "command to mount multiple directories in one go"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by benfindlay on 2009-04-08
I'm looking for a command that I can put into either terminal or into fstab that will mount multiple directories into another mount point.

I have recorded tv episodes on a couple of external hard drives, all in fodlers named after the show, all stored within a tv folder (i.e. /media/disk/tv/[show name]), and was wondering if there was a way to mount each [show name] folder into a folder elsewhere for the purposes of sharing(e.g. /home/user/Desktop/tv. I don't want to just share the tv folders, as there are 2 of them (1 on each drive). Then I want to add that containing folder to proftpd to share for use with media portal on another computer.

I came across [this]("http://ubuntuforums.org/showthread.php?t=1065937") post which detailed how to do it with fstab with a specific folder, but there are several directories that I would have to put into my fstab individually. I'd prefer a cleaner solution, especially one that I wouldn't have to keep updating as new tv folders are added. Would using a wildcard work in fstab?

Thanks in advance!

Ben

---

### Post by Tralce on 2009-04-08
I'm not really sure that's possible. Try using a symbolic link. However, that may cause issues if you ever have the external drive unplugged.

---

### Post by benfindlay on 2009-04-08
Thanks for the reply, unfortunately symlinks aren't an option. I want the proftpd server to be jailed to a specific directory, hence the need to mount the external drives within the jailed folder.

I've been thinking about adding a line with wildcards into fstab, for example something like```
/media/disk/tv/* /home/user/Desktop/tv/* none defaults,bind 0 0
``` but don't know if it's possible to do this and precisely what syntax I'd need to use.

---

### Post by zerhacke on 2009-04-08
I am assuming Perl's regular expressions could be used in a script called at boot time.  Let me think around on it for a bit and I'll post the script.

---

