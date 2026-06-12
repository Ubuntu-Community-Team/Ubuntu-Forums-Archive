---
title: "enigmail won't find GnuPGP after migration to linux"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by eskararriba on 2009-02-09
hi, 

I've got a problem getting enigmail to work with thunderbird:

I just changed from windows to linux (ubuntu 8.10), and migrated my thunderbird profile to the new OS. when I try to create a new key pair with the key manager, I get the following error message:

unable to locate GnuPG program "C:\Programme\GnuPT\GPG\gpg.exe". Make sure you have set the GnuPGP executable path correctly in the OpenPGP preferences

WHERE do I have do change WHAT exactly to fix this?
thanks

---

### Post by rbroom on 2009-04-27
If you have Enigmail loaded, you should have a menu called "OpenPGP" in Thunderbird.  Click on it and select Preferences.  The first tab ("Basic") lets you specify the location of gnupg.  The default is usually ```
/usr/bin/gpg
```.  If that doesn't work, open a command window (Applications/Accessories/Terminal) and type "```
which gpg
```".  If it comes back that's what you should put in the Engimail location field.  If it doesn't you can try finding it with "```
locate gpg|grep bin
```".

If THAT doesn't work, gnupg may not be installed.  Add the package gnupg.  (Applications/Add/Remove...)

Hope that's helpful.

---

