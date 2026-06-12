---
title: "photorec"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by sekani on 2009-05-08
I want to recover lost photos from a cd-rw that accidently got erased.I was trying to add some photos to the disc using CD/DVD Creator.I am trying to use photorec to recover them but on the opening page under 'select a media' it is not showing my cd-rom drive..i only have disk/dev/sda 250gb drive showing!... i do have the cd-rw with the lost photos in the drive. the cd drive desk top icon is saying that a blank cd-rw disc is in the drive...how can i get photorec to recognise this disk? I am using Ubuntu 8.10 on a Dell Inspirion 530s...thanks

---

### Post by Didius Falco on 2009-05-08
From the PhotoRec website:

[http://www.cgsecurity.org/wiki/CDRW](http://www.cgsecurity.org/wiki/CDRW)

> **Recovery of fast blanked CD-RW **

 It's possible to recover data from a quick-erased CD-RW disc without modifying it! 
When a CD-RW is fast erased, the PMA, TOC, pregap and the first sectors of your CD-RW are erased. Because the TOC has been erased, CD-RW appears as blank/empty. Because the first sectors has been erased including the headers, sectors 0, 1, 2... can't be located anymore but subsequent sectors can still be found. Unfortunatly, not each OS allows you to easilly access such sector but it works using Linux. 
To recover your lost data, run Linux version of Photorec. If CD-RW listed size is 0 or 2048 bytes, the CDROM reader firmware will block further read request, so you have to use another CDROM reader/writer. Start of the recovery is really slow because the first sectors are unreadable but usually after sector 300, data can be recovered, so be patient. 
 **  Read of previous cdrom session **

 With multi-session cdrom, it is possible to delete files of previous session. Because the files are not really deleted, it is possible to recover them. To read files from the first session, run under Linux 


```
mount /dev/cdrom /mnt/cdrom -t iso9660  -o session=0
```You could give that second method a go - I'ved used TestDisk but not the PhotoRec part.

I hope it helps...


Regards,

Didius

---

