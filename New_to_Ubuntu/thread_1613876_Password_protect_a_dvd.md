---
title: "Password protect a dvd"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by arju305 on 2010-11-04
Guys. Is there a way that we can password protect a dvd iso and then burn it on a dvd with password protection. After burning, it must ask for a password while mounting in any computer.

---

### Post by P4man on 2010-11-05
No. You can always read whats on a dvd (or harddrive or usb stick or whatever). You might be able to encrypt the data you put on the dvd, but can you elaborate what exactly you are trying to achieve?

---

### Post by lotharmat on 2010-11-05
teh prons collection obviously!  ;)

---

### Post by arju305 on 2010-11-05
Ok. I want some files of mine to be burned in a dvd. I dont want those files to be opened by others by any means i.e. they are highly confidential. 
Whenever any one put the dvd on any dvd drive, it should ask a permission for opening it.

I want to burn a collection of files of different formats i.e. txt, docs, videos etc...... in the same dvd.

---

### Post by arju305 on 2010-11-05
> **lotharmat said:**
> teh prons collection obviously!  ;)
But that is not a case.

---

### Post by julio_cortez on 2010-11-05
The only time I needed to do something similar (they were documents we were using at work) I created a compressed file (rar) protected with password and copied it to a USB stick. Then gave the stick myself to the recipient and sent him the password via SMS :D

I don't know if it can be done to an entire DVD though.

---

### Post by Hippytaff on 2010-11-05
A long shot but can you change the permissions of the files or ownership so that only the owner and a named user can read them.
 
You can buy password protected usb's. we have them in work.

---

### Post by P4man on 2010-11-05
> **Hippytaff said:**
> A long shot but can you change the permissions of the files or ownership so that only the owner and a named user can read them.

It would be trivial for anyone to retake ownership, assuming UDF or any other DVD filesystem supports this, and afaik, it doesnt.
 
```
You can buy password protected usb's. we have them in work.
```

Thats one way (although Im not sure how well these work with linux?) or like the above poster suggested, put the files in a password protected archive.

---

### Post by aeiah on 2010-11-05
use truecrypt. its multiplatform.

create an encrypted image, mount it, put your stuff in it, dismount it, and burn the encrypted image file to a dvd, along with a copy of truecrypt portable for windows or something.

---

### Post by Grenage on 2010-11-05
Encryption is about the only option here; Truecrypt has been mentioned, and I'd also recommend it.  It's easy to use, cross platform and very secure.

---

### Post by aeiah on 2010-11-05
aye we use truecrypt at work if we're demonstrating our software anywhere or anything. just put a copy of truecrypt portable on along with the encrypted image file and you'll be able to get to it easily on any windows pc (and any other that has an internet connection)

---

### Post by ibizatunes on 2010-11-05
If you zar all the files up and burned a password protected zar (you will only be able to extract them on a computer) but that might work

---

### Post by CharlesA on 2010-11-05
+9000 for truecrypt. The only way for it to be unreadable is to encrypt it.

---

### Post by arju305 on 2010-11-05
Thanks. I will try that.

---

