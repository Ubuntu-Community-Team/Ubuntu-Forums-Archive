---
title: "Login (not auto) not unlocking keyring (with identical password)"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by ecreeves on 2011-07-31
Hi, I've seen a lot of posts with people receiving multiple keyring prompts following autologin. My issue is a little different. I don't have autologin turned on (I type my user password everytime) and my keyring password is identical to my user password (I've tried changing both to a different identical password as well). I still receive multiple prompts for my keyring password everytime I login. I believe it may be one prompt for each stored secure wireless network I have, as I just added a third network and it came with a third prompt.

I've seen in previous posts that one can make the wireless networks available to all users to go around the keyring process, but I don't want to do this. I believe the login process is supposed to unlock the keyring if the passwords are identical, so hopefully there is a fix to get that happening.

---

### Post by bkratz on 2011-07-31
Might be something useful here

[http://ubuntuforums.org/showthread.php?p=11099412#post11099412](http://ubuntuforums.org/showthread.php?p=11099412#post11099412)

---

### Post by ecreeves on 2011-07-31
Thanks for the reply, bkratz. I forgot to mention that I don't want to set any password blank (I'd seen that solution in previous posts).

Ideally I'd just like the functionality to work the way it is supposed to from my understanding, which is that I can enter my password once at login and have it both login and unlock the keyring (which is set to the same password).

---

### Post by mikejonesey on 2011-07-31
try loging in (and inserting passkey into keychain), so that you are logged in and unencrypted, then as root user use passwd to change password of use to a new temp password, maybee "bob" then again back to your orig pass... this should update the passwords across...

---

### Post by ecreeves on 2011-07-31
Thanks, but no luck unfortunately. It still prompts me for the same password three times to open the keyring. Also, I deleted my unused network connections, and it still asks for it three times, so I'm not sure why, but I guess it isn't related to those connections.

---

### Post by Matt3223 on 2011-08-01
I too have this issue, the community docs had some info concerning libpam-gnome-keyring, which is installed on my system.

I think what happened to me is that I opted for auto-login initially and then went back to manual login.. now it asks to unlock the default keyring.

My question is, when the unlock keyring window comes up, there is the option to display details. Within the details options there are settings to adjust how the keyring functions. Problem is, the option to automatically unlock the keyring upon login is dithered out and I am unable to select it, which, if I could would presumably fix the issue.

I'm on some more research, but this seems fixable. Need to edit some configuration file.... question is which one and how.

anyone understand /etc/pam.d/gdm file?

a part says

> 
session optional     pam_gnome_keyring.so auto_start
@include common-password


should the "optional" be something else?

[edit]

found this link. Looks like my /etc/pam.d/gdm file looks as it should.

[http://ubuntuforums.org/showthread.php?t=1506759](http://ubuntuforums.org/showthread.php?t=1506759)

soo...so much for that :)
[/edit]

[edit 2]

there are a ton of questions at askubuntu.com about keyring issues. several referenced the change default to blank, and others referenced how to change the default and login to match. Changing the default and login to match didn't work for me, so I am resigned to use the setting default to blank option. The popups are now gone, but that certainly doesn't feel like an appropriate fix. Still wondering why the option to click the radio button on the unlock keyring dialog details section is dithered... anyhow... 

here's the askubuntu.com link:  [http://askubuntu.com/questions/17353/remove-keyring-popup-on-startup](http://askubuntu.com/questions/17353/remove-keyring-popup-on-startup)

[/edit 2]

---

### Post by ecreeves on 2011-08-03
I agree, it seems like there should be a way to solve this issue that does not force you to compromise on security, given that it is just a question of restoring the functionality that is intended in Ubuntu.

Not sure if it is helpful to anyone who has seen this problem, but this is the contents of my /etc/pam.d/gdm file:

```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password
```

---

### Post by Alwimo on 2011-08-04
I have found this happen several times after installing it inside the "Try Ubuntu" option.

---

### Post by ecreeves on 2011-08-11
It is very possible that I installed from within the Try Ubuntu option, I believe over a broken Ubuntu system that had failed while updating to 11.04.

Lately it has been switching between asking to open the keyring 3 times and 2 times, with no clear reason why.

---

