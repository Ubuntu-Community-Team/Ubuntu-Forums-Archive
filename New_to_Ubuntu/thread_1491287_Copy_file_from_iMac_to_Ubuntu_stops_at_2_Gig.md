---
title: "Copy file from iMac to Ubuntu stops at 2 Gig"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by videodrone on 2010-05-23
Hello all.

Noob here trying to copy large files across network.

I am trying to copy a video file of 5 Gig from my iMac to my new Ubuntu Lucid Lynx home directory using SAMBA. The file stops copying when it reaches 2 Gig. All my video files have this problem. I cannot copy large >2 Gig files from my NTFS Windows 7 drives either. My Ubuntu hard drive is formatted as ext4.

I googled it and found that my network uses SAMBA which does not handle files greater than 2 Gig unless the directory you copy to is "hard mounted" and/or "mounted with the CIFS option".

But this suggestion was from back in 2005 so is there a more modern way of copying files greater than 2 Gig across my network between my Windows-7 and iMac and Ubuntu machines ?

NOTE. The iMac and Windows machines DO happily copy >2 Gig files between them. It is only the new Ubuntu machine which wont do >2 Gig files.

thanks !

videodrone.:confused:

---

### Post by sylvester_0 on 2010-05-23
I wish I could help you... Are you initiating the copy from the Ubuntu machine? You could run "dmesg" in a terminal and see if anything funny is showing up. I've never seen a problem like yours.

---

### Post by videodrone on 2010-05-23
Thanks for the suggestion.

I found that if I initiate the file copy from my iMac, then the file copies OK and at 90MB/sec.

If I initiate from my Windows 7 machine, the file copies OK also at 90 MB/sec.

If I initiate from my Ubuntu machine, the file stops with an error message at 2Gig and only copies at 15 MB/sec.

I will try Ubuntu to Ubuntu and see what happens.

regards
videodrone

---

