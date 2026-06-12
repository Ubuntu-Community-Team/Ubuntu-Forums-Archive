---
title: "Moving files on the NAS"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by pjones0404 on 2011-01-14
I have a question about moving files around on my NAS. I want to move some large files from one directory on the NAS to another. When i access these files via nautilus and try to cut and paste them it tries to move them over the network. How can i just move them without transferring the file over the network?

For example, I am moving an .iso from one folder to another. When i do this, it moves the file to my computer and then back to the NAS. It takes a really long time to transfer and slows down my network. Is there anyway to do this without sending the file to my laptop. 

Hope this makes sense.

---

### Post by papibe on 2011-01-14
What kind of NAS are you using? 
Does it have a admin or config tool?
Can you ssh to it?

Regards.

---

### Post by pjones0404 on 2011-01-14
It is a linksys NMH-305. It has a web interface that has a file browser. It does not have SSH but does have FTP access. When i use the web interface, flash based, I am able to move files around without sending them over the network. I am hoping to do this outside of this interface as it is rather clunky to say the least.

---

### Post by papibe on 2011-01-14
It all will depend in the "intelligence" behind your NAS. I guess is using smb. In the case of samba shares from an Ubuntu server, I know for sure that works moving the files "internally" (if the files are in the same partitions of course).

Does your NAS also supports nfs?

Regards.

---

