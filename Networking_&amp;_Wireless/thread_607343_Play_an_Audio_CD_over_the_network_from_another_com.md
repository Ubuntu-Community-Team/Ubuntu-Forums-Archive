---
title: "Play an Audio CD over the network from another computer?"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Endolith on 2007-11-08
Is there a way to share a CD-ROM drive so that I can connect and play audio CDs from another computer?  It doesn't seem like Audio CD's are accessed in the same way that file systems are?

---

### Post by mpierce on 2007-11-08
You have to share the drive using samba, e.g.,

# A sample share for sharing your CD-ROM with others.
[cdrom]
   comment = Samba server's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes

Hope this helps...

---

### Post by Endolith on 2007-11-08
I don't want to modify my files by hand if I don't have to.  I shared /cdrom on SMB through the Shared Folders tool, and it shows up as an empty folder on the other computer, just like it does through SSH.

---

### Post by Endolith on 2007-12-18
As I said, I added it through the GUI, and it added this to smb.conf:

```
[CD-ROM]
path = /cdrom
available = yes
browsable = yes
public = yes
writable = no
```

But it doesn't seem to work for **audio CDs**.

---

### Post by trobbins on 2007-12-18
The method I would implement would be to use an application to rip the audio off the CDROM and place the wav files into a shared samba directory.

If I were really into it, I would use VLC player and stream any track I choose:

[http://www.videolan.org/doc/streaming-howto/en/ch02.html](http://www.videolan.org/doc/streaming-howto/en/ch02.html)

---

### Post by Endolith on 2007-12-18
> **trobbins said:**
> The method I would implement would be to use an application to rip the audio off the CDROM and place the wav files into a shared samba directory.

I can already play files from one computer to the other.  I want to play audio CDs.

---

