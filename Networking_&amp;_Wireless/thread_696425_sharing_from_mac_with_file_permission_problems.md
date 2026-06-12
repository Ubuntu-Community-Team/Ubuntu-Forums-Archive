---
title: "sharing from mac with file permission problems"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by mpc350 on 2008-02-14
I am using samba to share files from my Mac.  I transfer files to my Gutsy laptop and the files arrive with the owner as "nobody" and I cannot modify the files or their permissions.  I can see and access them though.  They also are accompanied by the "lock" symbol on the file icon.  

Do I need to change the permissions from the mac before I send them to the laptop?

Help anyone?

Thanks in advance, 

Matt

---

### Post by kyriakos1977 on 2008-02-14
this is normal samba user is nobody:nogroup
did you try sudo chown "user" "filename"
or at the worst chmod 777 "filename"

---

### Post by mpc350 on 2008-02-15
that's great!  so is there a way to change ownership for all files within a particular folder simultaneously?  Is there a way to change samba on the mac os to transfer files so they arrive as the correct owner?

Thanks
Matt

---

