---
title: "[SOLVED] 8.04, CIFS, nounix and Unix extensions"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by martinveasey on 2008-05-24
After upgrading to 8.04 I've found - like a lot of people - that Samba connections to NAS devices have needed to be changed.

SMBFS seems no longer to be supported and switching to CIFS caused me the same error:

mount error 20 = Not a directory

as a lot of other people. A workable solution that a lot of people have adopted is to put 'nounix' as an option in the mount command and this does allow me to make a connection.

However, this (I believe) has the effect of suspending UNIX file information and, as a consequence, the dates are not preserved on file transfer to the NAS device. This is unfortunate, as I was using the device as an incremental file backup medium using a simple cp -u command and the broken file dates mean that this is no longer working.

Has anyone any suggestions as to what I could try next? I've looked at using the ftp server on the device, but it seems to have a similar problem with dates.

Cheers,

Martin

---

### Post by martinveasey on 2008-05-26
Bump - if anyone has any suggestions?

---

### Post by prshah on 2008-05-26
> **martinveasey said:**
> 
SMBFS seems no longer to be supported and switching to CIFS caused me the same error:

Has anyone any suggestions as to what I could try next?

Suggestion: Can you not use scp or rsync? It seems to me to be the most logical choice.

---

### Post by martinveasey on 2008-05-27
Hi thanks for your reply.

I'd agree that ssh'd rsync or scp are a more workable general solution - I use these elsewhere already.

Unfortunately, the NAS box is rather limited. It provides access only via SMB and FTP services .

Cheers

---

### Post by dmizer on 2008-05-27
try the sfu option like so:
```
//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,nounix,sfu,file_mode=0777,dir_mode=0777 0 0
```

from man mount.cifs:
>        sfu
          When the CIFS Unix Extensions are not negotiated, attempt to  create
          device files and fifos in a format compatible with Services for Unix
          (SFU). In addition retrieve bits 10-12 of  the  mode  via  the  SET&#8208;
          FILEBITS  extended attribute (as SFU does). In the future the bottom
          9 bits of the mode mode also will be emulated using queries  of  the
          security  descriptor  (ACL).  [NB: requires version 1.39 or later of
          the CIFS VFS. To recognize symlinks and be able to  create  symlinks
          in  an  SFU interoperable form requires version 1.40 or later of the
          CIFS VFS kernel module.

---

### Post by martinveasey on 2008-05-28
Thanks for that - I won't be able to try it until the weekend as its at a remote site.

Do you know whether this will interfere with the NAS' ability to serve to Windows XP machines?

Cheers,

Martin

---

### Post by Iowan on 2008-05-28
Unless I misunderstand the **man mount.cifs** information, it should only affect the machine using **sfu** in the **mount** options - shouldn't affect windows (or other)  machines at all.

---

### Post by martinveasey on 2008-05-31
The "sfu" option didn't really help. Mounting the NAS allows viewing of the correct file dates on existing files - e.g. written via a Windows share, but writing new files still gives the wrong date - sometime in 2006. "Touching" the file subsequently doesn't help - unsurprisingly.

Never mind.

---

### Post by dmizer on 2008-05-31
is it possible to check/change the date on your nas device?

---

### Post by martinveasey on 2008-06-01
It is indeed possible - embarassingly, the date was set in 2006.

Changing it / enabling NTS, now means that files transferred across or created under Ubuntu take a file time equal to that running on the NAS box.

Interestingly enough, copying files across under Windows preserves the file time on the file as is.

I'm not sure whether this will have a practical effect, but it's good enough for me. Thanks for the suggestions.

Martin

---

### Post by dmizer on 2008-06-01
without the unix extensions, ubuntu relies on the nas device for the date (because date is part of the cifs unix extensions).  but of course, windows is native to samba and is able to preserve it's local date without unix extensions.

glad you got it fixed!

---

### Post by martinveasey on 2008-06-02
Thanks for that. Date change works - for some reason Windows copies preserve the date / time stamp, whereas Ubuntu under mount cifs / nounix / sfu take the current date / time on the NAS device.

I think that's going to be OK for my purposes.

---

### Post by rduke15 on 2010-01-17
Weird. If I understand this thread correctly, you lost the timestamps when you added the nounix option to your cifs mount?

Using Jaunty 9.04, I just spent a long time researching why copies didn't preserve time stamps, and the solution for me was to **add nounix to be able to preserve time stamps**.

---

