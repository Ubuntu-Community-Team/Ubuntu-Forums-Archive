---
title: "Samba file access problem"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Marinodimare on 2008-07-19
I've configured my computer to act as a samba server for my home network (nfs was too slow). There are two folders that i'm sharing: "audio" and "video". The relevant lines from smb.conf are such:

```
[audio]
path = /home/$user/audio
available = yes
browsable = yes
public = yes
writable = no

[Video]
path = /home/$user/media/Video
available = yes
browsable = yes
public = yes
writable = no
```

where it says "$user" the original file contains the real username.

When on one of my other computers, I have no problem browsing and playing videofiles, but somehow I can't get to play anything from the "audio" folder - probably some permissions error. I've tried a number of different audioplayers, on an ubuntu box as well as on my leopard system.

There is one thing that may or may not play a role here, but i'd be surprised if it would: As you can see, the path to the "video" folder contains the "media" directory. This is actually the mount point for my second harddrive, /dev/sda1.

Please help, this is rather puzzling and annoying!

---

### Post by CooLGeeK on 2008-07-19
Is there any permission difference between the two (2) folders?

I solved some of my Samba problems just by setting the right permission.
Don't know if it will help you.

---

### Post by Marinodimare on 2008-07-19
Here are the respective outputs of ls -l:

```
drwxr-xr-x  8 nillson nillson 4096 2008-07-12 11:41 audio
drwxr-xr-x 11 nillson nillson 4096 2008-02-07 22:07 Video
```

the only difference is that "media", as a mountpoint, belongs to group "root".

---

