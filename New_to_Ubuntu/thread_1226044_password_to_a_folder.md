---
title: "password to a folder????"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by koyakishore on 2009-07-29
hiii...

in my system..i have personal data..

as my system is used by many ppl..i want to keep that data safe..

now..my question is "will that be possible to give password to a folder???"

also.. as i'm new to ubuntu.. i dono how to hide folders..

so, i need answers for both..

thanks in advance..:)

---

### Post by cozmicharlie on 2009-07-29
> **koyakishore said:**
> hiii...

in my system..i have personal data..

as my system is used by many ppl..i want to keep that data safe..

now..my question is "will that be possible to give password to a folder???"

also.. as i'm new to ubuntu.. i dono how to hide folders..

so, i need answers for both..

thanks in advance..:)

The safest way to protect your info is to encrypt your files.  A number of programs can do this truecrypt, ecrypt, encrypt.  Do a search for encryption and you will find plenty of tutorials.  You can start here:
[http://tombuntu.com/index.php/2007/09/03/using-truecrypt-on-ubuntu-for-encryption/](http://tombuntu.com/index.php/2007/09/03/using-truecrypt-on-ubuntu-for-encryption/)

---

### Post by Sub101 on 2009-07-29
I find cryptkeeper the best encryption program for encrypting single folders.

---

### Post by Paresh on 2009-07-29
Try ecryptfs-utils.

this will allow you to create a ~/Private folder where you can keep all your personal info and this will mount and unmount automatically when you log in.

Only you will have access to this folder, any other users looking into your home directory will see gobbledegook.

try this to install & setup
```

sudo apt-get install ecryptfs-utils
ecryptfs-setup-private

```

then log out & log back in, you are all set to go.

Also hidden files and directories have a '**.**' in front of them, so, for example '**thisfile**' is not hidden, but '**.thisfile**' is hidden.

---

### Post by grizato on 2009-10-28
By The Way, if you don't know how to hide files or folders, you have to rename them and add a little "." at the begginging.:biggrin:

---

### Post by mikewhatever on 2009-10-28
> **grizato said:**
> By The Way, if you don't know how to hide files or folders, you have to rename them and add a little "." at the begginging.:biggrin:

So far so good, but obviously, anyone smart enough to be able to hit ctrl+h can unhide the hidden files in a second.

---

### Post by yknivag on 2009-10-28
Encryption is fine, but you risk losing files completely should the key be lost or forgotten.

The easy way to prevent others seeing your files is to ensure each user has their own username and to run:
```
chmod 600 <filename>
```
on the files you want to be hide.

That way they will not be readable by anyone other than the owning user and root.

Whilst this doesn't encrypt the files and doesn't stop anyone with sudo rights from accessing them, it will stop all other standard users and is much less fraught that encryption (no keys to remember etc).

It all depends on how secure you want your data to be.

---

