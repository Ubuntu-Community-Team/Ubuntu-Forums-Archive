---
title: "where's the Windows driive"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by strmk1ng on 2009-03-14
I was able to successfully to install Ubuntu on my 320 gig drive however it didn't give me a prompt to create a swap drive. The result of this is that I can't bring stuff over my Windows drive. The drive is seen in Places but I get the error message "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." Can anyone tell me how to create this swap in simple terms. Thanks

---

### Post by taurus on 2009-03-14
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Miljet on 2009-03-14
I think you may have a misconception of swap space. The swap partition in Linux, and swap file in Microsoft, is disk space for the operating system to use as temporary memory when the RAM gets too full. It has absolutely nothing to do with the ability to move files.

---

### Post by strmk1ng on 2009-03-14
Hmm well thanks for educating me. Do I really need this if I'm running 4 gigs of ram? Command output coming right up.

---

### Post by billgoldberg on 2009-03-14
> **strmk1ng said:**
> Hmm well thanks for educating me. Do I really need this if I'm running 4 gigs of ram? Command output coming right up.

No.

Swap is pretty much obsolete now because ram is so cheap.

It's only on low-end machines 1g or less that it's needed.

--

To answer your question, people have problems accessing their Windows partition from Ubuntu when they didn't close down Windows properly.

---

### Post by strmk1ng on 2009-03-14
That must have been the case because when I restarted I was able to get in just fine.

---

