---
title: "put password on zip files"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Falc7 on 2009-10-29
Hi
I want to know how to set up a password on a zip file in ubuntu, once everything is set up it has to be easy to do (no terminal).
I've tried the normal method, right click file-> compress-> zip -> add password, but it gives me an error message.

I am aware zip password isen't very secure, i'm not too bothered about that really though, however if someone else knows another method, that is easy to do for a beginner, that would be fine too :)

---

### Post by lavinog on 2009-10-29
what is the error message you received?

Are you using ubuntu 9.10 or 9.04?
the method you used worked for me.

---

### Post by Falc7 on 2009-10-29
Using ubuntu 9.10

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_GB.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)
Scanning

Creating archive /home/jamie/Desktop/Untitled HTML 1.html.zip



System error:
E_INVALIDARG

---

### Post by lavinog on 2009-10-29
> **Falc7 said:**
> Using ubuntu 9.10

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_GB.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)
Scanning

Creating archive /home/jamie/Desktop/Untitled HTML 1.html.zip



System error:
E_INVALIDARG

looks like you found a filename bug.

replace the spaces in the filename with underscores or put the file in a folder then archive it.

---

### Post by Shpongle on 2009-10-29
if you want real security try an app called truecrypt

see here [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

---

### Post by Wiebelhaus on 2009-10-29
> **dillbyrne said:**
> if you want real security try an app called truecrypt

see here [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

+1

---

### Post by lavinog on 2009-10-29
> **Falc7 said:**
> 
I am aware zip password isen't very secure, i'm not too bothered about that really though, however if someone else knows another method, that is easy to do for a beginner, that would be fine too :)
I am pretty sure encrypted 7z files are pretty secure as long as a good password is used.

---

### Post by Falc7 on 2009-10-29
> **lavinog said:**
> looks like you found a filename bug.

replace the spaces in the filename with underscores or put the file in a folder then archive it.

I get the same error no matter the file name:

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_GB.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)
Scanning

Creating archive /home/jamie/Desktop/plans.odt.zip



System error:
E_INVALIDARG                


> **DillByrne said:**
> if you want real security try an app called truecrypt

see here [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)


Okay, i'll give this a try, i've installed it, how do i go about getting a password? There seem to be a lot of options to mount the file. The reason i want to put a password on a file is that my mum wants to send semi-confidential files in a folder by email, and she wants to put a password on this file to deter just anyone being able to open it, is true crypt suitable for this?

---

### Post by lavinog on 2009-10-30
found this:
[http://ubuntuforums.org/showthread.php?t=1078714](http://ubuntuforums.org/showthread.php?t=1078714)
try removing p7zip-rar

---

### Post by lavinog on 2009-10-30
ok I figured this out, and I will file the bug report.
When you use rightclick>compress>zip and enable encryption, after entering a password is the "encrypt file list too" checked?  if so is it greyed out so you can't uncheck it?  if so switch the file type to 7z, uncheck "encrypt file list too", then press cancel (for some reason the change doesn't take effect until you restart the app. Now try and compress with encryption as a zip...it should work now.
The problem is that zip cannot encrypt the file list, but file-roller (the gui compression program) remembers the last setting used for any file type.

Edit: another way to fix this is:
```

gconftool-2 --type bool --set /apps/file-roller/general/encrypt_header false

```

bug report: [https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/464324](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/464324)

---

### Post by Falc7 on 2009-10-30
> **lavinog said:**
> ok I figured this out, and I will file the bug report.
When you use rightclick>compress>zip and enable encryption, after entering a password is the "encrypt file list too" checked?  if so is it greyed out so you can't uncheck it?  if so switch the file type to 7z, uncheck "encrypt file list too", then press cancel (for some reason the change doesn't take effect until you restart the app. Now try and compress with encryption as a zip...it should work now.
The problem is that zip cannot encrypt the file list, but file-roller (the gui compression program) remembers the last setting used for any file type.

Edit: another way to fix this is:
```

gconftool-2 --type bool --set /apps/file-roller/general/encrypt_header false

```

bug report: [https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/464324](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/464324)

Thats it! thanks :)

---

