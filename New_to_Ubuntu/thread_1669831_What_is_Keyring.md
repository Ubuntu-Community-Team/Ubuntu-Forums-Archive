---
title: "What is Keyring?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by john77eipe on 2011-01-18
Hi,

I'm using Ubuntu 10.10 on my laptop. I use Wifi to connect to the internet/intranet. Recently I changed my password and forgot it. So I logged in as root and removed my password.

Now I can login successfully but when Ubuntu boots, it's asking for password to open keyring. And it accepts the old password only. (Lucky that I finally recollected it and is now connected to internet) 

But why does it retain the old password? Also how do I change it?

---

### Post by pl@yer on 2011-01-18
The idea of a keyring is to be able to remember only one password. New passwords can be added to the keyring. The passwords are probably stored encrypted in order to access the passwords on the keyring you give your password to decrypt.

---

### Post by Frogs Hair on 2011-01-18
Try System > Administration > Users and Groups for changing passwords.

---

### Post by john77eipe on 2011-01-18
I don't want to change my password. It's already changed and I'm able to successfully log into my system. But I get a message to "unlock keyring to connect to wifi". And the password that works here is only the old one.

I don't fully understand the keyring concept. :( Anyways, how do I change this password to the new one.

---

### Post by john77eipe on 2011-08-03
This is how I solved it.

Since key ring password is different from my login password, the key ring wouldn't be opened. You have to manually provide the key ring password.

But my keyring password is lost. 
Solution:
System > Preferences > Passwords and encryption keys
If you remember your password, right click on the key and choose change password.
If you don't, delete the key ring and create a new one. If you don't create one now, ubuntu will ask to create when a requirement occurs.

---

### Post by beacon on 2011-08-09
I have asked this before but never got a reply. It seems relevant to this thread so I wonder if someone here can help. It seems so simple to go to systen>preferences>passwords and encryption keys, but that is as far as I get. I receive the following error message:

Failed to execute child process "/home/xxx/Dropbox/Documents/Personal/Passwords/KeePassX-0.3.1-bin/bin/keepassx-bin" (Permission denied).

I'd be grateful for advice.

---

