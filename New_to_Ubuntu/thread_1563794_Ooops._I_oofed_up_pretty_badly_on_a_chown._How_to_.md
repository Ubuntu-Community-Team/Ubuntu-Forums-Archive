---
title: "Ooops. I oofed up pretty badly on a chown. How to restore sudo access?"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by justinmiller87 on 2010-08-29
Here's the setup:

I have my shared drive that I keep my documents folders on that is used between Ubuntu and Windows 7. I created symlinks to everything, but then my /home partition I actually do have set up started getting bogged down, since I didn't leave much space there. As such, I moved my .wine folder over to said drive and created a symlink to it.

Well, now whenever I try to run something in wine, I was being told I wasn't the owner. Sure enough, I look at my .wine link, and root owns it. Well, genius me decides to run the following:
sudo chown -RLv justin .wine
Long story short, now whenever I try to do anything sudo, I get this:
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

If I run whatever I was trying to sudo now without sudo, I'm root. Great.

How can I get my stuff back to normal?

---

### Post by arrange on 2010-08-29
If it's just the *sudoers* file, then boot into *recovery mode*, choose *root*, and *chown* the file back to root. But I'm afraid there's more in store for you :( Back up before you reboot!

---

### Post by fslezak on 2010-08-29
So you did this:
```
sudo chown -RLv justin .wine
```And got this:
```

sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

```Well, you shouldn't have used the -L flag or the -v flag.

You seem to not be TRULY root, you just have root control.

[SIZE=4]NO GUARANTEE: proceed at your own risk:[/SIZE]

Try: ```
 chown -RLv root:root .wine
```to restore the ownership to root.

Then: ```
chown root:root /etc/sudoers
```to restore ownership of /etc/sudoers to root (UID 0).

---

### Post by justinmiller87 on 2010-08-29
Rebooting and running chown root:root /etc/sudoers worked, but now for some reason it still won't let me change the ownership of the .wine directory and I have to run wine stuff as sudo, which is quite annoying. If I try it from the command prompt, I get an error that .wine isn't a directory; if I try it from a gksudoed nautilus, I can select myself from the dropdown list, but it then immediately reverts back to root.

Does that have anything to do with the fact that it's symlinked to an NTFS drive?

---

### Post by arrange on 2010-08-30
> **justinmiller87 said:**
>  ...
Does that have anything to do with the fact that it's symlinked to an NTFS drive?I think so, NTFS file permissions are different from Linux. You can use *uid=1000* in the mount options to change the owner of ALL files within that partition, but I would recommend using NTFS partitions to store _data_ (photos, videos, documents,...), not configuration files, programmes etc (" system files") anyway.

---

### Post by justinmiller87 on 2010-08-30
> **arrange said:**
> I think so, NTFS file permissions are different from Linux. You can use *uid=1000* in the mount options to change the owner of ALL files within that partition, but I would recommend using NTFS partitions to store _data_ (photos, videos, documents,...), not configuration files, programmes etc (" system files") anyway.
It pretty much is being used for data only. In Windows 7, that partition is my f: drive, and I moved my entire users profile onto it. Then when I installed Ubuntu, I symlinked to those folders from /home in order to maintain data integrity. I only moved and symlinked .wine because I was running out of room on my small /home partition. Maybe I should switch it back and figure out something else I could get rid of.

---

