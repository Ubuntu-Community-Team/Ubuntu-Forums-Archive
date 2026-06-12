---
title: "Trying to read CDROMs prepared by MacOS 9"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by desconocido on 2010-11-02
I am running Ubuntu Karmic on my laptop.

I am trying to read some CDROM-R disks that were created on an Apple Macintosh running MacOS version 9. They were prepared using standard Mac system software if I remember correctly. I want to read some jpeg files that are on them.

After inserting the CDROMs, Nautilus ignores them completely.

Using System->Administration->Disk Utility, it tells me there is nothing on the disk (I forget the precise info). Using cd and ls at a terminal window does not help either.

Is there a way to read these disks from a Ubuntu machine?

---

### Post by catav on 2010-11-02
I use UNR 10.10 on my EeePC 1000HE. UNR does not recognise any CD/DVD on USB DVD drive. Before 10.10 I used to 10.04 on same PC and there were no problem. Another problem is, "*GLIB WARNING* ** GLib - getpwuid_r(): failed due to unknown user id (0)" message on booting and PC freeze.

---

### Post by andrewc6l on 2010-11-02
Here's a link that explains some of that (assuming your CD is HFS):

[http://andrewmemory.wordpress.com/2010/08/06/reading-fonts-from-a-mac-cdrom-and-converting-them-to-truetype/](http://andrewmemory.wordpress.com/2010/08/06/reading-fonts-from-a-mac-cdrom-and-converting-them-to-truetype/)

Be careful - some files on HFS filesystems have two forks (a data fork and a resource fork). Depending on what you're interested in, you may be able to just copy the files or you may have to do a few handstands to get what you want.

---

### Post by desconocido on 2010-11-09
> Here's a link that explains some of that (assuming your CD is HFS):

[http://andrewmemory.wordpress.com/20...m-to-truetype/](http://andrewmemory.wordpress.com/20...m-to-truetype/)

Thanks, I have used Synaptic to install macutils and hfsutils.
I will try them out tonight.

---

### Post by desconocido on 2010-11-11
hfsutils worked a charm. After installing, I typed

```
$ sudo mount -thfs /dev/cdrom /mnt/mac/
mount: block device /dev/sr0 is write-protected, mounting read-only
```

After this, the cd-rom is visible in nautilus at /mnt/mac/ and you can click on folders to get to where you want to be.

Later, I typed 
```
$ sudo umount /mnt/mac/
```

---

