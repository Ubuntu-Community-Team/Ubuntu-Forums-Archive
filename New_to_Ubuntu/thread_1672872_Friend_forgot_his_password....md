---
title: "Friend forgot his password...?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by projecthikari on 2011-01-21
So, a friend of mine comes up to me and says "I forgot the password to my ubuntu!"
FFFFFF
What should he do about this?

---

### Post by HermanAB on 2011-01-21
Boot and choose Safe mode, then change the password with the passwd utility.

---

### Post by MooPi on 2011-01-21
When rebooting hit the shift key to enter the grub menu. Choose the recovery mode. While in recovery scroll down to last option  which is ```
root
``` At the prompt type ```
passwd username_here
```User name being your friends user account name.
You will be asked for a new password and then a confirmation. Reboot after completion. New password should work.

---

### Post by cgb on 2011-01-21
Not sure if it works just in safe mode or not but if that doesn't work you can try the steps in the thread below.  Should get you sorted out.  

[http://ubuntuforums.org/archive/index.php/t-3609.html]("http://ubuntuforums.org/archive/index.php/t-3609.html")

*just saw MooPi's response, that should work as well and a little cleaner then the instructions in the link...

---

