---
title: "having trouble running thunderbird3 on karmic kaola"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by dagarshali on 2009-11-18
Hi, I downloaded the thunderbird3 beta 4 and extracted the zip file. I
then moved it to /opt using sudo mv thunderbird /opt/

when i changed the directory to thunderbird and ran it..i got a
profile manager. When i used the default user and said finish, I got
the following error. Not sure why. I was able to run the create
profile as a root though. But then when try to run it as a normal user
after creating profile as a root, it would start the profile manager
again.

 Profile couldn't be created. Probably the chosen folder isn't
writable.
[Exception... "Component returned failure code: 0x80520015
(NS_ERROR_FILE_ACCESS_DENIED)
[nsIToolkitProfileService.createProfile]"  nsresult: "0x80520015
(NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame ::
chrome://mozapps/content/profile/createProfileWizard.js :: onFinish ::
line 233"  data: no]

Regards,
Vishwa

---

### Post by ukripper on 2009-11-18
Because normal user can't write to /opt without permissions.

can you run this command and post output:
```
cat /opt
```

---

### Post by dagarshali on 2009-11-18
dagarshali@olivegarden:/home$ cat /opt
cat: /opt: Is a directory


this is all i get..

dagarshali@olivegarden:/home$ ls -la /opt
total 36
drwxr-xr-x  9 root       root       4096 2009-11-18 09:51 .
drwxr-xr-x 22 root       root       4096 2009-11-02 12:18 ..
drwxr-xr-x  3 root       root       4096 2009-09-08 20:24 cisco
drwxr-xr-x 14 root       root       4096 2009-11-11 14:06 firefox
drwxr-xr-x  2 root       root       4096 2009-09-22 13:18 matlab
drwxr-xr-x  3 root       root       4096 2009-08-28 13:14 real
drwxr-xr-x  6 dagarshali dagarshali 4096 2008-12-17 07:59 SALOME-MECA-2009.1-GPL
drwxr-xr-x 14 root       root       4096 2009-08-24 13:59 tecplot
drwxr-xr-x 12 dagarshali dagarshali 4096 2009-09-15 20:47 thunderbird


Regards,
Vishwa

---

### Post by ukripper on 2009-11-18
Sorry i meant ls -al before. my mistake

can you run this command:
```
ls -al /opt/thunderbird
```

---

### Post by dagarshali on 2009-11-18
Hi here it is..


dagarshali@olivegarden:/home$ ls -al /opt/thunderbird
total 17900
drwxr-xr-x 12 dagarshali dagarshali     4096 2009-09-15 20:47 .
drwxr-xr-x  9 root       root           4096 2009-11-18 09:51 ..
-rw-r--r--  1 dagarshali dagarshali     2109 2009-09-15 20:44 application.ini
drwxr-xr-x  3 dagarshali dagarshali     4096 2009-09-15 20:47 chrome
drwxr-xr-x  2 dagarshali dagarshali    12288 2009-11-18 09:51 components
-rwxr-xr-x  1 dagarshali dagarshali    45760 2009-09-15 20:47 crashreporter
-rw-r--r--  1 dagarshali dagarshali     3801 2009-09-15 20:03 crashreporter.ini
drwxr-xr-x  6 dagarshali dagarshali     4096 2009-09-15 20:44 defaults
-rw-r--r--  1 dagarshali dagarshali       52 2009-09-15 20:07 dependentlibs.list
drwxr-xr-x  2 dagarshali dagarshali     4096 2009-09-15 20:47 dictionaries
drwxr-xr-x  3 dagarshali dagarshali     4096 2009-09-15 20:42 extensions
drwxr-xr-x  2 dagarshali dagarshali     4096 2009-09-15 20:34 greprefs
drwxr-xr-x  2 dagarshali dagarshali     4096 2009-09-15 20:34 icons
drwxr-xr-x  3 dagarshali dagarshali     4096 2009-09-15 20:47 isp
-rw-r--r--  1 dagarshali dagarshali      478 2009-09-15 20:47 libfreebl3.chk
-rwxr-xr-x  1 dagarshali dagarshali   317036 2009-09-15 20:47 libfreebl3.so
-rwxr-xr-x  1 dagarshali dagarshali   188880 2009-09-15 20:47 libldap60.so
-rwxr-xr-x  1 dagarshali dagarshali     8076 2009-09-15 20:47 libldif60.so
-rwxr-xr-x  1 dagarshali dagarshali   839368 2009-09-15 20:47 libmozjs.so
-rwxr-xr-x  1 dagarshali dagarshali   200736 2009-09-15 20:47 libnspr4.so
-rwxr-xr-x  1 dagarshali dagarshali   858792 2009-09-15 20:47 libnss3.so
-rwxr-xr-x  1 dagarshali dagarshali   338140 2009-09-15 20:47 libnssckbi.so
-rwxr-xr-x  1 dagarshali dagarshali   122896 2009-09-15 20:47 libnssdbm3.so
-rwxr-xr-x  1 dagarshali dagarshali    77608 2009-09-15 20:47 libnssutil3.so
-rwxr-xr-x  1 dagarshali dagarshali    13180 2009-09-15 20:47 libplc4.so
-rwxr-xr-x  1 dagarshali dagarshali     8748 2009-09-15 20:47 libplds4.so
-rwxr-xr-x  1 dagarshali dagarshali    16688 2009-09-15 20:47 libprldap60.so
-rwxr-xr-x  1 dagarshali dagarshali   125644 2009-09-15 20:47 libsmime3.so
-rw-r--r--  1 dagarshali dagarshali      478 2009-09-15 20:47 libsoftokn3.chk
-rwxr-xr-x  1 dagarshali dagarshali   190032 2009-09-15 20:47 libsoftokn3.so
-rwxr-xr-x  1 dagarshali dagarshali   449784 2009-09-15 20:47 libsqlite3.so
-rwxr-xr-x  1 dagarshali dagarshali   160140 2009-09-15 20:47 libssl3.so
-rwxr-xr-x  1 dagarshali dagarshali   550316 2009-09-15 20:47 libxpcom_core.so
-rwxr-xr-x  1 dagarshali dagarshali    12192 2009-09-15 20:47 libxpcom.so
-rw-r--r--  1 dagarshali dagarshali   131352 2009-09-15 20:42 license.html
-rw-r--r--  1 dagarshali dagarshali     6434 2009-09-15 20:00 LICENSE.txt
drwxr-xr-x  4 dagarshali dagarshali     4096 2009-09-15 20:47 modules
-rwxr-xr-x  1 dagarshali dagarshali    10368 2009-09-15 20:47 mozilla-xremote-client
-rw-r--r--  1 dagarshali dagarshali      139 2009-09-15 20:34 platform.ini
-rw-r--r--  1 dagarshali dagarshali      183 2009-09-15 20:00 README.txt
-rw-r--r--  1 dagarshali dagarshali     6734 2009-09-15 20:46 removed-files
drwxr-xr-x  6 dagarshali dagarshali     4096 2009-09-15 20:28 res
-rwxr-xr-x  1 dagarshali dagarshali    10450 2009-09-15 20:03 run-mozilla.sh
-rw-r--r--  1 dagarshali dagarshali      825 2009-09-15 20:03 Throbber-small.gif
-rwxr-xr-x  1 dagarshali dagarshali     3891 2009-09-15 20:42 thunderbird
-rwxr-xr-x  1 dagarshali dagarshali 13329140 2009-09-15 20:47 thunderbird-bin
-rw-r--r--  1 dagarshali dagarshali        6 2009-09-15 20:34 update.locale
-rwxr-xr-x  1 dagarshali dagarshali    67348 2009-09-15 20:47 updater
-rw-r--r--  1 dagarshali dagarshali      151 2009-09-15 20:42 updater.ini

---

### Post by ukripper on 2009-11-18
can you run this command and try to create profile again:
```
sudo chown -R **yourusername:yourusername** /opt/thunderbird
```

replace **yourusername** with your username you are using.

---

### Post by dagarshali on 2009-11-18
Hi,
As is see in the ls -la of /opt/thunderbird, i am the owner.

Nevertheless, i did try to change the ownershipt again and i get the exact same error..

Cheers,
Vishwa

---

