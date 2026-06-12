---
title: "Samba, I think...."
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by maeks84 on 2007-05-24
First, I'd like to explain what I'd like to do and then I would like someone to confirm that Samba will work for this.

When connected to the Ubuntu computer....
1)  Read/Write anywhere on the entire drive
2)  Access the DVD Drive/Card Reader/External Drives/etc as though they were directly connected to the other computer.  (Other computer is currently Mac OS X 10.3.9)  So I can import photos from a SD card, watch a DVD that's in the Ubuntu machine, burn a DVD, etc.

If Samba will do this, which I think will but want to be sure, do I have to *install* anything on either machine.  Or do I just have to configure them.  I'll probably ask some more on this, but I'll play with some of the information from other posts first and see what happens.  Thanks.

---

### Post by maeks84 on 2007-05-25
[COLOR="Red"]Bump[/COLOR]

---

### Post by ruy_lopez on 2007-05-25
If you set up SSH on the Ubuntu box, you should be able to log into from the OS X box, using "ssh ubuntu_username@ubuntu_hostname". You can access the cdrom by navigating to /media/cdrom. If you want to transfer files to the ubuntu box, use ssh's scp command: 

```
scp localfile ubuntu_username@ubuntu_hostname:/path/to/copy/into
```

or, if you want to get a file from the ubuntu box

```
scp ubuntu_username@ubuntu_hostname:/file/to/get /place/to/put/it
```

Sharing your entire Ubuntu filesystem using Samba isn't a great idea. SSH will give you access to everything on the Ubuntu box. Plus, unlike samba, it encrypts the connection.

---

### Post by maeks84 on 2007-05-25
Thanks, ruy_lopez.  The commands work, so now I have a way to do it.  Better off than I was.  However, if possible, I would like to be able to access the Ubuntu files via the Desktop on the Mac.  Just like when I connect to another mac.  As well as having any disks, we'll say a CD inserted in the Ubuntu computer, appear as though it had been inserted on the Mac.  Do I need Samba to 'share' the CD Drive and other mounted volumes?  Then maybe NFS?? to access the hard drive on the Ubuntu?  Or can I use ssh to mount the Ubuntu drive on the Mac?

---

