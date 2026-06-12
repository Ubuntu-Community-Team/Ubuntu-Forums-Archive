---
title: "Ubuntu 18.4/Synology DS211J - copy from NAS is OK, copy to NAS is not?"
date: 2019-03-29
forum: Networking &amp; Wireless
---

### Post by Malmberg on 2019-03-29
Hi Experts,
 First post here - hope its the right place :-)

 I have just got a strange issue with my DS211j (DSM 6.2.1-23824  Update 6). I use it primarily as storage for "evaluation video's" -  sizes varies between 6 to 10 GB.

 I have uploaded more than 200 files during the past 2 years - and can play them on my Kodi boxes.
 Yesterday I was trying to upload a new file, size 7 GB. The upload  started fine, BUT when approx 2 GB was done, I got an error message,  something with "Power error", and connection to NAS was dropped.

 I have restarted the NAS - my router and my PC - still no luck!

 But I can copy from the NAS to my PC, and I can copy from a USB drive connected to the NAS.

 Connection is standard wired gigabit, from a Ubuntu 18 PC (kernel version 4.15.0-46) - through a D-Link router to my DS211j.

 Any help would be appreciated -Thanks

---

### Post by houstonbofh on 2019-03-29
How are you copying it?  What format, connection errors...  Have you tried other formats?  Getting to 2 gig and crashing out sounds like a file system error.  Can it support large files?

---

### Post by Malmberg on 2019-03-30
@ [                                                                                                    ]("https://ubuntuforums.org/member.php?u=123056")                                                                                     [URL="https://ubuntuforums.org/member.php?u=123056"][B][COLOR=#000000]houstonbofh,

[/COLOR][/B][COLOR=#000000]Copying is either drag-and-drop, or Crtl C - Crtl V, or right click/copy - right click/paste. 
Format: MKVs - not tried other formats.
I think the issue came after a small Ubuntu upgrade some weeks ago!
[/COLOR][/URL]

---

### Post by CatKiller on 2019-04-02
> **Malmberg said:**
> I got an error message,  something with "Power error", and connection to NAS was dropped.
It sounds like you're looking at things the wrong way round. What you're describing is your NAS mounting its hard drives read-only, potentially as a result of some kind of power surge. You can access the NAS through a browser and it will tell you things about its health.

---

### Post by Malmberg on 2019-04-07
Thanks CatKiller.
I can copy files from my pc if they are less than 2.1 GB to the NAS - but I can copy all sizes of files to the NAS from a USB drive connected to the NAS!

And according to the DSM Browser is my NAS in excellent shape :-)

AND - the issue came after a smaller Ubuntu update some month ago!!

---

### Post by houstonbofh on 2019-04-07
You never said how you are connecting.  scp? cifs? nfs?  One test is try to connect in a different way and see if you still have the same issue.

---

