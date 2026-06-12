---
title: "Keyring help"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by kerbion on 2011-05-23
Hey all,

New to Ubuntu and in love lol.

However when I boot my system now, the keyring security pop up shows up, and asks me to enter my password around 3 times, Twice it will work then the 3rd time it fails, and none of my typical passwords work. 

How can I reset that password?

Must I reinstall the OS?

---

### Post by wildmanne39 on 2011-05-23
> **kerbion said:**
> Hey all,

New to Ubuntu and in love lol.

However when I boot my system now, the keyring security pop up shows up, and asks me to enter my password around 3 times, Twice it will work then the 3rd time it fails, and none of my typical passwords work. 

How can I reset that password?

Must I reinstall the OS?
Hi, the 3rd pass word is for your wireless to conncet to your router, if you set that long password up and click to save in the icon at the top of the right corner then it should have saved it. The other pasword should be your user password. You can reset it with this link. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Hansholz on 2011-05-23
Keyring is a way of simulating Single Sign On. System>>Preferences>>Passwords & Encryption Keys

I'm still working this out myself. I've found You can use a Password folder to manage your website passwords. But I think you are being bothered by the key rings. You can  delete the keyring folders to stop them popping up. Or hit cancel and ignore it.

You don't need to reinstall the OS.

---

### Post by el_koraco on 2011-05-23
Go to System, Preferences, Passwords and Encryption keys, or if you're using the latest Ubuntu, open the Dash and start typing "passwords...". 

you'll see "Passwords default" Right click, choose edit, enter your password, and leave the "New passwords" boxes blank. It will then ask you if you want to use "unsafe storage", hit ok, and you should be done. 

You can also disable the automatic login, in which case you'll not be prompted for the keyring. I suggest that option, because the keyring is a hard beast to get rid of.

---

