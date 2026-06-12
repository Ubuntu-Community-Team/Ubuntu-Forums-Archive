---
title: "Sony MTP Rhythmbox - Permissions Issue"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by dioltas on 2009-05-01
Hi,

I have been trying for ages to get my Sony NWZ-S639F mp3 player working with ubuntu / rythmbox.

I'm almost there, if I run "sudo rhythmbox" then it detects the walkman in mtp mode, but if I just run rythmbox normally then no good. Same thing happens if I run mtp-detect, it can't connect. If I sudo mtp-detect though it seems to connect fine.

I can drag and drop through nautilus or whatever no problem, I don't have to use sudo. So it seems the problem is only with connecting using mtp.

Is there some way I can change the permissions so that rhythmbox will see the player running from a normal user account?

Thanks.

---

### Post by dioltas on 2009-05-01
Ok so I managed to fix it. Just had to add

# Sony Walkman NWZ-S639F
ATTR{idVendor}=="054c", ATTR{idProduct}=="038e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

to libmtp.rules in /etc/udev/rules.d 

Shouldn't have taken me that long to figure it out!

---

### Post by Mangus on 2009-11-14
same player with 9.10 here...I've tried everything....compiling new libmtp...configuring libmtp.rules etc....but nothing...I can't use it in mtp mode... only drag&drop via nautilus

mtp-detect hangs here:


libmtp version: 1.0.1

Listing raw device(s)
   Found 1 device(s):
   Sony: Walkman NWZ-S638F (054c:038e) @ bus 0, dev 4
Attempting to connect device(s)

---

### Post by 3rdalbum on 2009-11-14
Why do you want to use it in MTP mode? One of the big selling points of the Walkmans is that you can just drag and drop media onto it.

---

### Post by Mangus on 2009-11-14
> **3rdalbum said:**
> Why do you want to use it in MTP mode? One of the big selling points of the Walkmans is that you can just drag and drop media onto it.

The drag&drop via nautilus is a very limited method...
With 9.04 I used to connect to my walkman with amarok via "generic audio player mode" for transfer mp3s, and via MTP for album covers...

As "generic audio player" with amarok I can sync my playlists more efficently.

But now Amarok cannot "see" the walkman neither as mtp nor any other mode...

---

### Post by Mangus on 2009-11-14
Ok, now AMAROK can see the walkman as generic audio player. I've launched the hotplug.sh script that comes with libmtp.

But still can't connect it in MTP mode that's what I need to transfer album cover to the walkman.

---

