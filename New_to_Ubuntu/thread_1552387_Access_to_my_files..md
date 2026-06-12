---
title: "Access to my files."
date: 2010-08-13
forum: New to Ubuntu
---

### Post by adam_himself on 2010-08-13
Hello everyone!  Sorry if this may come off as a newb question or a bad idea (tell me if so!) but I am having trouble accessing some files on my E: drive.  Here's the breakdown:

I installed from Windows 7.  
I made a partition from my HD for Windows on the C: drive 
and made a 2nd partition for all file storage (E:/).  


I had always heard about Linux, but saw a friend at work using Debian and I was hooked after that... I used Wubi to install a 17GB Ubuntu install on my E:.  I found my C: listed as "105 GB filesystem" but I seem unable to access my E drive.  I had basic files like music and videos there (E:\music\) and such.  I installed Ubuntu directly to E:.  When I am in Windows its listed as "E:\ubuntu" if that means anything (root?)

I have tried my hardest to find a way to get to my music.  I can't seem to find a way.

Help?  Thanks.

---

### Post by philinux on 2010-08-13
From the wubi faq's.


> Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.


---

### Post by adam_himself on 2010-08-13
> **philinux said:**
> From the wubi faq's.

Thanks a ton.  Found it in /host/ .  For some reason it wasn't showing up on search or file/folder find for me...

---

