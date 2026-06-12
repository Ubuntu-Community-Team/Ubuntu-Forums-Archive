---
title: "Wireless Configuration file location?"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-04-06
Hello again :)

I feel like I live here with all these questions, but here it goes :).


Well I am trying to make a program that will automatically find my wireless config file and replace it with the one that I choose, why is this needed? because it is my customized ISO image, and nothing gets saved except on the ISODevice(which grub controls the iso).

I am just trying to find out where the ubuntu store the password for wireless config files, so I dont have to keep logging in and all that.

Anyone know?

EDIT: I've been digging into it as well on google, and the more I dig into it, the more questions come to mind like does the password even get stored in ubuntu at all, is it in the router or adapter perhaps?

2nd Edit: I Found the Gnome2/Keyrings folder from google, it is a binary file.

So I guess if I decode that, that will be the login/password?

---

### Post by ericeclifford on 2010-04-07
Can anyone confirm that the gnomekeyring in the .gnome2 folder is the password storage file for wireless configurations?

The keyring file seems to be encrypted, is it possible to decrypt it, if I am on the local machine.

---

