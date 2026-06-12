---
title: "Sharing a single directory over the Internet"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by poguemahone on 2008-06-18
I would like to share a single directory on my Ubuntu host with my brother (over the Internet). The directory has about 60 GB of data, so this isn't a situation where I can upload my data to some other server for him to download. He will be accessing the share from a Windows computer. He will only need read access.

What do you think the best way to do this is?  It sounds like there is a way to do it with sFTP (which I already use), but I don't really want him to be able to traverse the entire filesystem.  FTP sounds like a security risk. 

Any ideas?

---

### Post by Kebabman on 2008-06-18
You could set him up with a user account on your machine with a symlink in his home directory to the directory in question. Then allow him to access it via ssh. With this done he should be able to use a program like [sftpdrive]("http://www.sftpdrive.com/") to access his home directory and hence the shared directory via the symlink.

---

### Post by poguemahone on 2008-06-18
> **Kebabman said:**
> You could set him up with a user account on your machine with a symlink in his home directory to the directory in question. Then allow him to access it via ssh. With this done he should be able to use a program like [sftpdrive]("http://www.sftpdrive.com/") to access his home directory and hence the shared directory via the symlink.

This would certainly allow him to access the directory. However, I believe he would still be able to traverse the rest of the filesystem, no?

---

### Post by Kebabman on 2008-06-18
Yes it would. However you could use chroot to restrict the user to their home directory. There is a tutorial [here]("https://calomel.org/sftp_chroot.html") that I think might help you achieve what you want.

Hope this helps

---

### Post by poguemahone on 2008-06-18
I have heard of this method (sftp "jail"). It seems a bit complex and I was hoping that there was another method that I haven't stumbled across yet.

If I was going to use this method, could I still use sftp to browse the entire filesystem while resticting my brother to his home directory?  If I made a symlink to the directory I want to share, will the "jail" not prevent him from accessing it?

---

### Post by Kebabman on 2008-06-18
As you would log in using your username you should be able to browse the whole file system fine. Regarding him accessing the symlinked directory this should be ok as long as you set up the permissions correctly.

Granted this is not a simple solution but it is the only one that comes to mind. This is not to say there is a simpler one that I am overlooking as it is 1am :)

---

