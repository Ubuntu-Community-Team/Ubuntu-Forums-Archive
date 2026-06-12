---
title: "Hardy: Enter password for default keyring to unlock (nm-applet)"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2008-05-23
I upgraded to Hardy from Gutsy and I had setup pam keyring to automatically unlock the keyring. After upgrading it is prompting me again. If I go into Seahorse there is a keyring in there and is set to default in the drop down and I cant change it to anything else.

Can someone please advise me the best way to automatically unlock the nm-applet for my WPA key so that my wireless works without having to enter my password?

---

### Post by SnowPunk98 on 2008-05-25
bump

---

### Post by prshah on 2008-05-25
> **SnowPunk98 said:**
> 
Can someone please advise me the best way to automatically unlock the nm-applet for my WPA key so that my wireless works without having to enter my password?

If you set your keyring password the same as your login password, keyring will unlock automatically and not prompt you for your password. You can use seahorse to change your keyring password.

It's not exactly what you asked for; hope it helps though.

---

### Post by SnowPunk98 on 2008-05-26
I tried that and it did not work, still prompts me.

---

### Post by SnowPunk98 on 2008-05-29
bump

---

### Post by davidyu on 2008-05-29
Hi:
       I have the same problem after upgrading to 8.04 Hardy.
However i found the solution :
from :[http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock](http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock)

To get rid of the keyring prompt after automatic login in hardy 8.04 you can:

System > Preferences > Encryption and Keyrings
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.

Related bug report (kinda) : [https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993](https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993)

---

### Post by SnowPunk98 on 2008-05-30
This did resolve the problem and thank you for the email as well. It warned me of the security risk by doing this but I suppose if they have my login it doesn't really matter.

Does having no password on the keyring present any other security issues if the only key in there is my WPA key?

---

### Post by kylirh on 2008-07-12
> **davidyu said:**
> Hi:
       I have the same problem after upgrading to 8.04 Hardy.
However i found the solution :
from :[http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock](http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock)

To get rid of the keyring prompt after automatic login in hardy 8.04 you can:

System > Preferences > Encryption and Keyrings
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.

Related bug report (kinda) : [https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993](https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993)

Thanks for the solution! It is nice to be able to auto log in and not have the keyring prompt anymore.

---

### Post by axm on 2008-08-09
> **davidyu said:**
> 
However i found the solution :
from :[http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock](http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock)


Posting here, since above is read-only:

After upgrading gutsy->hardy I had the same problem, I just deleted the login keyring and suspended twice, first to re-add the key to the restored login keyring, second to choose wlan to connect. Next suspend was fine, connected without keyring asking me for a password and my login password set for the keyring. Hope this helps.

---

### Post by shahin on 2008-08-17
Davidyu's solution worked for me.  Thank you.

---

### Post by deeesseee on 2008-08-17
Yeah, trying Davidyu's method worked for me as well.

---

### Post by meganox on 2008-09-10
Davidyu's method is insecure and you shouldn't use it if you keep important passwords on the login keyring.

> **axm said:**
> Posting here, since above is read-only:

After upgrading gutsy->hardy I had the same problem, I just deleted the login keyring and suspended twice, first to re-add the key to the restored login keyring, second to choose wlan to connect. Next suspend was fine, connected without keyring asking me for a password and my login password set for the keyring. Hope this helps.


This worked for me, simply deleted the keyring and logged in again, and the new keyring was created.  Added the WEP key, no more prompts.

---

