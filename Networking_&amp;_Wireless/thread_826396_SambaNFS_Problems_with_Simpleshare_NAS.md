---
title: "Samba/NFS Problems with Simpleshare NAS"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by LabRat79 on 2008-06-11
Okay I'm having a lot of problems here getting my NAS (A 500 GB Simpleshare) to talk to Mythbuntu (8.04)...

I can mount the shares in samba just fine like so: 

```
sudo mount -t smbfs //192.168.0.102/media/music /mnt/music -o rw
``` 

It doesn't recognize the hostname but the IP it does see, so thats how I mount it. So it mounts up fine, I can see the files using ls or in my file manager, but when I try to read one of the files, I get "File not found" errors. This is true for music files in Xine, video files in mplayer, and text files in nano from terminal. 

Also the drive claims to support NFS, but I can't get it mounted at all, even after googling for hours for some specific fixes for NFS on this drive...

Anyone know what the problem is with samba? Or maybe a way to get mounted with NFS? 

Any help would be much appreciated this is really putting a damper on my HTPC plans :(

---

### Post by dmizer on 2008-06-12
you can mount //server/share, but not //server/share/path

the syntax is:
//server/sharename
where "sharename" is the name you give to the top level share on your NAS.

so, if you have a share called media, with three subfolders (music, movies, and photos for example), you will have to mount media and then browse to music, movies, or photos.  if you want a separate mount for each of these, you'll have to create a share for each of them on your nas, so you can mount directly like so:

```
sudo mount -t smbfs //192.168.0.102/music /mnt/music -o rw
sudo mount -t smbfs //192.168.0.102/movies /mnt/music -o rw
sudo mount -t smbfs //192.168.0.102/photos /mnt/music -o rw
```

the only other way i can think of to do this would be like so:
```
sudo mount -t smbfs //192.168.0.102/media /tmp/media -o rw
sudo mount /tmp/media/music /mnt/music
sudo mount /tmp/media/movies /mnt/movies
sudo mount /tmp/media/photos /mnt/photos
```

if you take a look at the second link in my sig, you will find directions on how to enable name resolution for your Mythbuntu box, as well as lots more information on how to mount your nas device.

---

### Post by LabRat79 on 2008-06-13
Thanks much for the response, after a little more searching I stumbled upon a very nice solution...if anyone else is interested I used the 'smbnetfs' package, this mounts my entire network to /mnt so I can just go to /mnt/home/server/share/subshare, it works out beautifully.

---

