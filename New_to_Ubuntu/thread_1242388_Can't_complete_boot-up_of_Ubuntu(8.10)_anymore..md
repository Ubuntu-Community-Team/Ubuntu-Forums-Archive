---
title: "Can't complete boot-up of Ubuntu(8.10) anymore."
date: 2009-08-17
forum: New to Ubuntu
---

### Post by bobc4012 on 2009-08-17
I was attempting to write to a CD and while that was taking place, I went to Firefox to do more e-mail. The system came to a standstill and was crawling. I tried to "force quit" and could not get any response. I then "powered down" and "repowered" (turned the PC off/on). After that it hangs after checking "OK" on the CUSP Printer boot. I can hit the Power Off and it will en start to power down and hangs again. 

I would like to recover my data. I booted the "live CD" but cannot get write access to my HD (read access is fine), nor can I get write access to an external HD nor a USB stick. Again, only read access. I tried creating an Admin ID with Root privilege, but it is not allowed to change permissions. Any ideas on how I can either fix the boot problem or get write access to an external HD or USB while using the Ubuntu 8.10 CD? 

Thank you

Bob C.

---

### Post by mapes12 on 2009-08-17
Hi Bob

Is your system setup with "/" and /home on separate partitions? If yes, then reinstall the Ubu Filesystem in "/" making sure you instruct the installer to leave /home untouched. You should be good to go from there.

If you still need to use the Live CD to get at your data then load the Live CD then in Terminal ```
gksu nautilus
``` should launch the GUI file browser with root permissions to get at you data. Also, if you can get to the folder where your data is located you should be able to change permissions. Right click the folder then Properties then select the Permissions tab at the top.

Mark

---

### Post by bobc4012 on 2009-08-18
Thanks for the info. I couldn't remember about the GKSU. It did allow me to plug in an USB stick and I was able to copy some files to it, but others failed to copy. I didn't try copying to my external drive yet (tomorrow). I had another lap-top that I had plugged the external drive. I had figured out a convoluted way of getting files off the Ubuntu lap-top onto the external drive. By allowing all software, I was able to install "Dropbox" while running the "live CD". I was then able to copy the files I wanted to save to the "dropbox" and pick them up with the other lap-top. Time consuming, but workable. Now, the free version of "dropbox" limits you to 2GB. Tomorrow, I'll plug in the external and copy the rest - a lot quicker. 

BTW, is there anyway I can recover and boot Ubuntu? It seems to complete the CUPS check and then hangs. I suspect it may have something to do with SAMBA. 

I did get errors when I tried to issue te GKSU command. I tried with and without using SUDO. The following are the two attempts.

=======================================================
Without using sudo:

ubuntu@ubuntu:~$ gksu nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:7299): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

------------------------------
using sudo: 

ubuntu@ubuntu:~$ sudo gksu nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:8158): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///root
--> file:///

(nautilus:8158): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:8158): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
seahorse nautilus module shutdown
ubuntu@ubuntu:~$

---

### Post by bobc4012 on 2009-08-18
BTW, I should have added that after using GKSU, I could not set the permissions to the HD (to the folders on it). Probably because of the failure of the GKSU command. However, tomorrow, I'll also try to create a "user account" with the same ID that I had when the system was working. I will then try GKSU under that ID rather than "root".

---

