---
title: "script doesn't work anymore???"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by noworldorder on 2010-06-20
I created a script that mounts an external hard drive.  

#!/bin/sh
mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare 
mount -t smbfs //192.168.1.104/Backup /mnt/Backup

It is in my startup and has been working fine.I recently upgraded to 10.04 Ubuntu and I don't know if this has anything to do with it. 

 A while after the upgrade something changed.  Normally when booting up a permission screen for the scrip would pop up, I would enter the password, and it worked.  

But suddenly it started going past the login for the script and the mouse could not click on anything.  I discovered that I could press alt-o and the mouse worked again.  And I would activate the script in terminal and it would work.

Any idea why this would suddenly change and what I can do to get the script working again.

Thanks!

---

### Post by Diabolis on 2010-06-21
You can do this by placing entries similar to the one below in **/etc/fstab**. You can also specify the username and password there.
```

//10.0.1.37/samba-share /media/mount-point cifs username=usuario,password=pass,defaults 0 0

```

Check **System / preferences / Startup Applications**, try to call your script from there like this:
```
/bin/bash absolute-path-to-your-script
```

Maybe your script is being called before you have communication to the external drive and placing a delay for it will help.

---

