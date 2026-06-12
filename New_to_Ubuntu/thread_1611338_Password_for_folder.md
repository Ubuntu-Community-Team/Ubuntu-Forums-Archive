---
title: "Password for folder ?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2010-11-01
Could anyone please tell me if I can put a password on folder?

---

### Post by LunaticHiatus on 2010-11-01
cryptkeeper, its in the software center. there is also easycrypt, but I never used it

---

### Post by holiday on 2010-11-01
> **cheekymonky2010 said:**
> Could anyone please tell me if I can put a password on folder?

You could put the folder in the home directory of a user you create for just this purpose. Then we will have to provide a username and password to access the folder. 

$ su - folder-owner

Give the password and there you are.

There may be other solutions but that is what I would do - unless I read something better from the others on this excellent forum.

---

### Post by whoop on 2010-11-01
Maybe Ubuntu's Private folder feature is something you are looking for. 

It encrypts a folder and auto mounts it on login. You can also make it not mount automatically, but manually via password.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by papibe on 2010-11-01
Not exactly. But there many ways to protect files and dirs, from other users, yourself, etc.

If the folder is a samba share (share folder over the network) it is very simple. If it's a local folder you can change the owner to the folder to root, and change the permissions to 700 (only access to root). That way only knowing the sudoers can access the file.

Did this help? If not, tell us more what you want to accomplish.

Regards.

---

### Post by ubudog on 2010-11-01
Check this thread out:
[http://ubuntuforums.org/showthread.php?t=829526](http://ubuntuforums.org/showthread.php?t=829526)

---

### Post by yetiman64 on 2010-11-01
I think probably the easiest/safest suggestion so far is that of papibe's, using folder access permissions. Just remember if you go this way and need access via the gui to use "gksudo" or "gksu" with nautilus to stop any problems on bootup (research .ICEauthority problems on this site to understand this).

I personally use cryptkeeper (leverages off encfs) as mentioned by LunaticHiatus and manually mount the folder from the Notification Area icon for it when access is needed. The main thing to note with this is the contents are encrypted and loss of the password could cause you difficulties. So far it has worked quite nicely for me.

---

### Post by whoop on 2010-11-02
> **yetiman64 said:**
> I think probably the easiest/safest suggestion so far is that of papibe's, using folder access permissions. Just remember if you go this way and need access via the gui to use "gksudo" or "gksu" with nautilus to stop any problems on bootup (research .ICEauthority problems on this site to understand this).


It could be the easiest, but it's far from safe/secure (live-cd or recovery console on the target machine and your in).

---

### Post by NertSkull on 2010-11-02
Most secure would be to encrypt it.  Requires a few more steps.  But using GnuPG or even Truecrypt would make it super secure.

---

### Post by ArgusVision on 2010-11-02
I've used and happen to like tuecrypt.  I  left detailed instructions on a different thread.  I'd post a link but I'm answering from my phone. (Doesn't support copy paste.) Search True crypt in the forums , or if you're interested in the step by step add my username to the search.

---

### Post by aeronutt on 2010-11-02
I've been using truecrypt for years, I'm very happy with it.

---

### Post by yetiman64 on 2010-11-02
> **whoop said:**
> It could be the easiest, but it's far from safe/secure (live-cd or recovery console on the target machine and your in).

True, I meant safest for data integrity/access (I should have been a bit clearer), in the sense of a beginner losing a password to an encrypted folder etc only.

Note my second paragraph re the use of cryptkeeper on my machine for higher security requirements. ;)

---

### Post by ArgusVision on 2010-11-02
Here's a link to the thread I mentioned earlier. 

[http://ubuntuforums.org/showthread.php?t=1553670&page=2](http://ubuntuforums.org/showthread.php?t=1553670&page=2)

---

