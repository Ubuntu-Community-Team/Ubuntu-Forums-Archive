---
title: "Encrypt entire hard disk (after install)"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by abhiroopb on 2010-01-12
I currently have a hard drive where / and /home are on separate partitions.

I would like to encrypt my /home partition. I would like to do this WITHOUT re-installing Ubuntu.

Is this possible?

Thanks

---

### Post by HiImTye on 2010-01-12
[EncyrptedFilesystem:So how do I encrypt my home directory?]("https://help.ubuntu.com/community/EncryptedFilesystemHowto#So%20How%20Do%20I%20Encrypt%20My%20Home%20Directory?")

---

### Post by lotharmat on 2010-01-12
> **abhiroopb said:**
> I currently have a hard drive where / and /home are on separate partitions.

I would like to encrypt my /home partition. I would like to do this WITHOUT re-installing Ubuntu.

Is this possible?

Thanks


Yup - there is a package called 'ecryptfs' 

[Here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

---

### Post by HiImTye on 2010-01-12
I tried to stay away from encryptfs since it's inherently less secure, the article I posted covers encrypting all folders that are commonly used, including swap

but encryptfs would be easier

---

### Post by abhiroopb on 2010-01-12
Thanks to both of you!

@HiImTye: Thanks but the link was REALLY too complicated for what I was looking for.

@lotharmat: Thanks for your link, but I don't really want to create one SINGLE encrypted folder. I'd just like to encrypt everything in /home. Is there any way to do that?

Thanks!

---

### Post by HiImTye on 2010-01-12
[EncryptedHomeFolder]("https://wiki.ubuntu.com/EncryptedHomeFolder")

---

