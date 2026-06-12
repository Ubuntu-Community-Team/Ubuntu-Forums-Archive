---
title: "Network Manager Applet"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by marcks on 2009-10-17
I am running Ubuntu 9.04

Every time I log in I am asked for a password for the 'Network Manager Applet'. I have read a few posts where it says this is your normal login password but that is not working, nor is pressing enter, or any passwords that I generally use.

I installed UbuntuStudio and this is when the popup appeared, prior to this when I chose to go into Ubuntu I didn't need to login.

Not sure what I have done. Can anyone help, please?

---

### Post by 3rdalbum on 2009-10-18
If it's the password to unlock the keychain, then you need to type your keychain password. Usually this is your normal login password (because we're all too lazy to set a different password for our keychain!), but if you set a different password then you will need to provide it.

If it's asking for a passphrase or key for your wireless network, that's a different story. You'd need to type in your wireless passphrase and make sure that the popup menus are set to accept a passphrase, or type your key and make sure it's set to accept a key.

As Network Manager is one of the first things you'd generally encounter that will use your Gnome keychain, you might have accidentally typed your wireless passphrase when it asked you to **create** a password for your keychain.

---

### Post by marcks on 2009-10-18
it's asking me to unlock the keyring but I don't know what the password is, I have tried them all and it doesn't like any of them. Is there some way to change whatever it is?

---

