---
title: "Unique Password problem"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-06
Hii! Here it goes:-

1. I have Karmic installed on my computer and this is the only OS I have on my system.(No dual booting etc). And it has only one user.

2.A few days back, I decided to change the password of my system and went about doing it by going to "System>Administration>Users and Groups>Username>Properties>ChangePassword".Here I changed the password to say"XYZ".However even after rebooting the system , I found that **"XYZ"** never came into effect and still the old Password only worked.

3.Then I tried changing the password again. This time I went to "System>Preferences>About Me>ChangePassword." and changed the Password to **"ABC"**.And this time it worked and it did change. Now I could happily use my new password **"ABC"**.

4. Then yesterday I tried logging into empathy. When I tried using it , a pop up was displayed which said"[I] Unlock Keyring
Enter Password for default keyring to unlock.The application'Account Manager'(/usr/lib/telepathy/mission-controls)wants access to the default keyring but it is locked".[/I]And it asked for the password to which I entered my new system password**"ABC"**.But then it never accepted the password.However when I entered **"XYZ"**, it worked.

Now what is happening here.Why are there two passwords in force. It would be great if someone could help me with this. 

Regards
Vivek

---

### Post by asmoore82 on 2010-04-06
It sounds like you can just open "Applications -> Accessories -> Passwords"
and change your Keyring password to match '**ABC**' and you'll be all set.

Your login password and your keyring password are always 2 separate entities.
But at first they are both set to the password you used during installation.
Their separation is useful in an "auto-login" setup because in that case,
your login password is automatically bypassed but your keyring and
stored sensitive data is still *_not_* un-locked.

I'm not sure exactly how it fits together but the preferred method of changing
your password should be through the "About Me" Preferences.
Using the Administration menu is like the System Administrator
is breaking into your account for you. It's like the "lost password" scenario;
but it's too subtle to notice when the user and administrator are the same person.

---

### Post by vivek40 on 2010-04-06
Thanks asmoore! But what exactly is a keyring password(am quite new to linux.. all i know about is the login pwd ..coming from windows). Moreover when I goto applications>accessories>password and encryptionkeys.. i get the screenshot attached..
what should be done here.. where should the password be changed
Regards
Vivek

---

### Post by vivek40 on 2010-04-06
Someone please help with this!

---

### Post by mcduck on 2010-04-06
> **vivek40 said:**
> Thanks asmoore! But what exactly is a keyring password(am quite new to linux.. all i know about is the login pwd ..coming from windows). Moreover when I goto applications>accessories>password and encryptionkeys.. i get the screenshot attached..
what should be done here.. where should the password be changed
Regards
Vivek

The keyring is used to store passwords and encryption keys from many applications, like the Network manager, instant messengers and e-mail readers.

To change your keyring password just right-click the "Passwords: Login"-keyring in the manager and select "Change Password".

---

