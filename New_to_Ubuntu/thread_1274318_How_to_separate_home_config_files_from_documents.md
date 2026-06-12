---
title: "How to separate home config files from documents?"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by bikrus on 2009-09-24
Hi, everyone!

Is there any solution for subject?

I don't like (hate) the amount of ~/.* entries which has not been created by myself.

For example, I need to see ~/.hgignore, but I don't want to see ~/.some_app_config. Because first one is "created by me", and other are not.

I see solution: make for example /data/user and put there my documents. But many (if not all) programs suggest that my homedir (read: my documents) are stored in /home/user. So, this is not very good way.

Next solution: put all ~/.* (dotfiles-dotdirs) to ~/etc/ (or ~/config/ or ~/something_else_for_configs/). I will agree to have this (only one) dir in my home. But how to tell all programs that their configs are there? This is a problem.

So. Is there any solution to separate personal app configurations from documents?

Thanks.

---

### Post by BDNiner on 2009-09-24
You can store your documents where ever you want so long as you make sure that you have permissions to write to that folder. If keeping them hidden is something that you are trying to do then you can always place them in your desktop folder.

---

### Post by bikrus on 2009-09-24
> **BDNiner said:**
> You can store your documents where ever you want so long as you make sure that you have permissions to write to that folder. If keeping them hidden is something that you are trying to do then you can always place them in your desktop folder.

Maybe I have described my question not exactly. I often use terminal and old-style file managers (gnome-commander, krusader). In terminal, by bush defaults, home folder is /home/user - and this is good. In commanders home folder is /home/user - it's good too. But using these tools I always see many ~/.* entries. My document's directories are at the /home/user too. And to find (10% of all entries in my home) documents created by myself I always should see that heap of ~/.* . And I don't want to hide every ~/.*. Only created by apps. Example: I like to see ~/.hgignore. This is my problem.

I don't want to put my documents to desktop. First: because I like to keep desktop clean of unnecessary things for desktop. Second: to access my document, in your scenario, I should "cd desktop" and then begin to work. That approach is increasing my PATHes too. That not good.

I understand, that current approach was developed by years. But I don't like it.

For example. When I was under Windows, I have not use Documents'n'Settings at all. I have separated disk D: and my staff was there. Maybe I should try /data/user approach? Hm...

I asked this question because I think somebody already have this task too. I don't like to invent bicycle.

(Why? Why the architectors of *nix "duplicate" root tree in /usr, /usr/local, but not in home? Why there are no ~/etc folder by default? - sorry for emotions...)

Anyway. Thanks for reply.

---

### Post by ajgreeny on 2009-09-24
Some people use a separate partition for their documents and files, eg photos, music, videos, OpenOffice docs etc etc, and leave all the hidden ~/.folder where they are.  Most of those hidden folders and files are configuration and can not be moved to another location without causing all sorts of problems for the applications they relate to.

This is a sort of halfway house between the ubuntu default, which is to have everything on one partition except for swap, and the separate home partition arrangement, which puts all your docs and configs on a separate /home partition.

To do what you want you will need a root partition of perhaps 10 -12 GB minimum, which will include your /home/username folder, but also make a new /data partition for docs and just tell your various applications to save to folders in this new data partition.  You then need to ensure that the data partition mounts at boot time, that you are the owner of the mount folder, and have read/write access to it, which you can easily do with a line in /etc/fstab.

---

### Post by bikrus on 2009-09-24
Thanks for reply. I think, I'll make /data/user for my documents.

Sad, but true...

---

### Post by webwiller on 2009-09-24
I personally have mounted a separate partition on /mnt/data and I store all my docs and all my staff in there. Never had any problem with this management. I have a quad-boot and all my OS'es recognize and are able to access that separate ntfs partition. For my Win7 is D:\ and for Ubuntu is /mnt/data.
That's it ;)

---

