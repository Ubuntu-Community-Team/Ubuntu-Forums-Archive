---
title: "What is the default keyring?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by GaretJax on 2009-10-10
Using 9.04 UNR for the first time on my Dell Mini 9 and when I connected to my wireless it asked me to create a password for the Default Keyring.  I have no idea what this means.  How is this password going to be used?  What does it protect me from?  Is it okay if I skip making a default keyring, will I still be secure?

---

### Post by swoody on 2009-10-13
The default key-ring grants access to the saved passwords on your system. Such as with your internet connection - your encryption key/passphrase will be stored on your computer, but you may have to allow access for network manager to access your saved key by entering the keyring password and allowing it. It also protects your other keys as well - such as personal GPG keys, and keys needed to verify the Ubuntu repository. Personally, I would setup and use a keyring password, as if anyone trys to gain entry to your system, they won't be able to access your important keys and passwords without the keyring password.

I hope I explained that well enough, and cleared this up, rather than confusing you more :)

---

### Post by beastrace91 on 2009-10-13
In short - its a global password to store all passwords.

Personally I don't use one - but if you are worried about someone taking you computer and using it maybe you should have one ;)

~Jeff

---

### Post by GaretJax on 2009-10-13
I should probably be more worried about security than I am, seeing how this is a miniature laptop and could easily be stolen.  But I hardly use it outside of my house.

Suppose I am not using the key ring and my wireless password is stored on this system.  Then suppose my laptop is stolen, but the thief could not log onto my system because he doesn't know my logon password.  Could he still get my wireless password?

---

### Post by beastrace91 on 2009-10-13
Nope. Need the log on password to get to any of it ;) Thats why I just use "unsafe storage" for my keyring

~Jeff

---

