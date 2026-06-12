---
title: "Where is SMBUSERS ?"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2014-09-11
Have v14.04 installed and attempting to use SAMBA to access Windows machine and vice versa to transfer files.

Following the steps outlined here;
HOW TO SETUP SAMBA PEER TO PEER WITH WINDOWS
[LINK]http://ubuntuforums.org/showthread.php?t=202605&highlight=XFCE+access+network+computer[/LINK]

But I thing the problem lies in the conf file at this point;
```

username map = /etc/samba/smbusers

```

I see there is NO smbusers in the samba folder!  So since I added users, where did they go? If the above has been changed in the newer versions of Ubuntu, where are they?
Can't get windows to logon to samba, but I can ping the linux machine, but can't map to it.

PS. Don't know why [ HTML ] code is off ?!?!?
Thanks.
Rick

---

### Post by bab1 on 2014-09-11
> **Rick St. George said:**
> Have v14.04 installed and attempting to use SAMBA to access Windows machine and vice versa to transfer files.

Following the steps outlined here;
HOW TO SETUP SAMBA PEER TO PEER WITH WINDOWS
[LINK]http://ubuntuforums.org/showthread.php?t=202605&highlight=XFCE+access+network+computer[/LINK]


This tutorial is over 7 years old.  A lot has changed.  Also, there are errors in the instructions.
> 

But I thing the problem lies in the conf file at this point;
```

username map = /etc/samba/smbusers

```

I see there is NO smbusers in the samba folder!  So since I added users, where did they go? If the above has been changed in the newer versions of Ubuntu, where are they?

The smbusers file is **not** the file for the Samba users database.  Here is the location of the default Samba users database```

/var/lib/samba/passdb.tdb

```

The ***smbusers*** file does not exist until you create it.  It is only needed if your windows users have a different username from the Linux/Samba username.

> 

Can't get windows to logon to samba, but I can ping the linux machine, but can't map to it.

PS. Don't know why [ HTML ] code is off ?!?!?
Thanks.
Rick
Save yourself a lot of grief.  Follow this [excellent tutorial ]("http://www.jonathanmoeller.com/screed/?p=1590").

NOTE:  If you want to embed a link in your text use the advanced editor and click on the "Link:" icon.  Hint: It's between the "Indent" icon and the "Email" icon (about in the middle of the row of icons.

---

### Post by Rick St. George on 2014-09-11
Thanks Bab1 ... but apparently all I needed to do was to Reboot both machines. Then it worked. I was also playing around with my router, added a couple more IPs, and updated the firmware.  After rebooting ... all was fine.

Will consider - Case Closed.
Thanks Ubuntu . . . as I learn more and more, the more I TOTALLY want to dump Windows completely.

Ubuntu - completes me!

Rick

---

