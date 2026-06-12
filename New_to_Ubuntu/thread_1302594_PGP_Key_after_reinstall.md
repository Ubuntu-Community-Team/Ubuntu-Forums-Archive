---
title: "PGP Key after reinstall"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-27
Hi guys,

I have a personal key with my name and email address that I signed the code of conduct with. It's still attached to my launchpad account. I reinstalled karmic RC today, and I want to use that same key in Karmic.

How do I "download" the key off launchpad and import it into Passwords and Encryption Keys?

---

### Post by duanedesign on 2009-10-27
The Public part of the key is still attached to your launchpad account. It is no good without the Private key. Not having a backup of your private key is bad: the system was designed exactly to prevent people from regenerating the same gpg key twice. If when you reinstalled you had a separate home partition that you didnt format or hopefully you have a back up or created a revocation certificate and burned it to a CDROM when you created your key - you can now revoke this key and create a new one.

Otherwise, well... you public key will remain on the key servers for ever. Don't worry it happens to the best of us. ;)

If you dont have a back up or revocation certificate you will need to create a [new pgp key]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") and upload it to your Launchpad account. Dont forget to make many back ups and store them in different places. I have a backup at my house and one at my parents house. Some people even put a copy in their safe deposit box.

---

### Post by wojox on 2009-10-27
Never mind misread.

---

### Post by humphreybc on 2009-10-27
> **duanedesign said:**
> The Public part of the key is still attached to your launchpad account. It is no good without the Private key. Not having a backup of your private key is bad: the system was designed exactly to prevent people from regenerating the same gpg key twice. If when you reinstalled you had a separate home partition that you didnt format or hopefully you have a back up or created a revocation certificate and burned it to a CDROM when you created your key - you can now revoke this key and create a new one.

Otherwise, well... you public key will remain on the key servers for ever. Don't worry it happens to the best of us. ;)

If you dont have a back up or revocation certificate you will need to create a [new pgp key]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") and upload it to your Launchpad account. Dont forget to make many back ups and store them in different places. I have a backup at my house and one at my parents house. Some people even put a copy in their safe deposit box.

I've got a backup of my home folder, where would I find my private key?

---

### Post by sgosnell on 2009-10-27
In the .gnupg folder.  If your backup includes hidden folders.

---

