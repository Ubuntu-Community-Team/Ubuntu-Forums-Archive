---
title: "unable to mount samba network shares"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by leona on 2008-05-26
A problem I've had before, but was able to resolve.
Now after a fresh install of 8.04 I am able to mount network shares via fstab my work around via a start up script doesn't work either, but if I run the commands from the command line as root they work, but as "my" user I get permission denied.
Be going through the dmsg log to see if I can see any smbfs errors, but can't find any, I can not be sure that its trying to load it at all.
Lines in question look like 
> 
//192.168.1.1/www /home/leona/web smbfs username=user,password=pass,uid=leona,gid=leona,fmask=777,dmask=777 0 0


This should work, (it used to) so can you tell me what is up?

Thanks.

---

### Post by jetsam on 2008-05-26
Smbfs has been switched to cifs for Hardy.  The formats are slightly different.  Try this:

```
//192.168.1.1/www /home/leona/web cifs username=user,password=pass,uid=leona,gid=leona,file_mode=0777,dir_mode=0777 0 0
```

Check it with **sudo mount -a**.  It will give you error messages that way if there are any.  

You might also need to add ```
,nounix
``` at the end of the options list.  Try it without first.  It doesn't seem necessary for samba shares to me, but I think it's needed now for some windows shares.

---

### Post by leona on 2008-05-26
Thank you for replying so quickly to my distress call :)  That worked a treat, all my shares are working how they should now, I obviously must have missed that change.
Thanks again.

---

