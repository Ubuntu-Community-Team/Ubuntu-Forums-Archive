---
title: "enter password for default keyring to unlock"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Falc7 on 2009-07-28
I have done a lot of googling on this problem, and the solutions that have worked before no longer work, so i thought i'd make a thread about it.

Using Jaunty, i always have to put my password in to unlock the default keyring before ubuntu will connect to the wireless network when auto login is selected. All i want is for ubuntu to automatically log in, and connect to the internet. Can anyone help me set this up?

---

### Post by llamabr on 2009-07-28
Your keyring password must be the same as your login password for this to work:

[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

---

### Post by Falc7 on 2009-07-29
This is what my file looks like atm:
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
@include common-pamkeyring
```

But i got 'authentication denied' errors when i loged out :/
So i removed the last line, what else can i try?

---

### Post by Falc7 on 2009-08-04
Anyone? :)

---

### Post by mcduck on 2009-08-04
If you use normal login and your keyring password and login password are the same the keyring is unlocked automatically. With automatic login this doesn't work, which is why you need to type the keyring password.

There's an easy solution, remove the keyring password and you won't be asked for it any more. Of course that makes your system slightly less secure, but since you are using automatic login it makes no difference and you most likely don't have any important encryption keys or stuff like that in your keyring anyway.

To remove the keyring password go to Applications/Accessories/Passwords and Encryption Keys, then on the passwords-tab right-click the "default:login"-keyring, select "Change Password", and type your old password but leave the fields for new password empty.

(and, by the way, forget about that PAM stuff, that guide is rather outdated and doesn't really apply here. The stuff that it does is already working for you, as what it does is that it unlocks the keyring at login time. Which is exactly how things work out-of-the-box in the latest Ubuntu versions..)

---

### Post by Falc7 on 2009-08-04
Was following your instructions, but i don't seem to have the "default:login"-keyring

Here is a screenshot so you can see what i mean

[http://img44.imageshack.us/img44/3696/screenshotcdi.png](http://img44.imageshack.us/img44/3696/screenshotcdi.png)

---

### Post by mcduck on 2009-08-04
> **Falc7 said:**
> Was following your instructions, but i don't seem to have the "default:login"-keyring

Here is a screenshot so you can see what i mean

[http://img44.imageshack.us/img44/3696/screenshotcdi.png](http://img44.imageshack.us/img44/3696/screenshotcdi.png)

sorry, I meant the "passwords:login"-keyring.. I was just giving the instructions from my memory.. :)

---

### Post by Falc7 on 2009-08-05
Thats brilliant, thanks so much!

---

### Post by Georgesl on 2009-08-06
Just had to do this because I changed my own passwords and the keyring password doesn't update along with the user password.  Very annoying.  Here's how to get it back into alignment:

Go to Applications/Accessories
Click on Passwords and Encryption Keys
Click on the Passwords Tab
_Right-click_ on Passwords:login
Click on Change Password
Type the old password in the Old Password field
Type your new password in the Password field
Type your new password in the Confirm Password field
Click on the Change button

Hope that this helps.  This issue had me scratching my head for quite a while until I discovered the "Magic Right-Click!"

---

### Post by xjgnsdof on 2009-08-07
mcduck's suggestion did the trick. I had to delete the keyring password because Ubuntu One kept asking me for it when I logged in.

To compensate for the absence of a keyring password, one can always enable a password-protected login screen or, better yet, a password-protected system boot (via the BIOS).

---

### Post by mcduck on 2009-08-07
> **elgilicious said:**
> mcduck's suggestion did the trick. I had to delete the keyring password because Ubuntu One kept asking me for it when I logged in.

To compensate for the absence of a keyring password, one can always enable a password-protected login screen or, better yet, a password-protected system boot (via the BIOS).

If you use the password login, you can just as well also enable the keyring password. As long as your login and keyring passwords are same the keyring is unlocked automatically.

BIOS passwords are pretty much useless, as they are very easy to reset.

---

### Post by T-n-T Handywork on 2009-08-07
Thanks to those who posted solutions for the keyring issue. It's been driving me nuts!

---

### Post by rustutzman on 2009-08-07
> **mcduck said:**
> BIOS passwords are pretty much useless, as they are very easy to reset.

Desktops yes. Laptops no.

---

### Post by mcduck on 2009-08-07
> **rustutzman said:**
> Desktops yes. Laptops no.

Depends on laptop. Every laptop I've had has had a CMOS reset button in the bottom, which makes resetting the BIOS password even easier than it would be on a desktop machine..

In addition many laptops clear the CMOS if you just remove the battery and hold power button for couple of seconds.

---

### Post by brendanpiater on 2009-08-16
> **Georgesl said:**
> Just had to do this because I changed my own passwords and the keyring password doesn't update along with the user password.  Very annoying.  Here's how to get it back into alignment:

Go to Applications/Accessories
Click on Passwords and Encryption Keys
Click on the Passwords Tab
_Right-click_ on Passwords:login
Click on Change Password
Type the old password in the Old Password field
Type your new password in the Password field
Type your new password in the Confirm Password field
Click on the Change button

Hope that this helps.  This issue had me scratching my head for quite a while until I discovered the "Magic Right-Click!"

This worked for me, thank you very much!

Cheers
B

---

