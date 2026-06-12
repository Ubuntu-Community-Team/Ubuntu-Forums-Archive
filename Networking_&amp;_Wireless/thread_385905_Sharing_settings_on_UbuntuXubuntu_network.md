---
title: "Sharing settings on Ubuntu/Xubuntu network"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by AdamWarlock on 2007-03-16
Hey all.

I was wondering if someone might be able to give me a simple walkthrough as to how I could setup a network between an Ubuntu and a Xubuntu [both Edgy] box so that if someone logged into either machine, they would be able to retrieve their Thunderbird [used for newsgroups and email] and Swiftfox settings?

I am able to set up a shared folder on the Ubuntu box and mount it on the Xubuntu box for sharing downloaded files with no problem. If anyone can help me, I would really appreciate it.

Thanks,
Corey

---

### Post by AdamWarlock on 2007-03-18
BUMP

Please help me.

---

### Post by barney_1 on 2007-03-18
Well, here's how I would do it:

1) Have one machine house the settings files.  Setup a network share for that directory on that machine, I would use NFS rather than samba.  Set up the remote computer to mount this NFS share to a directory at boot-time: 
[http://www.ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://www.ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

2) On the remote computer, find and delete your configuration files for Thunderbird, etc.  Replace those deleted files with symbolic links to the files you have mounted over the NFS share.

Info about those configuration files: [http://www.mozilla.org/support/thunderbird/edit](http://www.mozilla.org/support/thunderbird/edit)

Info about linking files (make sure you don't use -s, this should be a hard link):
In terminal:
```
man ln
```

---

