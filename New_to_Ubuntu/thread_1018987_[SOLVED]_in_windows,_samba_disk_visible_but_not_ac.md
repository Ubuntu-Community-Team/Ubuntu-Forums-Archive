---
title: "[SOLVED] in windows, samba disk visible but not accessable"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by anewguy on 2008-12-22
I followed this thread to set up my old PC as a file server:

[http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

My ntfs hard disk on the server is /dev/sdb1.

The server is visible under "Dwe-wrk-group" under the Microsoft Windows Network under Entire Network under My Network Places on the Windows box.  It also shows sdb1 public hard disk as per the Ubuntu server smb.conf file.  In the smb.conf file I also have the group defined as DWE-WRK-GROUP.  This matches what shows on the Windows box when I do system/properties (it appears that the view in the explorer has somehow changed the all-capital letters to lower case except for the 1st).

When I try to open/explore the shared drive from Windows I get an error saying it is not accessable, I may not have permissions, group not found.  I tried changing the group name in smb.conf to Dwe-wrk-group to match that showing in Windows in the network places, but then it loses the server.

If anyone could take a look at the link, then given what I have listed here as well, and give me some guidance it would be greatly appreciated!

BTW - the part on the 3rd part of the link where it says to sudo smbpasswd -a family I had problems with - it wouldn't take the password I was trying to create.  I've gone so far as to try sudo smbpasswd -x family to try to remove the family userid so I could try again but it fails saying "Failed to modify password entry for user family".  If I try to add again, I get the same error message.

So, I'm close - I can see the server and the disk on the server, I just can't access the disk!

Any help would be GREATLY appreciated!

Thanks in advance!
Dave :)

---

### Post by CarolinaGuy on 2008-12-22
1. Have you created a mount point on /dev/sdb1
	```
mkdir /mnt/store
```

2 Have you mounted it? 
```
mount /dev/sdb1 /mnt/store
```

3. Have you assigned permissions?

```
chmod 777 /mnt/store
```

4. Have you added the drive & mount point to your fstab?


CarolinaGuy

---

### Post by anewguy on 2008-12-22
Well, I followed the instructions in the link, which included creating a mount point of /media/store, mounting the device there, changed fstab, etc. all according to the link.  It is still giving me a permission error and saying group name not found on the Windows side.

(1) What would cause a group name not to be found?

(2) Could my internet security (Trend Micro) being doing something?  Seems weird I can see it on the network but not access it.

Thanks!
Dave :)

---

### Post by anewguy on 2008-12-23
It seems to be permissions between the Windows userid and password and samba.  I tried adding my Windows userid ("Valued Customer" - I know, it sucks) with smbpasswd and putting in my Windows password.  Smbpasswd for some reason seems to always reject password modifications even when run as su.

At any rate, after making that change, now the server doesn't show at all nor does the disk drive.

help?  :)

---

### Post by ZhiZaki on 2008-12-23
Here's some advice to try:

Make sure you've restarted Samba since the changes you made to smb.conf.

In smb.conf, try setting the share to "public" to see if can just be accessed without security.

Try `chmod -R 777 /media/storage` to make sure that it's not some funky folder permission stopping ya.

---

### Post by anewguy on 2008-12-23
Thanks for the reply.  I went back over the link I was using and found at the bottom of it (it's embarassing I didn't see it before but I was trying to go step by step) what the problem was:

Indeed, I needed to add guest ok = yes to the defs for the shared disk, and I had a syntax error in the group statement.

Now everything is working great!

Thanks EVERYONE for your wonderful help in getting me over a problem again!

Dave :)

---

### Post by ZhiZaki on 2008-12-23
Yeah, smb.conf is a mean little witch when you make syntax errors... hehe

---

