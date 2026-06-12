---
title: "How is Ubuntu as a home media and file store solution?"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by AZ1972 on 2011-02-09
I have increasingly relied on my mobile devices to do things that I used to do with my desktop pc.  I read, browse, follow news, listen to music and so forth on my iPhone and iPad.  I use my Windows laptop for school work, RDP for work, and to play what games I still have time for (not a serious gamer, just MMOs and flash games really).  I really only log my desktop on to archive email off of various accounts once a month or so.

I was thinking of cannibalizing that hardware and creating a raid 0 type media server.  I do need one place to access and store my ever increasing set of music, pictures, videos, and personal documents, and saved downloads.  I often share these files between various devices and it can get daunting to keep them synched, so a single storage area makes sense.   I currently use a WD Worldbook for this, which has the added benefit of allowing me to stream to my PS3.

What I would want to do is:

- Store all media, documents, email, and software downloads to the new system.  I would prefer to continue managing the music with Media Monkey, most likely from my laptop.

- Secure these files

- Have a stable system that can be left on 24/7 without annoying updates and crashes.

- Continue streaming media to my PS3

- Convert my WD Worldbook into a backup device

- Perhaps learn to stream Hulu to the PS3 as well.

Is Ubuntu a good solution for this?  

Thanks!

---

### Post by Paqman on 2011-02-09
Yep, Ubuntu works extremely well as a server.

I'm a little concerned that you're thinking of using RAID0 for storage though. RAID0 has absolutely no redundancy or parity. While it improves speed, it cuts the reliability in half that of a single drive. A failure on either disk means you lose data.

For serving files you don't need the kind of speed RAID0 gives. You can stream HD video playback off a standard 7200rpm magnetic drive, so you'd be better off going for RAID1 if you have two disks. That way you're protected against hard drive failure. Even a single disk would be better than RAID0 for streaming media.

---

### Post by AZ1972 on 2011-02-09
Thanks Paqman, you are right the RAID idea is probably overkill for a home media server.

---

### Post by wormyblackburny on 2011-02-09
I run a Ubuntu 10.04x64 media server and it works excellent. As long as you know how to configure Samba, you should be fine (otherwise, a little Google-fu should help you). PS3 streaming works as long as you can follow some simple tutorials. Overall, you should be pleased. Once you get it working, it is reliable, and you still keep the system functional as a working desktop for web surfing, email, etc...

---

### Post by 3rdalbum on 2011-02-09
> **wormyblackburny said:**
> I run a Ubuntu 10.04x64 media server and it works excellent. As long as you know how to configure Samba, you should be fine (otherwise, a little Google-fu should help you).

There are frontends to Samba; there's system-config-samba in the repositories, or the preinstalled "shares-admin" which is simpler. Both will install the Samba server software too, if it's not already installed.

---

### Post by wep940 on 2011-02-09
Just my 2-cents worth - if you have the drives for raid, why not shadow?  You're protected against device failure so you hopefully wouldn't lose everything if one of the disks died.

---

### Post by mastablasta on 2011-02-10
for storing files it's good (i mean google uses it for it's servers, though a bit modified), but for everything else i wouldn't be so sure (syncronising devices from various manufacturers and porgrammes that need other OS etc.).

---

### Post by Paqman on 2011-02-10
> **AZ1972 said:**
> Thanks Paqman, you are right the RAID idea is probably overkill for a home media server.

No RAID is a great idea. RAID1 or RAID5 would be ideal. It's just RAID0 that's a bit dodgy.

---

