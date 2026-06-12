---
title: "FsUsbEx..."
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Prof4Jesus on 2009-12-21
I have had an error message pop up and have no clue what it relates to.  Any insight would be appreciated!  The message reads, "Failed FsUsbExService, No existing FsUsbExDevise."

---

### Post by oldos2er on 2009-12-21
Which version of Ubuntu are you running?

---

### Post by Prof4Jesus on 2009-12-21
'm using Ubuntu 9.04.

---

### Post by vene-ubu on 2010-11-09
I can see that this is a very old Post.  Hope my answer helps someone else :)
I am using Ubuntu 9.04 too with Wine 1.0.1:

I got this error after I Installed Samsmung's New PC Studio.  Which I downloaded from a non-official website. After next Wine application start the problem appeared.

It is being caused by the file "C:Windows\System32\FsUsbExService.ex" is being executed gives this error.

I read around that this may be a virus.  I just tried reinstalling Wine and truly this software is not there on the original install. 

To solve it you can delete such file, or better what I did was edited the registry entry:
- HKEY_LOCAL_MACHINE/System/Services/Eventlog/FsUsbExservice/ImagePath, 
And cleared the entry.

(The registry editor in Wine can be opened browsing C drive on applications->Wine, Windows/regedit.exe.)

---

