---
title: "error in extracting .tar.gz file"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by phanipalagummi on 2009-01-28
I just downloaded a .tar.gz file which when extracting i got an error 

please see this picture

---

### Post by emarkd on 2009-01-28
Looks like a bad archive, or maybe an incomplete download.  I'd try downloading it again.

---

### Post by phanipalagummi on 2009-01-28
i tried upgrading,re-installing it but i found the same error.

---

### Post by emarkd on 2009-01-28
What do you mean by "upgrading" or "reinstalling" it?  It looks like a corrupt tarball.  I'm assuming you downloaded the file from some internet source.  If the website provides an md5sum for the file, you can use that to verify the file you've already downloaded.  We can help with that if you don't know how.  If not, I'd suggest trying to download it again.

---

### Post by taurus on 2009-01-28
The error has nothing to do with upgrading or reinstalling Ubuntu.  It has everything to do with how you downloaded that file, whatever that is.  If you download it from a terminal, make sure you use the binary mode.  If you download it with firefox, make sure it can handle a large download because sometimes the network chokes on a large download.

---

### Post by phanipalagummi on 2009-01-28
Ok,as you said i installed the .tar.gz file again ,and unfortunately it was the same error the .tar.gz file is the samsung scx-4100 linux drivers
(UnifiedLinuxDrivers.tar.gz)

---

### Post by phanipalagummi on 2009-01-28
and the updating and re-installing was ment on archive manager software.
Which done through synaptic

---

### Post by igknighted on 2009-01-28
> **phanipalagummi said:**
> Ok,as you said i installed the .tar.gz file again ,and unfortunately it was the same error the .tar.gz file is the samsung scx-4100 linux drivers
(UnifiedLinuxDrivers.tar.gz)

1) I bet that driver is already included, you probably don't need to install it.

2) If not, contact samsung and tell them the archive is corrupted.

---

### Post by mc4man on 2009-01-28
You need to extract from the terminal and then I'd assume follow the intrsuctions on website. Will extact to a cdroot folder.

ex. put in home folder

> doug@doug-desktop:~$  tar xzf UnifiedLinuxDriver.tar.gz

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

