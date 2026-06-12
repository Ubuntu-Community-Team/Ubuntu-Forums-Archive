---
title: "Hard Disk Encryption"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by josh.wright on 2010-03-12
Hello,

First post on this forum, so hello everyone!

I've got a question about the Hard Disk Encryption on Ubuntu 9.10. Is it possible to change the password for it? I haven't found out how, did initially think that it could be done with 'passwd' in the terminal or via the users and groups interface in Administration but they didn't work.

Thank you!

---

### Post by partloer on 2010-03-12
Hi Josh Wright,

First time posting for me as well.  The passwd command is just for changing the passwords for the user logins.  For changing the Hard Disk Encryption read this post [http://ubuntuforums.org/showthread.php?t=670667 ]("http://ubuntuforums.org/showthread.php?t=670667")

If this doesn't work let me know.

---

### Post by josh.wright on 2010-03-15
Thank you for the link. 

I've just run into problems in that my laptop would not boot, I've found a thread that addresses the problem though, once thats fixed I'll then have a look at the hard disk encryption.

[http://ubuntuforums.org/showthread.php?t=1425644&highlight=ICEauthority](http://ubuntuforums.org/showthread.php?t=1425644&highlight=ICEauthority)

---

### Post by J V on 2010-03-15
Go for home encryption, much faster and about me will change the encryption passphrase too (wrapped decryption)

---

### Post by albert s on 2010-03-15
Im adding a second HDD to my computer, is there a simple way to encryt it, and leave the original HD as it is?
would truecrypt be suitable?
I dont need anything super secure, just to stop the nephew etc messing about with some files accidently, a password would mean he would be stopped in his tracks before clicking the wrong thing.

---

### Post by partloer on 2010-03-15
Hi Albert S,

Another option would to create a separate account for your nephew.  That way you could control what folders, settings, permissions he has for the computer.  While this is not encrypted is does prevent him from having access and messing with files among other settings.  

You could use truecrypt I have used this before and it works well. Once you setup the second hard drive you can encrypt the entire hard drive or setup a volume which you have have on either the main hard drive or second hard drive.
[http://www.truecrypt.org/docs/]("http://www.truecrypt.org/docs/")

The main thing with encryption is to make sure you remember when you decrypt and encrypt.  For example you could decrypt your files to work on them then give your nephew your computer without encrypting them again this would allow your nephew access the files.  So make sure that you encrypt them again once you are done working.

---

