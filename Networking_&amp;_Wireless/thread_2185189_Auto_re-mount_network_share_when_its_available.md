---
title: "Auto re-mount network share when its available?"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by Thee on 2013-11-01
Hi,

I got a NAS that I'm mounting using fstab at boot. But if my NAS device is not turned on at boot time, it doesn't get mounted of course.
So I'm looking for a simple way to remount my NAS share after boot without needing to type *sudo mount -a* every time. It would be ideal it gets mounted automatically when its turned on, or when I try to access it.

Any ideas?
Thanks

---

### Post by Morbius1 on 2013-11-01
> or when I try to access it.
That's why the gods created AutoFS:

*** Install autofs:
```
sudo apt-get install autofs
```
*** Edit the autofs master file to define the parent folder for all your Samba connections:
```
gksu gedit /etc/auto.master
```
*** Add the following line to that file - right above the "+auto.master" at the end of the file:
```
/mnt/SMB /etc/auto.smbshares --timeout=30 --ghost
```
*** Create the /etc/auto.smbshares file:
```
gksu gedit /etc/auto.smbshares
```
*** Define the mount point and mount parameters in that file. An example:
```
nas-documents -fstype=cifs,rw,uid=1000,iocharset=utf8 ://nas/documents
```
Or if credentials are required:
```
nas-documents -fstype=cifs,rw,username=name,password=secret,uid=1000,iocharset=utf8 ://nas/documents
```
[COLOR=#0000cd]* EDIT: It looks like I'm going to be referencing this post in the future so I should point out that you can protect the credentials used in the line above by chmod'ing the file to 600:*[/COLOR]
```
sudo chmod 0600 /etc/auto.smbshares
```
*** Then restart the autofs service:
```
sudo service autofs restart
```
You share will be mounted the instant you access /mnt/SMB/nas-documents

---

### Post by Thee on 2013-11-02
Such a long procedure for such a simple thing. I wish Ubuntu did this by its self. But thanks a lot for the help, I'll try it out :)

---

### Post by Bucky Ball on 2013-11-02
Why samba? Needs to be accessed by Windows box too?

---

### Post by Thee on 2013-11-03
Thanks a lot, works as expected :)

---

### Post by ndangerfield on 2014-01-10
@Morbius1 thanks for your info. Works fine - but is it possible for the drive to show up under the "Network" heading on start up? Currently this only shows up after I've accessed my NAS using "Browse Network"

Thanks

---

### Post by Morbius1 on 2014-01-11
Using the above procedure for reference you would create a bookmark in Nautilus to /mnt/SMB/nas-documents. It will show up under "Bookmarks" which is right above "Network"

---

