---
title: "Unable to copy files from a Windows SMB share"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by simonjbale on 2006-11-09
Hi,

I am unable to copy files from a windows SMB share that I access through Places->Connect to Server. If I try to drag a file from the share to my desktop I receive the message "Error "Not a directory" while copying."   The same error occurs if I double click on the file. I am also unable to create any new files or directories although no error is displayed in this case.

Any help is greatly appreciated, I'm using Ubuntu 6.10.

Best Wishes, Simon Bale.

---

### Post by dannyboy79 on 2006-11-09
have to tried to instead of dragging to your desktop, tried right clicking and saying copy and then pasting it some place other than your desktop? just a thought, well if you're trying to double click on a file through nautilus, what kind of a file is it, also, just because you can connect to the share doesn't mean you have read write permissions. are you using winxp with simple file sharing turned OFF? then under security, you add the same username that's on your ubuntu box as a person that hsould have read write access to the shaer? other than that I not sure what to tell ya there but you could try it another way, install smbfs first, sudo aptitude install smbfs, then mount the windows share into a folder you create on your ubuntu computer. make sure the folder you create is owned by you with read write permissions. use you this link to show you how to mount windows shares onto your ubuntu box: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

good luck

---

### Post by Antman on 2006-11-13
> **simonjbale said:**
> Hi,

I am unable to copy files from a windows SMB share that I access through Places->Connect to Server. If I try to drag a file from the share to my desktop I receive the message "Error "Not a directory" while copying."   The same error occurs if I double click on the file. I am also unable to create any new files or directories although no error is displayed in this case.

Any help is greatly appreciated, I'm using Ubuntu 6.10.

Best Wishes, Simon Bale.

Yeah, I have this issue too. I recall that there was a quick fix for it, but I forgot what it is.. lol... as soon as I find it I'll post.

---

### Post by mogul on 2006-11-20
> **Antman said:**
> Yeah, I have this issue too. I recall that there was a quick fix for it, but I forgot what it is.. lol... as soon as I find it I'll post.

I don't suppose you found it?  Google's unhelpful and I'm running into the same issue.  TIA

---

