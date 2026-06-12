---
title: "SMB Sharing / Symbolic Links"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by marx2k on 2006-11-27
I am using SAMBA share this directory called music.. as you can see it is a directory of symbolic links pointing to other locations on my hard drive...

lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:52 collection1 -> /media/hdb4/Music
lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:52 collection2 -> /media/hdd3/Music
lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:53 collection3 -> /media/hdf2/Music
lrwxrwxrwx  1 marx2k marx2k   17 2006-11-01 03:53 collection4 -> /media/hde3/Music


Here is my samba config file entry for it...
[MyMusic]
    path = /home/marx2k/music
    browseable = yes
    read only = yes
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = marx2k
    force group = marx2k

When this directory (music) is mounted in XP, XP has absolutely no problem in going into each of these directories (collection1, collection2, etc) and copying or streaming the music from within.

However, if I mount it in edgy using the command:
sudo mount -o username=marx2k,password=[ThePassword] //192.168.11.5/MyMusic music

it mounts the directories again as symlinks.. so it looks like this on my local drive..
lrwxr-xr-x  1 root   root     17 2006-11-01 03:52 collection1 -> /media/hdb4/Music
lrwxr-xr-x  1 root   root     17 2006-11-01 03:52 collection2 -> /media/hdd3/Music
lrwxr-xr-x  1 root   root     17 2006-11-01 03:53 collection3 -> /media/hdf2/Music
lrwxr-xr-x  1 root   root     17 2006-11-01 03:53 collection4 -> /media/hde3/Music

And when I try to go into any of those I get:
-bash: cd: collection1: No such file or directory

So why should it work flawlessly under XP but in Linux Im going to guess I will have to share each Music directory on each partition singularly? Is there an easier way to do this?

---

