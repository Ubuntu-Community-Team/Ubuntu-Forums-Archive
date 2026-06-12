---
title: "Video won't playback over network"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by MrV-3309 on 2006-12-17
First off - forgive the cross post.  Wasn't sure if this belonged in the Network or Multimedia forum.


Problem - Computer with Ubuntu won't play video files hosted from my main computer.

- Will play them fine when copied to the Ubuntu computer.

- Will play MP3 files sitting on main computer.

- Recognizes files as video files (launches correct program, video player screen goes black like it's about to start playing, but stays black and never starts video)

- Does the same thing using either the built in Movie Player or VLC.

- Main computer is running WinXP Pro.



My brother in-law convinced me to try Ubuntu for my media player (instead of Win98 which I was running).

I have this computer hooked up via cat5e through my router (the two computers are actually only separated by a wall).

Had everything working 100% under win98, so would seem to be a Ubuntu issue. Some sort of network latency issue????

I'm running version 6.06 LTS

Thanks greatly for any help anyone can provide. I'm a complete Linux newbie. Haven't touched UNIX since people were asking me "Internet......What's the internet???". Good times.

---

### Post by Zrock on 2006-12-17
Having the same problem... tryingn to run through a remote desctop and video starts on the host but on the client its just a blue screen

---

### Post by dio525i on 2006-12-17
as far as i know the problem is with a package that is updated in Edgy (so i'm not sure why it doesn't work for you in 6.06)  you could try the same resolution though;

you have to mount your NFS in Ubuntu


```
sudo mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword 
```

to add perm.

```
sudo gedit /etc/fstab
```

then add this line

```
//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0
```


this is all outlined [here]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently")

---

### Post by midnightflash on 2006-12-20
I have the same problem...
No videos over LAN.

Mounting the NFS manually cannot be the real solution... :-/
Other distributions are doing this the right way without... and I'm using Ubuntu on my (very mobile) notebook, so I really don't want it this way.

---

### Post by dio525i on 2006-12-20
i agree...i have the same problem...not to mention i have a server setup with 4 different harddrives in it...and i can't mount my regular user account and have write acess to all of my harddrives....

i'm still scouting for a proper solution...it seems that the only one that most people have come to is either to mount it or downgrade to dapper

if you hear of anything let me know...i'll do the same

cheers

---

### Post by midnightflash on 2006-12-21
[https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/60326](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/60326)

There are several bug-reports... and the culprit is found.

And so they might work on it.

---

### Post by Derspankster on 2006-12-21
Add me into the mix. I'm having exactly the same problem. After reading until I was blue in the face, I found the bug report. I never had this issue with Dapper but I'm not going back because Edgy is a much better performer.  However, until this is resolved, I won't be going ahead with my planned Ubuntu file server. Bummer!

---

### Post by WetWired on 2007-10-05
I am having the same problem.

---

