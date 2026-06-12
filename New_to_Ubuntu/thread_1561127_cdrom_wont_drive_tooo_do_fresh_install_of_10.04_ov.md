---
title: "cdrom wont drive tooo do fresh install of 10.04 over 8.10"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by salima on 2010-08-25
from reading other threads i gather this is a problem and the solutions either didnt apply or havent worked for me.

i have tried:
                                 sudo mount -t iso9660 /dev/scd0 /media/cdrom
and i got:
                                  mount: block device /dev/scd0 is write-protected, mounting read-only  
 mount: /dev/scd0 already mounted or /media/cdrom busy  
 mount: according to mtab, /dev/scd0 is mounted on /media/cdrom0 



the cdrom would not eject, and i had an icon on the desktop which when i tried 'unmount volume' i got the error "only root  can unmount". 
 but when i did a restart i got it out. 

same as before, i am getting this error when i try to use the cd:
                                  Unable to mount Ubuntu 10.04
 DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
 

the file i downloaded was the 10.04 desktop i386 iso
what to do next?.

---

### Post by uRock on 2010-08-25
Are you trying to mount the ISO or have you already burnt it to disk?

---

