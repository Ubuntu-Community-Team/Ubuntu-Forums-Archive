---
title: "Best way to stream media from ubuntu server 10.04 to PS3"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by CharlesA on 2010-06-17
Hi,

I am wondering what the best/lightest weight way to stream media to a PS3 from a machine running Ubuntu server 10.04.

I saw MediaTomb, but I don't know how well it'll work if I've got 3-4 VMs running, as well as Samba, SSH, etc on the same server.

Does anyone have any experience with this sort of thing?

---

### Post by CharlesA on 2010-06-19
Anyone?

I've found a few software packages like MediaTomb, and PS3MediaServer, but I was wondering what the best choice would be.

---

### Post by MrWES on 2010-06-19
> **CharlesA said:**
> Anyone?

I've found a few software packages like MediaTomb, and PS3MediaServer, but I was wondering what the best choice would be.

Been using Mediatomb for several years without issues.

---

### Post by CharlesA on 2010-06-19
> **MrWES said:**
> Been using Mediatomb for several years without issues.
Thank you. :)

I think the main concern I have is that I won't be able to use MediaTomb, or other software, to stream ripped dvds (they are only VOB files, no transcoding done with them) to the PS3.

---

### Post by MrWES on 2010-06-20
> **CharlesA said:**
> Thank you. :)

I think the main concern I have is that I won't be able to use MediaTomb, or other software, to stream ripped dvds (they are only VOB files, no transcoding done with them) to the PS3.

change the file extension to .mpg and they'll play fine via Mediatomb

Bill

---

### Post by NCLI on 2010-06-20
PS3 Media Server is the best media streamer I've ever used. It works on all platforms, and streams to all DLNA-compatible devices(Like the PS3). It also transcodes all incompatible formats, and has an excellent support forum.

Just run:
```
sudo add-apt-repository ppa:freshwww/ppa
sudo apt-get update
sudo apt-get install ps3mediaserver
```

You can also install it manually if you don't trust this PPA, just ask in the support forum if you have any problems.

---

### Post by CharlesA on 2010-06-21
Thanks. :)

I'll be giving ps3mediaserver a shot. :)

I got it installed, now I got to figure out how to configure it I think. Fun times.

---

### Post by MrWES on 2010-06-21
> **CharlesA said:**
> Thanks. :)

I'll be giving ps3mediaserver a shot. :)

I got it installed, now I got to figure out how to configure it I think. Fun times.


[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4329]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4329")

---

### Post by CharlesA on 2010-06-21
Connection time outs suck.

---

### Post by CharlesA on 2010-06-21
Connection time outs suck.

---

### Post by CharlesA on 2010-06-21
Connection time outs suck.

---

### Post by CharlesA on 2010-06-21
Connection time outs suck.

---

### Post by CharlesA on 2010-06-21
> **MrWES said:**
> [http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4329]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4329")

Thanks. :)

The only problem I ran into was that my server couldn't keep up with transcoding on-the-fly and I didn't really find any info on how to enable CUDA on a Ubuntu 10.04 box that is running headless.

---

### Post by MrWES on 2010-06-22
Yah my server doesn't do transcoding well, so I don't use it.

---

### Post by Malkhut on 2011-01-29
I have installed according to your suggestion.  I'm sure this is a total n00b question, but how do I get it to run?  It's listed as installed in the Synaptics Package Manager

I tried going to the directory with PMS.sh and running it using the ./ command, but it says that I don't have permission.  Is there a way to create an icon or something?

> **NCLI said:**
> PS3 Media Server is the best media streamer I've ever used. It works on all platforms, and streams to all DLNA-compatible devices(Like the PS3). It also transcodes all incompatible formats, and has an excellent support forum.

Just run:
```
sudo add-apt-repository ppa:freshwww/ppa
sudo apt-get update
sudo apt-get install ps3mediaserver
```

You can also install it manually if you don't trust this PPA, just ask in the support forum if you have any problems.

---

### Post by Malkhut on 2011-01-30
If anyone is interested, I did manage to get this working.  I uninstalled and reinstalled using these instructions:

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

I think the update command in my above attempt gave me the newest (unstable) version.  Downloading manually, I picked an older, stable version.  It sees my PC and transcodes straight out of the box, no effort required.  Beautiful!

The only problem now is that the ps3 doesn't stream soft subtitles, so I have to find a way to hard-sub my subtitled files.

Also, it automatically sees my entire computer.  I would like find a way to configure it to only see my public folder.  That way, I don't have to search the file system, and I keep some privacy. ;)

---

### Post by ursa2k7 on 2011-01-30
chmod 755 on the PMS.sh 


> **Malkhut said:**
> I have installed according to your suggestion.  I'm sure this is a total n00b question, but how do I get it to run?  It's listed as installed in the Synaptics Package Manager

I tried going to the directory with PMS.sh and running it using the ./ command, but it says that I don't have permission.  Is there a way to create an icon or something?

---

### Post by ursa2k7 on 2011-01-30
Navigation/Share Settings Tab
at the bottom Shared Folders box
plus to add 
X to remove


> **Malkhut said:**
> If anyone is interested, I did manage to get this working.  I uninstalled and reinstalled using these instructions:

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

I think the update command in my above attempt gave me the newest (unstable) version.  Downloading manually, I picked an older, stable version.  It sees my PC and transcodes straight out of the box, no effort required.  Beautiful!

The only problem now is that the ps3 doesn't stream soft subtitles, so I have to find a way to hard-sub my subtitled files.

Also, it automatically sees my entire computer.  I would like find a way to configure it to only see my public folder.  That way, I don't have to search the file system, and I keep some privacy. ;)

---

### Post by Malkhut on 2011-02-04
I figured out how to get it working.  Thanks for the advice.  Surprisingly easy to use.

---

