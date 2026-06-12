---
title: "Encrypt existing /home partition"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by newboyo on 2010-10-21
Hi all,
 
I've set my box up just so - and now realise that I should have encrypted my (separate)/home. I'm confused after reading (but not really understanding) the forum.
 
Here's what I plan to do -
1. backup /home (via rdiff) to an external HDD.
2. reinstall 9.10 with the encrypt option.
3. sync /home from the ext HDD home.
 
My questions are -
1. Will the plan work?
2. will the box be back to the way it was, before the experiment?
 
will appreciate advise on my plan or on alternative routes.
 
Rgds
 
New

---

### Post by pavel989 on 2010-10-21
> **newboyo said:**
> Hi all,
 
I've set my box up just so - and now realise that I should have encrypted my (separate)/home. I'm confused after reading (but not really understanding) the forum.
 
Here's what I plan to do -
1. backup /home (via rdiff) to an external HDD.
2. reinstall 9.10 with the encrypt option.
3. sync /home from the ext HDD home.
 
My questions are -
1. Will the plan work?
2. will the box be back to the way it was, before the experiment?
 
will appreciate advise on my plan or on alternative routes.
 
Rgds
 
New


im sure that u can enrypt on the fly, but incase you do want to do it your way, do u have any programs that uve already configured

---

### Post by pavel989 on 2010-10-21
i guess what your trying to do is
[this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

but if its an actual partition, you might wanna do [this]("https://help.ubuntu.com/community/EncryptedFilesystemHowto")

or you can really simply do [this]("http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html")

---

### Post by newboyo on 2010-10-21
> **pavel989 said:**
> i guess what your trying to do is
[this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")
 
but if its an actual partition, you might wanna do [this]("https://help.ubuntu.com/community/EncryptedFilesystemHowto")
 
or you can really simply do [this]("http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html")
 
Thanks vm. 
 
CryptManager seems to be the solution.
 
Would it encrypt the entire /home, or would the encryption be restricted to child directories of /home? 
 
Would the encrypted directory be susceptible to being opened by by someone with root access? << I've read of how encrypted directories can be opened (in case of laptop theft), because the thief has root access>>.

---

### Post by pavel989 on 2010-10-21
uh to be honest, i really do not know if itd only be the child directories, however, i doubt that it would do that. I would imagine it would encrypt the entire /home dir.

also, your confusing read access and encryption. encrypting means that you modify the data so that if anyone tries to access it, they would see more or less random data.

you can learn more from this wiki article about the back-ends of this app: [Cryptsetup]("http://en.wikipedia.org/wiki/Cryptsetup")
and [Linux_Unified_Key_Setup]("http://en.wikipedia.org/wiki/Linux_Unified_Key_Setup")

**_HOWEVER_**
if you save the password for it in a keyring manager, then i can imagine that with root access, if the keyring manager itself isn't protected with encrypted passwords, the keyring can be opened and thus so can the encrypted /home dir. therefor, i would recommend to make sure that your keyring manager does encrypt its passwords as well as its own password or just memorize the password.

honestly though, id be surprised if your keyring manager isnt encrypted

---

