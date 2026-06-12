---
title: "Tomboy not opening"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by chavon20 on 2008-12-15
After experiencing a few issues yesterday with file permissions, which I believe has been fixed, unfortunately it has affected other applications.  Firefox and Sunbird were a couple that wouldn't work correctly but are now up and running.  However I tried Tomboy this morning and it won't open.  I opened a terminal and I got this:
> pandj@SILVERROBOT:~$ tomboy

** (/usr/lib/tomboy/Tomboy.exe:14608): CRITICAL **: _wapi_shm_file_open: shared file [/home/pandj/.wapi/shared_data-SILVERROBOT-Linux-i686-312-11-0] open error: Permission denied

** (/usr/lib/tomboy/Tomboy.exe:14608): CRITICAL **: _wapi_shm_attach: shared file [/home/pandj/.wapi/shared_data-SILVERROBOT-Linux-i686-312-11-0] open error
**
** ERROR:(shared.c:346):shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/tomboy/Tomboy.exe:14608): WARNING **: Thread (nil) may have been prematurely finalized


There is a lot more output however I was unable to put all this info in as Im told that it contains too many images (????)
Is there anything I can do to fix this?  Or would it be worth deleting the .tomboy folder in the home folder and reinstalling Tomboy? Many thanks!

---

### Post by chavon20 on 2008-12-15
*bump* anyone?

---

### Post by plucky on 2008-12-16
> ** (/usr/lib/tomboy/Tomboy.exe:1460: CRITICAL **: _wapi_shm_file_open: shared file [/home/pandj/.wapi/shared_data-SILVERROBOT-Linux-i686-312-11-0] open error: Permission denied


Try ```
cd ~/.wapi
ls -l
```

Are you the owner? Seems like a permissions problem.You should have r/w access to those files.

It should look like this ```
-rw------- 1 pandj pandj 1277960 2008-12-16 12:06 shared_data-SILVERROBOT-Linux-i686-312-11-0
-rw------- 1 pandj pandj 3686404 2008-12-16 12:06 shared_fileshare-SILVERROBOT-Linux-i686-36-11-0

```

Other than that,I would save the **.note** files in the hidden tomboy directory,so you don't lose your notes, by renaming the directory and then get tomboy to recreate another one by opening the application.

If that doesn't work,then re-install tomboy ```
sudo apt-get install --reinstall tomboy
``` and see if that fixes the issue.

If it does,then copy back the .note files to the new .tomboy directory and you should have your notes back after the next login.


Good Luck

---

