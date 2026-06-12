---
title: "unable to get exclusive lock"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by hduguay on 2010-06-04
I tried installing java from the synaptic package manager and have run into a problem. Now when I try to run the update manager I get an error saying unable to get exclusive lock. any help with this would be greatly appreciated .

---

### Post by howefield on 2010-06-04
Do you have any other package managers running ?

You may only run one at a time, whether that be synaptic, add remove, update manager, ect ect.

---

### Post by telewatho on 2010-06-04
As you may know, the package installation programs all "lock" a directory so that only one of them can modify the package database at once. :-)

One thing to try is to make sure there are no other programs like "synaptic" or "apt-get" or "software center" running at the same time.

If none of these processes are running, there could be something else going on. Check you're running synaptic as the root user.

---

### Post by hduguay on 2010-06-04
No I dont have any other packages running. I initially tried to install java from the spm, it wouldnt load, so i closed off and now when i try to open the update manager it gives this error. Also if I try to do upadtes via terminal I get error E: unable to lock administration directory  ( var/lib/dpkg), is another process using it? Not sure what to do to rectify this

---

### Post by sandyd on 2010-06-04
> **hduguay said:**
> No I dont have any other packages running. I initially tried to install java from the spm, it wouldnt load, so i closed off and now when i try to open the update manager it gives this error. Also if I try to do upadtes via terminal I get error E: unable to lock administration directory  ( var/lib/dpkg), is another process using it? Not sure what to do to rectify this

restart

---

### Post by sgosnell on 2010-06-04
It's also possible for the lock file to not be removed from the directory.  If the program which placed the lock file is interrupted it may not remove it, and sometimes the removal doesn't happen for other reasons.  Sometimes it's necessary to manually remove a lock file.

---

### Post by hduguay on 2010-06-04
How do I unlock these files? And also how do I make sure I am doing these updates as root user aside from making sure I unlock the root option under user groups ?

---

### Post by hduguay on 2010-06-04
So how do I manually remove a locked file ?

---

### Post by bruno9779 on 2010-06-04
did you try to reboot as suggested?

---

### Post by hduguay on 2010-06-04
When I try to run updates through terminal it gives message 
          **Bug Description**

   
   Binary package hint: sun-java6-doc
 This is also a problem with the java5 version of this package
 Trying to install these packages produces a message:
 Setting up sun-java6-doc (6-00-2ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:
     jdk-6-doc.zip jdk-6-doc-ja.zip
 (choose the non-update version if this is the first installation).
Please visit
     [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)
 now and download.  The file should be owned by root.root and be copied
to /tmp.
 [Press RETURN to try again, 'no' + RETURN to abort]




which from my understanding is a known bug,this is stopping my from getting my updates. How do I get around this error ?

---

### Post by hduguay on 2010-06-04
I rebooted a few times to no avail.

---

### Post by bruno9779 on 2010-06-04
If reboot does not work, try:

```

sudo dpkg --configure -a
```

If even this doesn't work, only then try and remove the lock manually.

```
sudo rm /var/lib/dpkg/lock 
sudo rm /var/cache/apt/archives/lock
```

NB: make double sure that you have no dpkg or apt-* processes running before doing this

---

### Post by bruno9779 on 2010-06-04
I have just read your error message posting, and I recall having a similar issue when trying to install java by building it and making .deb files.

you may need to:

```
sudo dpkg -r sun-java6*
```

install java 6 by doing:

```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version
```

---

### Post by sgosnell on 2010-06-04
> So how do I manually remove a locked file ? 
It's technically a lock file, not a locked file.  It's a zero-byte file written to a directory by a program which needs to lock a process so that no other programs can run it.  Lock files are normally named 'lock'.  For the file you mentioned, ```
sudo rm var/lib/dpkg/lock
``` should do it.  Just make sure nothing else is running.  Update manager, aptitude, apt-get, Synaptic, dpkg, and some others all set locks, because they're all doing essentially the same thing, and none should be running simultaneously.

---

### Post by robertmf on 2012-08-31
> **sgosnell said:**
> It's technically a lock file, not a locked file.  It's a zero-byte file written to a directory by a program which needs to lock a process so that no other programs can run it.  Lock files are normally named 'lock'.  For the file you mentioned, ```
sudo rm var/lib/dpkg/lock
``` should do it.  Just make sure nothing else is running.  Update manager, aptitude, apt-get, Synaptic, dpkg, and some others all set locks, because they're all doing essentially the same thing, and none should be running simultaneously.
[COLOR="DarkRed"]
):P Thanks :D
[/COLOR]

---

