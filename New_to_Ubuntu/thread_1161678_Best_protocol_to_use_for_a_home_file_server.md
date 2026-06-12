---
title: "Best protocol to use for a home file server?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-05-16
Hi!  I have been playing around with an older computer that I have set up as a server.  However, I am not sure what protocol to use for file sharing.  I have been using samba because it is so easy to configure and use, but it is kind of slow and I only have Linux clients.  I have been considering FTP, but I am worried about securing it.  What other options are there?  What would be ideal?  What do you use on your own network?

Thanks in advance!

---

### Post by bodhi.zazen on 2009-05-16
If you are behind a firewall, ftp is fine (IMO).

If you are wanting to share over the internet, ssh (sshfs) FTW :)

---

### Post by chrisod on 2009-05-17
I found NFS to be a lot faster that Samba.

---

### Post by mapes12 on 2009-05-17
If you only have Linux boxes then have a look at this thread. It worked for me: [http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308)

---

