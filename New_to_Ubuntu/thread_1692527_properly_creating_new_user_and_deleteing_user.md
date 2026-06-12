---
title: "properly creating new user and deleteing user??"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by extrafuzzyllama on 2011-02-21
hi all i am new to ubuntu and had to reinstall ubuntu because on my first install i completely messed it up

well at first it went well but it started with a account already named user

so i made myself an admin type account and deleted the old account and after reboot i got a iceauthority error and was only able to pull up the terminal

so i made a fresh install and decided to ask how to properly delete that default account and create a new account with full admin rights and then delete the old account

thx in advance

i am running ubuntu on my cr-48 with 10.10 btw in case that makes any difference

---

### Post by deconstrained on 2011-02-21
You can use Gnome's administrative tool for managing that, in your menu  at System -> Administration -> Users and Groups

Or, if you're feeling adventurous you could read up on the manual pages of usermod, userdel, passwd and gpasswd, and do it all from the command line.

You may need to add the new admin account to the /etc/sudoers file when you're done creating the new admin account. This can be done either by specifying the username of the account or by selecting a group. To do by username add a line that's "username ALL=(ALL) ALL", and to do it by group name, "%groupname ALL=(ALL) ALL" (prefix with a %)

---

### Post by seawolf167 on 2011-02-21
See [here]("https://help.ubuntu.com/community/AddUsersHowto") for the graphical & command line instructions on adding users

---

