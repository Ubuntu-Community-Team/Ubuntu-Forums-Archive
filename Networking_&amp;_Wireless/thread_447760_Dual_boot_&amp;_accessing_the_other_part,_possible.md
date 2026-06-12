---
title: "Dual boot &amp; accessing the other part, possible?"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by gmalac on 2007-05-18
Hello,

Sorry if this is a stupid question but I have installed Ubuntu on a Vista PC that now has the two options at startup. The rest of the family is on Vista while I use Ubuntu.  
The PC has a second drive with all the shared folders (music, video, images) that can be accessed when booting in Vista, not when booting in Ubuntu.
What I'd like to achieve is accessing these folders from within Ubuntu so I don't have to have these files in double on the same PC.
But can't see them from Ubuntu while with Samba I see the shares in the other PC on my home network. 
Is this normal? Or is there a way to access these folders?

Thanks for any help

Guy

---

### Post by newlinux on 2007-05-18
You probably just need to mount the partition you want to use on the second hard drive.  I assume it is an NTFS partition? Linux doesn't natively write to NTFS but it can read from NTFS partition. And there is a driver to allow it to write to NTFS partitions. 


Perhaps one of these links will help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by gmalac on 2007-05-20
Thank you very much for your help, I went with the second option and installed ntfs-config.
This works great and gave me full rw access to the vista part of the PC. Exactly what I was looking for!
Thanks again
Guy

---

### Post by newlinux on 2007-05-20
Glad it worked! happy ubuntuing!

---

