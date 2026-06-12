---
title: "enter default keyring to unlock?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Grukmuck on 2009-02-02
im dual booting ubuntu 8.10 and windows xp, and whenever i log into ubuntu it asks me to enter my default kering to unlock so that i can connect to wireless internet. what do i have to do to make that go away and automatically connect without entering my password/keyring? 

not a huge deal, but just kinda annoying.


thanks in advanced.


-gruk

---

### Post by cmnorton on 2009-02-03
This means a password changed at some point. You should not see this. Here is a link that might help you.

[http://ubuntuforums.org/showthread.php?t=1040631](http://ubuntuforums.org/showthread.php?t=1040631)

---

### Post by Grukmuck on 2009-02-03
i went into Applications-> Accessories-> Password and Encryption Keys and under the password tab it has Network secret for Auto ACTIONTEC/802-11-wireless-security/wep-key0, so i double clicked it and two windows pop up, the one on top ask for me to allow access for an application called "seahorse". i went to Places-> Search for files... and did a search for seahorse. and nothing came up.

what is seahorse?

---

### Post by HuaiDan on 2009-02-03
You were in the right place in assword and encryption keys. Then go to edit/preferences password keyrings tab. Find the keyring below and reset the password to the keyring as blank. It will give you a security warning but nevermind that.

Should b problem solved.

---

### Post by Grukmuck on 2009-02-04
that worked. i dont have that annoying keyring prompt anymore. thank you.


im still curious as to what "searhorse" is or was though.

---

### Post by mcduck on 2009-02-04
> **Grukmuck said:**
> that worked. i dont have that annoying keyring prompt anymore. thank you.


im still curious as to what "searhorse" is or was though.

Seahorse is Gnome's keyring manager (The one that opens when you go to Applications/Accessories/Passwords and encryption keys).

And the keyring is the way how programs can store their important encryption keys and passwords etc, so that you don't have to type them all the time yourself.

If you use the normal login (typing user name & password to login) the keyring gets unlocked automatically, but if you are using automatic login instead you need to give keyring password before programs can access keys & passwords stored in keyring. Removing the keyring password solves this, if you don't need the security.

---

### Post by Grukmuck on 2009-02-04
cool, thanks.

---

### Post by RealG187 on 2009-02-13
[http://ubuntuforums.org/showthread.php?t=1065954](http://ubuntuforums.org/showthread.php?t=1065954)

I can't access my wireless because of the ****ing keyring

---

