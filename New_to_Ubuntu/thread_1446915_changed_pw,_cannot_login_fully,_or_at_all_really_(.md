---
title: "changed pw, cannot login fully, or at all really (encrypted user folder)"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by reighlok on 2010-04-04
I just changed my user password and all seemed okay, but when I try and login from the home screen it will only accept my old password. This gets me past the login screen, but it seems like it cannot decrypt my user folder (or whatever it is called). My guess is that it only changes the user partition password and not the login password yet it will only use the login password to decrypt the home folder and let me use the computer. What can I do? All help is appreciated. I have some work in progress papers due soon and I really really do not want to lose all my work. Thank you.

---

### Post by NightwishFan on 2010-04-05
Try this, change the encfs password:
```
encfsctl passwd /home/.enc/**username**
```

Then reboot. Replace "username" with your user name. If that does not work look for help here:
[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

---

