---
title: "Can't open avi files from a shared folder"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by eeefresh on 2008-03-24
I've got a dual-boon laptop (Ubuntu 7.10 and Vista) and I successfully set up a shared folder on my desktop that I can now access using samba.  However, I am trying to open some avi files from the shared desktop folder and I am getting this message:

Code:

The filename "1408.avi" indicates that this file is of type "avi document". 
The contents of the file indicate that the file is of type "AVI video". If you open this
 file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file 
from a trusted source. To open the file, rename the file to the correct extension
 for "AVI video", then open the file normally. Alternatively, use the Open With menu
 to choose a specific application for the file.

The files will open with Totem, but only with a green bar across the top of the screen. They won't open at all with VLC. I tried this with several avi files and had the same issue with all of them.

I think my router broadcasts at 11 Mbps, and my laptop is getting a strong signal, so I don't think its a speed issue. I am also able to view the movies just fine when I boot into Vista.  Any ideas?
__________________

---

### Post by Eiríkr on 2008-03-24
Is your desktop file server running Windows, or Linux?  If Linux, can you open the AVI files in Totem and VLC when you're on the desktop itself?  If Vista, that OS is known to be problematic in mixed network environments, though whether that's due to Microsoft being evil or inept is hard to say with any certainty.  

Cheers,

Eiríkr

---

### Post by eeefresh on 2008-03-24
My desktop with the shared files is an XP machine.

---

### Post by Eiríkr on 2008-03-25
Just to be sure these playability problems are actually due to connecting via SMB, try copying an .avi file to your Ubuntu hard disk.  Is the green bar across the top gone from Totem?  Can VLC open the file?  If either of these is a "no", it sounds like the issue might have to do with codecs instead of Samba.  AVI is widely supported, but it still is, after all, a Microsoft format.  :-|

Cheers,

Eiríkr

---

### Post by eeefresh on 2008-03-26
I copied some to my local HD and found they still wouldn't play.  However, if I changed the extension from "avi" to "AVI", they all played!  I am still getting the green bar across the top...not sure where that is coming from, but it doesn't show up when I play the file in Windows.

---

### Post by Eiríkr on 2008-03-26
The green bars are likely a codec issue, not because any codecs are missing, but rather because the codecs don't always work too well, especially with Microsoft formats.  WMV files on my Ubuntu install often wind up looking like they've been [badly solarized]("http://images.google.com/images?q=solarized+print").  

If anyone has any advice on how to get better A/V performance for these formats, you've got at least two of us paying attention.  ;)

Cheers,

Eiríkr

---

