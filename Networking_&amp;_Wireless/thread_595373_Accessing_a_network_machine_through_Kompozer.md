---
title: "Accessing a network machine through Kompozer"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by suzyweb on 2007-10-28
Hello,

Thanks so much for this forum and for your help!

I can't seem to set up a web site on my sister's computer through Kompozer. I have tried creating a SMB, but Kompozer can't see it. I found some instructions on Mounting smbfs Shares Permanently here:

[http://ubuntuforums.org/showthread.php?t=255872&highlight=Permanently+mount+samba+share](http://ubuntuforums.org/showthread.php?t=255872&highlight=Permanently+mount+samba+share)

Is this what I need to do? If so how to I find out the sharename? 

Thanks so much!

Suzy

---

### Post by suzyweb on 2007-10-29
bump... thanks again for your help!

---

### Post by wolfsta on 2007-10-29
Hi Suzy

Did you try just mounting the share manually from that guide?

> smbmount //windowscomp/share /mnt/dir -o username=suzy

Was it successful?  Or is it just from within kompozer you cannot access the smb mounted dirs?

---

### Post by suzyweb on 2007-10-29
hello! Thanks for your reply. It's just from Kompozer that I can't access the smb.

---

### Post by wolfsta on 2007-10-29
If you are running Kompozer under the same user account that you mounted the smb shares with then you shouldnt have any issues.  I have never used Kompozer before but I'm guessing your just trying to open files from it?

Does it give an access denied error or something?  You said Kompozer can't see it can you please explain this a little more?  Where abouts did you mount the smb share to?

---

