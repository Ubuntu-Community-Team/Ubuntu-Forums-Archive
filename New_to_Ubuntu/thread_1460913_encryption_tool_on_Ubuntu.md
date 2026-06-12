---
title: "encryption tool on Ubuntu"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by codemaniac on 2010-04-23
hi friends i want to encrypt my ubuntu /home partition.. Suggest me some good encryption tools...Thanks..

---

### Post by nhasian on 2010-04-23
there are two ways that i know of, you could encrypt the folder during the installation of ubuntu, or you can use truecrypt.

---

### Post by codemaniac on 2010-04-23
would you please tell how do i install truecrypt..i could not find it in the repos

sudo apt-cache search truecrypt

does not return truecrypt..!!

---

### Post by @rizz on 2010-04-23
Try the PGP Key encryption 

  Go to
      
Accessories--> Passwords and Encryption-->Click on file -->New

A dialog box will appear and from there select PGP Key and that will start a wizard. Complete it and select a passphrase of your choice.

then right click on the folder and select the encrypt option.

This is the way i encrypt my mails and files

---

### Post by codemaniac on 2010-04-23
> Try the PGP Key encryption 

  Go to
      
Accessories--> Passwords and Encryption-->Click on file -->New

A dialog box will appear and from there select PGP Key and that will start a wizard. Complete it and select a passphrase of your choice.

then right click on the folder and select the encrypt option.

This is the way i encrypt my mails and files
 		                   		  		  		 		 			 				__________________

thanks pal for your reply . i tried your steps and set up the passphrase..Now when i right-click a folder , there is no "encrypt option" on the menu!!!!!!!!

---

### Post by @rizz on 2010-04-23
Oops forgot to mention 

  You need to reboot once!:lolflag:

---

### Post by nhasian on 2010-04-23
> **codemaniac said:**
> would you please tell how do i install truecrypt..i could not find it in the repos


[http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

---

### Post by bodhi.zazen on 2010-04-23
If you do not wish to re-install you can use ecryptfs or make a new home partition and use LUKS.

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

Tryecrypt is a nice tool, but it is not opensource. If you want an opensource option cryptfs or LUKS.

If you re-install sue the alternate CD to use LUKS. Both the alternate and desktop CE will give you the option of encrypting your home directory (ecryptfs), with or without LUKS (alternate CD).

---

### Post by codemaniac on 2010-04-24
thanks friends for your help..

---

### Post by KIAaze on 2010-04-24
If you just want to encrypt a few files:
[http://gringotts.berlios.de/](http://gringotts.berlios.de/)
Available in repositories.

Single file GPG encryption:
```
gpg --symmetric --encrypt --recipient MAIL FILE #("--symmetric": optional symmetric encryption allows decrypting without the GPG key, only password needed)
gpg --decrypt FILE
```

---

### Post by Paqman on 2010-04-24
> **codemaniac said:**
> thanks pal for your reply . i tried your steps and set up the passphrase..Now when i right-click a folder , there is no "encrypt option" on the menu!!!!!!!!

You need to install the package [seahorse-actions]("apt:seahorse-actions").

---

