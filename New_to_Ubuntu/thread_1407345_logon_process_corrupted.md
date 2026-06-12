---
title: "logon process corrupted"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by boogieFreak on 2010-02-15
hi,  here's my problem
os=ubuntu 8.10          kernel 2.6.30.9
after tried to modify  those 2 files 
/etc/rc.local
/etc/event.d/tty1

(not sure of the path for 2nd file)

trying to make autologin but didn't work

and i must tell that after modifying  and didn't work
i backed up the original files

and now i can't login anymore : 
i'm blocked at the prompt "login" and "password"  
it comes back continually

i tried to change password via  "recovery mode"
so it's not a password issue

i think my modifications on the files have corrupted the boot process

thank you for help

---

### Post by audiomick on 2010-02-15
you could try booting into the live CD and putting your backups back in place of the modified files. You would probably have to work as root. One way is to start the file manager with root privileges using
```
gksu nautilus
```

---

### Post by boogieFreak on 2010-02-15
hi, and thank you for answer

i did back up  the original and working files (cause i can access to files with recovery mode at boot)
but the problem still remain,   and there is another strange thing : ==>  when i type the password 
it is shown in clear text   and the prompt ask a 2nd time for a password        and the logon process 
repeat again and again     

ah the joys of linux...

---

### Post by xifer on 2010-02-15
do you get this on all terminals or just tty1? or just in GUI (tty6 or is it 7)

You don't need to worry about /etc/rc.local - that may be deleted or left blank

/etc/event.d/tty1 - not sure about this but if only one is affected you might try deleting and copying another to tty1 and edit as required.

if only one username is affected you might try

passwd -d

or 

passwd -e

you may end up looking into 

update-passwd -s -v

or even
MAKEDEV

---

### Post by boogieFreak on 2010-02-16
hi, thanx for your help i have this issue at the beginning (before startx) i have only 1 account : root   update info : i have installed and uninstalled GDM  ==> possible source of my problem ?  gonna try your advice and send result   thanx for your time

---

