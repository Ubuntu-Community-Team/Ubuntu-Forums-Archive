---
title: "Password protect/Encrypt a directory?  NOT just chown to root..."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-05-14
Hi, all:

I have a few directories that I'd like to encrypt and password protect.  They have subdirectories in them as well.  I'd specifically like to have different passwords than my root or user pwds, and I'd specifically like to encrypt them.  

All the other suggestions I've read involve chowning the directories to root; if somebody's already in my box, I want to ensure that these directories are totally inaccessible and have failsafes...think Mission Impossible.

What would you all do?

Thanks!

---

### Post by Anthon on 2009-05-14
I have my whole /home encrypted. It is a seperate filesystem in a file and mounted when I log in (ie. pammount is used to take the (long) password for my account to decrypt the file). 
I have used cryptsetup to set this up. 
It is easier to do this if it is acceptable for you to 'just' have some directories mounted with an explicit command. However I wanted all of my users directory (including .ssh private keys) encrypted. That is why I went for pammount etc.
Lookup the use of cryptsetup or ping me directly if you want the specific commands.

---

### Post by sgosnell on 2009-05-14
Truecrypt.  It works on Windows also, so you can put the files on a flash drive and open them on a Windows box if you install the app on it.  It's in the repositories.

---

### Post by michy99 on 2009-05-14
+1 for Truecrypt.

---

### Post by AClark on 2009-05-14
+1 for TrueCrypt :)

---

### Post by Sub101 on 2009-05-14
Im a fan of cryptkeeper, which is also in the repos.

---

