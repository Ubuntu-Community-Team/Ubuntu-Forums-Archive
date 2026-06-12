---
title: "File copying errors"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-10-03
Well I finally got my files to the ext HD by doing it from the live CD. Now when I want to copy them to my documents it says no room. I have a 100GB HD and only the operating system on it. I think it is counting all the files on removable drives as it says 53gb used. How can I get it to look only to the installed hard drive. I can never back up as when I connect an ext HD it immediately counts that space as used so I connect with my files to copy and it says no room. This backing up in Ubuntu is a total mess no matter what I try or fix I can never get my files onto the laptop.Thanks for the help.

---

### Post by scragar on 2009-10-03
[quote=man page]       -x, --one-file-system
              stay on this file system
[/quote]
Use the -x flag.

---

### Post by cmcanulty on 2009-10-03
OK how do I do that type it in terminal?

---

### Post by scragar on 2009-10-03
Wait, having read that again you're backing up, there's an easy way to do that:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

```
sudo su
tar cvpzf backup.tgz --exclude=/{proc,lost+found,backup.tgz,mnt,media,sys} /
```When it's done you'll have a file called backup.tgz in the current directory that contains you're whole file system(excluding anything you likely don't want, like the contents of external media).

---

### Post by cmcanulty on 2009-10-03
OK how do I do that type it in terminal?

---

### Post by scragar on 2009-10-03
Well that can just be copied and pasted in, I recommend that first you make sure you're wherever you want to save the archive, since it will likely be large, so copying it will take a while.

---

### Post by cmcanulty on 2009-10-03
What I need to do is copy an 80GB folder of my docs to an empty my docs and since it counts the backup on the ext HD as used it says no room for 80GB when laptop has an empty 100GB HD except for the operating sys uuntu 9.04. I googled ubuntu -x flag and got no info.

---

