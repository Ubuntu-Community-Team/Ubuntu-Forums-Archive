---
title: "Having some samba permissions issues"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by rudeboymcc on 2007-03-19
HI. I'm trying to set up samba so i can access my folders from a windows xp laptop. I want some of the folders to be read by anyone (not writable), but some to only be writable by me (using a password prompt hopefully). 

At the moment I've managed to get all folders to show up with no password prompt and all of them are just readable (there's no prompt so i can't log in). I'm trying to make V only writable by me.  I've tried adding "write list = michali" but thsi just says "you don't have permission" and doesn't prompt for a username and password. 

Any help is appreciated:
```

[global]
workgroup = MSHOME
server string = Samba
netbios name = ABIT
#hosts allow = XX.XXX.XXX.XXX XX.XXX.XXX.XXX
security = share
smb passwd file = /etc/samba/smbpasswd

wins support = no
[D]
path = /media/Downloads
available = yes
browseable = yes
public = yes
writable = yes
force user = michali

[V]
path = /media/VIDEOS
available = yes
browseable = yes
public = yes
writable = yes
security = user
write list = @michali


  
[AllVideos]
path = /media/VIDEOS/My Videos
available = yes
browseable = yes
public = yes
writable = no



```

---

### Post by rudeboymcc on 2007-03-19
bump - any help is appreciated...

---

### Post by madcow72 on 2007-03-30
Hey!  I just came across your thread while looking for something else.  When I set up samba, I usually follow steps as illustrated in [this howto]("http://ubuntuforums.org/showthread.php?t=202605").  I also add the option "writeable = yes" to the [MyFiles] section if I want to be able to write or make changes.  

I'm not sure how you've set up samba on your computer, but that howto works for me everytime.  On a side note, however, it looks like Feisty is doing  a really good job of automating samba so that I don't think I'll have to do anything so manual anymore, other than a slight tweak to the /etc/samba/smb.conf file from time to time to change permissions of shared folders.

Good luck!

---

