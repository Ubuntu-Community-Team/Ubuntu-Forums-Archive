---
title: "Default keyring problems"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-02-03
Ok so i installed 10.04 on a Toshiba Satellite A205 and whenever I try and connect using Wifi it asks for a default keyring password and when I enter the login password it says incorrect password.  If I hit cancel a couple times it allows me to connect but after a few minutes it disconnects.  any ideas

---

### Post by Sealbhach on 2011-02-03
That is indeed annoying.

**EDIT:** This is a more drastic step, try the suggestion from mcduck below first.

   [http://ubuntuforums.org/showpost.php?p=9525808&postcount=11](http://ubuntuforums.org/showpost.php?p=9525808&postcount=11)

.

---

### Post by mcduck on 2011-02-03
> **Sealbhach said:**
> That is indeed annoying. Try this:  [http://ubuntuforums.org/showpost.php?p=9525808&postcount=11](http://ubuntuforums.org/showpost.php?p=9525808&postcount=11)

.

I wouldn't recommend that, at least unless all other methods fail. Simply because that will destroy all contents of the current keyring, which is absolutely unnecessary when the keyring password can be easily reset without loosing any data.... :)

Edit: At least it would be a good idea to warn about losing all stored data when providing such instructions.

---

### Post by mcduck on 2011-02-03
> **djyoung4 said:**
> Ok so i installed 10.04 on a Toshiba Satellite A205 and whenever I try and connect using Wifi it asks for a default keyring password and when I enter the login password it says incorrect password.  If I hit cancel a couple times it allows me to connect but after a few minutes it disconnects.  any ideas

Have you at some point changed your login password? In that case the keyring password is still the same as your original login password was.

Go to System/Preferences/Passwords and Encryption Keys, right-click the "Passwords:login"-keyring and select "Change Password". Type in your old password and set the new one to same as your current login password is.

Or, if you want to use automatic login (without typing your password at the login screen) set the new keyring password to empty. This will set the keyring to store passwords unencrypted, allowing applications to access them without requiring a password  to unlock the keyring first. It's slightly less secure but makes no meaningful difference if you use automatic login anyway.

---

### Post by djyoung4 on 2011-02-03
thank you mcduck.  worked perfect

---

### Post by djyoung4 on 2011-02-03
I spoke too soon.  It started doing it again and now I have no password and encryption key option under preferences

---

### Post by mcduck on 2011-02-04
Just noticed you are using 10.04? You shouldn't have had it under System/Preferences in the first place. :D Take a look in the Applications/Accessories -menu instead...

(or if all else fails open a terminal and run "seahorse" to start it.)

---

### Post by djyoung4 on 2011-02-04
> **mcduck said:**
> Just noticed you are using 10.04? You shouldn't have had it under System/Preferences in the first place. :D Take a look in the Applications/Accessories -menu instead...

(or if all else fails open a terminal and run "seahorse" to start it.)
Ok found it but on that box I get the first screenshot where there is a password:login option and a password:default option but on all my other boxes I get the second screenshot with them only having a password:login option

---

