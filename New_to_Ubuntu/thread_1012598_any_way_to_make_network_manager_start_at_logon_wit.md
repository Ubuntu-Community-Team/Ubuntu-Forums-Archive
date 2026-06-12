---
title: "any way to make network manager start at logon without requireing password?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by jeromey on 2008-12-16
every time i boot my computer and log in to my user it asks me to enter my password to unlock the default keyring for nm-applet

i am the only person who uses this computer and there is really no need for this

is there any way to put an end to this behavior and make the default keyring unlock automatically?

---

### Post by sdennie on 2008-12-16
Does your keyring password differ from your login password?  If so, try going to System->Preferences->Encryption and Keyrings click on the "login" keyring and change then the button that allows you to change the password.  Set the password to the same as your login password and it should unlock automatically.

---

### Post by plucky on 2008-12-16
@vor

Shouldn't that be **Applications > Accessories > Password and Encryption Keys > Edit > Preferences** and then select Login keyring?


System->Preferences->Encryption and Keyrings doesn't work for me on 8.10.


Good Luck

---

### Post by sdennie on 2008-12-16
> **plucky said:**
> @vor

Shouldn't that be **Applications > Accessories > Password and Encryption Keys > Edit > Preferences** and then select Login keyring?


System->Preferences->Encryption and Keyrings doesn't work for me on 8.10.


Good Luck

It sounds like 8.10 and 8.04 (which is what I'm on) must differ in this case.  One of the two should work!  :)

---

### Post by flanagan on 2008-12-16
All the above is good advice and it should work. But, in case it does not, then you have likely run into an annoying bug in network manager that many experienced under 8.04. Back when I was using 8.04, I had to replace network manager with Wicd to get around the same problem. See [http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04](http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04) for instructions.

I should mention that I have a couple machines with clean installs of 8.10 that have no such trouble with network manager. The bug was probably fixed.

---

### Post by S_e_P_p on 2008-12-16
Hello,

please find solution in this thread:

[http://ubuntuforums.org/showthread.php?t=1003471](http://ubuntuforums.org/showthread.php?t=1003471)

Kind regards,

SePp

---

