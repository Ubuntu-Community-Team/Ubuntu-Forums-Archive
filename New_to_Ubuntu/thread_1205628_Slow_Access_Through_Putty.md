---
title: "Slow Access Through Putty"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by age99 on 2009-07-06
I am trying to access an Ubuntu machine through Putty installed on a Windows Vista laptop.  The access is incredibly slow.  Both machines are very fast.  
Any graphic or even text (gedit) file is barely usable because they take up to 1 minute to load despite being very small files (< 100kb).  I've accessed the same machine locally through Putty and it is very fast but once I am remote, it is very, very slow.  
If I try to download the same files through winscp421 or other programs, they transfer in 1 or 2 seconds.

From what I understand, Putty is using ssh to access the remote machine. Is this correct?  Are there any ways to improve this speed?

Are there other options for doing this that might be faster?

---

### Post by wojox on 2009-07-06
It's been awhile since I puttied around on windows, but I think it defaults to ssh. Under remote ip and port should be some option buttons. See if ssh is selected.

When you're remote are you on a wireless laptop?

Is your ubuntu box behind a router?

---

### Post by age99 on 2009-07-06
SSH is selected.  X11 forwarding is also selected.

I'm on a wireless laptop, both remotely and locally.  

The Ubuntu machine I'm accessing is behind a router.  If the router was the problem, wouldn't it also slow down speeds when I am transferring files through other programs?

Thanks

---

### Post by wojox on 2009-07-06
You've transferred files through other apps remotely?

---

### Post by age99 on 2009-07-06
Yes, I used WinSCP and it transfers the files very quickly.

---

### Post by XCan on 2009-07-06
Have you tried to enable compression in Connection -> SSH?

---

### Post by age99 on 2009-07-07
I tried the compression, and while there is a slight improvement, a 875kb file still takes about 1 minute to load through putty in a viewer but only about 8 seconds to download the entire file.
To bring something up and edit in gedit is painful.

---

