---
title: "How to access encrypted files with the passphrase?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by AlphaTwentyEight on 2010-12-22
Morning.

2 weeks into learning Ubuntu, 10.10.

Encrypted HD1 crashed, I have the passphrase.  

HD2 fresh install no encryption.

I want to access and recover the encrypted information from HD1, transfer to HD2 then reinstall 10.10 on HD2.

How do I do this?

---

### Post by AlphaTwentyEight on 2010-12-22
Gdecrypt?

---

### Post by AlphaTwentyEight on 2010-12-22
More background.  

When ubuntu asked me if I wanted to encrypt home I selected yes because it sounded like something interesting to do.  So the encryption must be the standard ubuntu 10.10 encryption.  The encrypted files are not sensitive mostly pictures and favorite urls, a lot of my creative work is in there which will be impossible to replace otherwise.  

If there is not an easy way to do this, I have plenty of time to work on it.  Some direction will be appreciated.  such as which utilities i need to use, what sort of commands do i need to master. where to find the man pages to do what I want to do, etc...

Thank you in advance.

---

### Post by AlphaTwentyEight on 2010-12-22
More background.  

So far what I have found is that I need to use ecryptfs.

I wrote this down when I made home encrypted:  ecryptfs-unwrap-passphrase

I am going over the ubuntu manpage:  [http://manpages.ubuntu.com/manpages/lucid/man7/ecryptfs.7.html](http://manpages.ubuntu.com/manpages/lucid/man7/ecryptfs.7.html)

From what I have read I assume there is no GUI to do what I want to do.  
The steps I think I need to take are.
1. mount the filesystem
2. specify where to put the files after encryption
3. tell encryptfs the passphrase to use

This is way more complicated than I thought.  I don't advise any new users to encrypt their home folder.

---

### Post by AlphaTwentyEight on 2010-12-23
I am able to boot the encrypted HD2 and log in, but only to the terminal with no GUI, so the hard drive it is not crashed.  

Can I move the contents of the encrypted home file from HD2 to HD1? 

When logged in to HD2 will the contents of home be decrypted when I transfer to the un-encrypted HD1?

---

### Post by rockerphil on 2010-12-23
yes, i'ts possible to move the contents of your home folder to your first hard drive, and as far as the files being encrypted, the drive becomes unencrypted upon login, and are encrypted when you're not logged in, so no, they won't be encrypted when you move them. in order to move the files you're going to need the first hard drive mounted to the file system, so if you would, please post the output of this command and i'll be willing to help you as much as possible.

```
sudo fdisk -l
```

this will give a list of your partition table. hope this helps,

Phil

---

### Post by AlphaTwentyEight on 2010-12-23
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk Identifier: 0x0001575a

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9357 75158528 83 Linux
/dev/sda2 9358 9730 2990081 5 Extended
/dev/sda5 9358 9730 2990081 82 Linux swap / Solaris
[ 201.169530] end_request: I/O error, dev sdb, sector 0
[ 201.169588] Buffer I/O error on device sdb, logical block 0
[ 201.169645] Buffer I/O error on device sdb, logical block 1
[ 201.169700] Buffer I/O error on device sdb, logical block 2
[ 201.169756] Buffer I/O error on device sdb, logical block 3
[ 201.169840] end_request: I/O error, dev sdb, sector 0
[ 201.169894] Buffer I/O error on device sdb, logical block 0
[ 201.169983] end_request: I/O error, dev sdb, sector 240121720
[ 201.170048] Buffer I/O error on device sdb, logical block 30015215
[ 201.170751] end_request: I/O error, dev sdb, sector 240121720
[ 201.170807] Buffer I/O error on device sdb, logical block 30015215
[ 201.170932] end_request: I/O error, dev sdb, sector 0
[ 201.170986] Buffer I/O error on device sdb, logical block 0
[ 201.171041] Buffer I/O error on device sdb, logical block 1
[ 201.171098] Buffer I/O error on device sdb, logical block 2
[ 201.171178] end_request: I/O error, dev sdb, sector 0

---

### Post by AlphaTwentyEight on 2010-12-23
if i do a mkdir /recover is that a file outside of /home?


and then can i move the files to /recover which would mean those files are no longer encrypted?

---

### Post by AlphaTwentyEight on 2010-12-23
yes that works.  I did a: mv Favorite /recover 

sweet

Thank you Phil

---

