---
title: "USB drive share has been removed after 9.04 upgrade"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Matt26 on 2009-05-06
after my upgrade to ubuntu 9.04 i noticed that my external USB hard drive no longer has a share set like it used to- how do set up the share on a USB drive again.

thanks.

---

### Post by cariboo on 2009-05-06
How were you sharing the drive? With Samba or NFS?

---

### Post by Matt26 on 2009-05-06
> **cariboo907 said:**
> How were you sharing the drive? With Samba or NFS?

with samba, i believe since all of my other NTFS drives are shared via samba.

---

### Post by Matt26 on 2009-05-07
anyone?

---

### Post by Tom Mann on 2009-05-07
Hi Matt,

Do you not have the option to share the drive on the right click menu (right click over the hard disk)?

Failing that, Ubuntu may have backed up your original configuration when you upgraded, which you can find with one of the two following commands in Terminal:

```
ls -R /etc | grep smb
ls -R /etc | grep samba
```

You *could*(YMMV) try to restore the backed up file over the current file. This could lead to problems, and I can't tell you the filename at the moment as I'm not at home :(

NB: Anyone tell me if I got the ls syntax right?

---

### Post by Matt26 on 2009-05-07
> **Tom Mann said:**
> Hi Matt,

Do you not have the option to share the drive on the right click menu (right click over the hard disk)?

Failing that, Ubuntu may have backed up your original configuration when you upgraded, which you can find with one of the two following commands in Terminal:

```
ls -R /etc | grep smb
ls -R /etc | grep samba
```

You *could*(YMMV) try to restore the backed up file over the current file. This could lead to problems, and I can't tell you the filename at the moment as I'm not at home :(

NB: Anyone tell me if I got the ls syntax right?

no, i do not have that option... i will take a look for the files you mentioned and see what happens.

shouldn't i have the right-click option for sharing the drive or at least the Sharing tab within the Properties dialogue for the drive?  how would i go about accessing these options otherwise?

---

### Post by Tom Mann on 2009-05-07
Ok... Got it.

The file that has been overwritten should be /etc/samba/smb.conf
If you run ```
ls /etc/samba
```you may have more than one file that reads along the lines of smb.conf.

If you're really struggling post the output of the above command here.

---

