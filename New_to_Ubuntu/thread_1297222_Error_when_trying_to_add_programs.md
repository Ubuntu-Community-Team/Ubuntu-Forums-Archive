---
title: "Error when trying to add programs"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by redjess on 2009-10-21
Hi

Had this problem for a few days and thought I had fixed it but clearly not. Whn trying to do anything with the package manager this error message pops up.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What can I do to fix this?

Please let me know in really simple terms - im very new to this DIY computer malarky.

Thanks

Redjess

---

### Post by oldos2er on 2009-10-21
Open a terminal (Applications, Accessories, Terminal), and run
```
sudo dpkg --configure -a
```

---

### Post by Warpnow on 2009-10-21
> **redjess said:**
> Hi

Had this problem for a few days and thought I had fixed it but clearly not. Whn trying to do anything with the package manager this error message pops up.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What can I do to fix this?

Please let me know in really simple terms - im very new to this DIY computer malarky.

Thanks

Redjess

Its telling you to enter the command that might fix it. Open a terminal and type

sudo dpkg --configure -a

If there is an error message from that, post it here.

---

### Post by redjess on 2009-10-21
I typed that in and got this...

Setting up sun-java6-doc (6-14-0ubuntu1.8.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


 I had this message before and tried to download it but it didn't work - i'm beginning to think im in a catch 22!

---

### Post by wojox on 2009-10-21
Do you have Sun Java(TM) Development Kit (JDK) 6 installed?

Need that for sun-java6-doc (The JDK(TM) is a development environment for building applications, applets, and components using the Java programming language.)

---

### Post by redjess on 2009-10-28
Thank you for replying, sorry for taking so long to get back to you.

I tried to check whether or not I had Sun Java(TM) Development Kit (JDK) 6 installed on Synaptic Package Manager but when I opened it I got the original error message...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Is there another way to find out if I have this program installed?

---

