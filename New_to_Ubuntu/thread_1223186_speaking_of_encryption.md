---
title: "speaking of encryption"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-25
i recently did an alternative install with encrypted LMV(not sure exactly what this is? ) 
is it effective in terms of encryption?

---

### Post by Crunchy the Headcrab on 2009-07-25
I believe what it means is that your data is encrypted so if someone was physically in possession of your hard drive they couldn't see your data unless A: they knew your password and could log in to your machine or B: they broke the encryption (not likely).

Is that what you are asking?  I'm sorry if I misunderstood.

---

### Post by foxmulder881 on 2009-07-25
That is correct.

---

### Post by heyyy on 2009-07-25
> **Crunchy the Headcrab said:**
> I believe what it means is that your data is encrypted so if someone was physically in possession of your hard drive they couldn't see your data unless A: they knew your password and could log in to your machine or B: they broke the encryption (not likely).

Is that what you are asking?  I'm sorry if I misunderstood.

yes 
so having this kind of install keeps my data encrypted and makes them inaccessible to others who might have physical access to the hard drive?

---

### Post by Crunchy the Headcrab on 2009-07-25
Precisely.  Of course the point is moot if they know your login password.  I don't encrypt my drives because nobody else uses this pc (it's a home laptop) and I've got nothing on it that would matter if someone stole it anyway.

---

### Post by heyyy on 2009-07-25
also comparing to truecrypt?

---

### Post by Sinkingships7 on 2009-07-25
> **heyyy said:**
> also comparing to truecrypt?

They do virtually the same thing. After encryption, binary data is unreadable because it is scrambled. I use TrueCrypt myself for certain sensitive files. Encrypting a whole drive has never even been close to a necessity for me.

---

### Post by 3rdalbum on 2009-07-26
The weakest points of drive encryption are:

1. The password. Most users don't choose a strong one.
2. The user. It's much easier to beat someone until they give you their password, than it is to crack the encryption scheme or brute-force a strong password.

---

### Post by jerome1232 on 2009-07-26
> **heyyy said:**
> i recently did an alternative install with encrypted LMV(not sure exactly what this is? ) 
is it effective in terms of encryption?

LVM, means Logical Volume Management, it's just a very flexible way to partition your discs. It's used with encryption alot so that you can have multiple Volumes but only require one pass phrase to unlock them.

---

