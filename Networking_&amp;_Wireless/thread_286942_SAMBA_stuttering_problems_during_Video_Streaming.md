---
title: "SAMBA stuttering problems during Video Streaming"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by z00100 on 2006-10-28
Hi guys,

I just switched from SuSE to Edgy as a file server and so far everything is working peachy with the exception of video streaming.

I use my file server as a repository for my video and audio files which I stream to my HTPC.

With SuSE everything was working fine and there was no issues.  However after changing distros to Edgy, I have noticed that there is a fair bit of stuttering problems when I play videos.

The actual video seems to be running fine, the problem is the audio.

Can anybody shed some light on what could be the problem?  I am going crazy trying to figure this out.

:-k ](*,)

---

### Post by dmizer on 2006-10-28
humm ... how well does the video play if you play it locally?

also, how are you mounting the shared drive?  fstab?  nautilus?

---

### Post by z00100 on 2006-10-28
Sorry for not being more detailed.......

I am playing the video on my Windows XP HTPC Box.

If I copy the file locally it works just fine with no stuttering.  It's only when I stream it off my Edgy box that is stutters.

The Edgy box has samba shares set up on it.  

Coincidentaly, when I copy large files to and from my Edgy box it copies just fine and at very quick speeds.

---

### Post by dmizer on 2006-10-28
edit ....
i just realized that was a whole bunch of useless information.  you're trying to mount edgy shares on a windows machine ... sorry, i'm not gonna be much help for you there.

might start by posting the contents of /etc/samba/smb.conf

---

