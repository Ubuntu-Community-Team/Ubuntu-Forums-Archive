---
title: "External hard drive - use by both Ubuntu and Windows, and share using samba questions"
date: 2021-02-05
forum: Networking &amp; Wireless
---

### Post by uacnt83982803 on 2021-02-05
I recently obtained a large external drive that I will use for backing up of my critical data (separately from cloud backups).

I formatted the drive using FAT and my plan is to encrypt it using VeraCrypt.  That way I can read/write from both my Ubuntu and Windows PCs (when directly plugged in).

Question #1, should I encrypt the entire partition in VeraCrypt or create a very large encrypted volume?

Second, it would be nice if I could access this drive across my network via a share (leaving it plugged into my Ubuntu machine, using the share to access it from Windows and hopefully my phone).  Right up front I'll state that I'm not knowledgeable on creating shares in Ubuntu so I'll need help with that.

Question #2, is what I'd ideally like to do (above) doable with a share, considering that I'm sharing a drive encrypted with Veracrypt?  This circles back to Question #1, since I assume one method would make it easier to share than the other?  Maybe not.

Appreciate any input!  Thanks.

---

### Post by CelticWarrior on 2021-02-05
Let me start by pointing out that when the contents of an encrypted file or partition are accessible that means, obviously, that said drive has been decrypted, at which point the question is moot.

Thin about why do you want encryption... Is it to have the data inaccessible when the external drive isn't in use, during transport from A to B, due to fear of it being stolen? Or eventually snatched by someone with access to its current location? 
Do you understand that encryption doesn't provide any protection if already decrypted and in use from anyone having physical access to the computer?

---

### Post by uacnt83982803 on 2021-02-05
Yes, I understand that once decrypted it's open to whoever happens to have it.  I would only decrypt it when I need to access it either by the local Ubuntu PC it's plugged into, or the other devices at home (for example, I do my taxes on the Windows PC and want to archive the data to the external drive.  Or I am doing a periodic photo upload from my phone).  I should have clarified that.  My main concern for encrypting it is, as you suggest, to protect the drive should it be stolen.

---

### Post by CelticWarrior on 2021-02-05
Right...

Here's an intro: [https://security.stackexchange.com/questions/178782/differences-between-using-an-encrypted-container-and-encrypting-a-partition](https://security.stackexchange.com/questions/178782/differences-between-using-an-encrypted-container-and-encrypting-a-partition)
and some discussion: [https://www.wilderssecurity.com/threads/encrypt-full-external-hdd-or-container-or-partition-with-veracrypt.372875/](https://www.wilderssecurity.com/threads/encrypt-full-external-hdd-or-container-or-partition-with-veracrypt.372875/)

A visual aid for encryption a partition: [https://www.youtube.com/watch?v=FwhdzjP4EKQ](https://www.youtube.com/watch?v=FwhdzjP4EKQ)

---

### Post by uacnt83982803 on 2021-02-05
Thank you friend, I will read through those items thoroughly before proceeding.

---

### Post by Morbius1 on 2021-02-06
Is this post and all of these related:

[https://ubuntuforums.org/showthread.php?t=2457329&p=14018487#post14018487](https://ubuntuforums.org/showthread.php?t=2457329&p=14018487#post14018487)
[https://ubuntuforums.org/showthread.php?t=2457396](https://ubuntuforums.org/showthread.php?t=2457396)
[https://ubuntuforums.org/showthread.php?t=2457353&p=14018146#post14018146](https://ubuntuforums.org/showthread.php?t=2457353&p=14018146#post14018146)

---

