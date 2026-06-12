---
title: "[SOLVED] Encrypting personal files"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by augie2051 on 2008-12-27
Im trying to encrpt files and seem to be having some trouble.  I dont want to send the files I just want extra security so that someone can open a particular file.  On vista I was able to use the fingerprint reader or password to "lock" files on my desktop.  Can i do something similar in ubuntu or.  I tried using the encrption option when clicking the file the program seems to run and then I receive an error and it doesnt lock.  any help would be greatly appreciated.

---

### Post by nhasian on 2008-12-27
ubuntu 8.10 comes with the ability for each user to have their own private encrypted directory. from a terminal type:

```
sudo apt-get install ecryptfs-utils
ecryptfs-setup-private
```

---

### Post by augie2051 on 2008-12-27
that worked thanks

---

### Post by binbash on 2008-12-27
you can also use truecrypt to encrypt files

---

### Post by kevdog on 2008-12-27
For individual file encryption I would probably recommend gpg.  For directory or partition encryption I would recommend truecrypt.  For entire disk encryption I would recommend dmcrypt available on alternate CD installation.  SSHFS is another alternative - and would be recommended if you are accessing the encrypted directory or partition remotely.

---

### Post by hyper_ch on 2008-12-28
sshfs is no encryption tool... sshfs will just mount a remote directory through a ssh channel.

---

