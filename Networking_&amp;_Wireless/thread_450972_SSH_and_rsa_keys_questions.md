---
title: "SSH and rsa keys questions"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by theredcross on 2007-05-21
Trying to figure this thing out with [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH) and was fine until i started messing with the rsa keys. I've made a user which i wish to be able to connect remotely, now can I run ```
ssh-keygen -t rsa
``` as any user, or does it have to be that user? and as this other user does not have sudo priveleges and apparently also does not have permission to write to ~/.ssh/

Am I missing something? the rsa section of that article seems a little unclear to me.

---

### Post by mitch.c on 2007-05-22
> **theredcross said:**
> Trying to figure this thing out with [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH) and was fine until i started messing with the rsa keys. I've made a user which i wish to be able to connect remotely, now can I run ```
ssh-keygen -t rsa
``` as any user, or does it have to be that user? and as this other user does not have sudo priveleges and apparently also does not have permission to write to ~/.ssh/
After you generate the key pair, copy the contents of id_rsa.pub to ~/.ssh/authorized_keys on the PC you wish to access remotely. '~' SHOULD BE THE HOME DIRECTORY OF THE USER YOU WISH TO USE WHEN YOU LOGIN REMOTELY.

For example, if the user 'bob' desires remote access via ssh to PC-A, then /home/bob/.ssh/authorized-keys should contain the contents of id_rsa.pub (it really doesn't matter what account was used to generate the key). Now if the secret key id_rsa exists on PC-B, then bob can login to PC-A from PC-B like this:
```
bob@PC-B:~$ ssh bob@PC-A
```
After bob enters the passphrase, remote access will be granted.

---

### Post by theredcross on 2007-05-22
semantics can make all the difference, thanks a ton!
another question, some other SSH related pages mention dsa as well as rsa, what is the difference?

---

### Post by mitch.c on 2007-05-22
> **theredcross said:**
> some other SSH related pages mention dsa as well as rsa, what is the difference?
Different encryption algorithms, but both serve the same purpose. It's generally safe to assume they are equally strong. There are some patent and export restrictions on RSA.

---

