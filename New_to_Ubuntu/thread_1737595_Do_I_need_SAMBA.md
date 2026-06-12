---
title: "Do I need SAMBA?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by xpatrick on 2011-04-23
Everything I read about sharing folders across networks including using Samba deal with windows/linux networks - If you have a network made up of only Linux machines can folders/drives be shared without Samba or any additional tools/apps

Thanks

---

### Post by el_koraco on 2011-04-23
Yes, but you need to set up a different server and client configuration, like NFS or FTP.

---

### Post by xpatrick on 2011-04-23
thanks - and is using nfs a better option than samba?

---

### Post by Morbius1 on 2011-04-23
That's a loaded question :D

I'm not going to get involved in the debate on that one but I would like to point out that in a normal home network NFS and Samba are not in the same category as samba is a browseable protocol and NFS is not ( the last time I checked - I'll admit it has been a while ). You have to know where the share is with NFS.

---

### Post by el_koraco on 2011-04-23
As with everything, it comes down to personal preferences and experiences. Samba has the built-in graphical tools for accessing the network folders from Nautilus, so it might be easier from the get go. Personally, I find NFS to be faster, but there is some additional setting up to do.

---

### Post by PhillyPhil on 2011-04-23
Samba will work fine.  Here's a simple samba howto: [http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)

---

