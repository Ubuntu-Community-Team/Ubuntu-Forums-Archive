---
title: "Verify after writing to hard disk."
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Hellion DarkLord on 2011-02-27
I have been having problems with my hard drive. I have to save very important work that I'm doing and I need to know for sure that everything has actually been written to the disk or have an error pop up so I can save it to a usb flash drive.

Is there a setting for this? 

Thanks lots,

HD

---

### Post by wizard10000 on 2011-02-27
> **Hellion DarkLord said:**
> I have been having problems with my hard drive. I have to save very important work that I'm doing and I need to know for sure that everything has actually been written to the disk or have an error pop up so I can save it to a usb flash drive.

Is there a setting for this? 

No, but there are things you can do.

You can uncomment write_cache=off in /etc/hdparm.conf which will force the system to write changes to the disk immediately rather than caching disk writes until the system is less busy.  The down side to this is that if there is a power failure (or if the disk fails) you'll lose any pending disk writes.

You can reopen the file after you've saved it to insure your changes are there, or better yet...

...you can back up critical data - which you should probably be doing anyway, especially if you've got a hard drive that's a little iffy.

Hope this helps -

---

