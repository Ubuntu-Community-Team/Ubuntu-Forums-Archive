---
title: "New 1TB External Hard Drive is acting up with Ubuntu"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by corevette on 2009-10-07
I bought a WD Black Armor WS110 Terabyte Hard Drive last week

I transferred my library on to it, and the file transfer freezes halfway through

I figure the problem is NTFS + Linux, so I format it ext4

I try the transfers again, and it still freezes. Some of the transfers go through, while some of them just freeze. What is the problem?

---

### Post by QIII on 2009-10-07
How large is your "library"?  ext4 should be able to handle some whopping file sizes.

Can you transfer a single file to see how that goes?

---

### Post by corevette on 2009-10-07
I tried transferring a 300 mb Arch Linux iso and it froze transfer almost half way through....

I'm on 9.10 beta right now. Do you think it's Ubuntu's fault or the hard drives fault?

---

### Post by QIII on 2009-10-07
When I get home, I'll try to move a similar sized file from ext4 to another ext4 disk on my network.

That size file should be trivial ext4 to ext4.

---

### Post by corevette on 2009-10-07
> **QIII said:**
> That size file should be trivial ext4 to ext4.

Why? I have plenty of 4GB single files that transfer fine on NTFS and ext4, i feel like only recently it has been acting up.

---

### Post by QIII on 2009-10-07
Trivial -- commonplace or ordinary.

A file that size should be no effort.

---

### Post by corevette on 2009-10-07
I think i'm gonna back everything up, convert it to NTFS, and then go on windows and see if it still has problems

---

### Post by corevette on 2009-10-07
You know what's really strange, is I turned the external hard drive from vertical to a horizontal position, and it seems to be working flawlessly.

EDIT: Nevermind.

EDIT EDIT: Copying files off the drive works flawlessly with no freezing, the only problem is writing the files.

---

