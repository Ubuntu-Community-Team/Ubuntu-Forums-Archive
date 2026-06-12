---
title: "Auto-Login For Some Users"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by ertw1 on 2010-01-10
Hello everyone,

Here is my situation.  I have Xubuntu installed with four user accounts.  My user account is the only one with admin privileges.  

Here is my challenge to you.  After the computer is booted up and the login screen is presented I would like that just three of the user accounts be able to login on a single click (no password).  I would like only my account to require a password to login.

Thanks in advance guys!

---

### Post by gsmanners on 2010-01-11
There was a thread on that some time ago about modifying the PAM config for gdm.

[http://ubuntuforums.org/showpost.php?p=66046&postcount=11](http://ubuntuforums.org/showpost.php?p=66046&postcount=11)

Bear in mind that copy-pasta is not a good idea for this (as PAM uses selinux extensively nowadays), so it might be a good idea to think what they're doing through carefully before trying it out.

---

