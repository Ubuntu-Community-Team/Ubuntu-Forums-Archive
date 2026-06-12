---
title: "Want to Set Up User Name and Password Login Screen"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by tb75252 on 2011-01-20
I am using Ubuntu 10.10 (32-bit)

Right now, when I start Ubuntu there is no login screen.  (I created only one user account and when I boot up it goes directly into that user without asking for user name or password.)  I now would like to create a login screen asking for user name and password for safety reasons.

I go to System -> Administration -> Users and Groups.  It shows a single user account and under Password it says "Asked On Login".  That cannot be right because the system boots into the user account without asking for a password.  I know that I created a root password when I installed Ubuntu but I do not remember having created a user password.  If I click on the Change button near the Password entry, the pop up window wants to have the old password...

Anyhow, how do I create a login screen asking for user name and password?

---

### Post by Layvian on 2011-01-20
Try going to [System > Preferences > About Me], that should do the trick, I did the same originally and it worked for me.

---

### Post by tb75252 on 2011-01-20
> **Layvian said:**
> Try going to [System > Preferences > About Me], that should do the trick, I did the same originally and it worked for me.

Did as you suggested.  A popup window wants to know my current password.  The thing is that I do not have a current user password; I never set one up in the first place...  I tried leaving the field blank but Ubuntu does not like that!

---

### Post by uRock on 2011-01-20
You had to make a password during the ubuntu install. How have you been running updates without a password?

This link may be helpful. [Psychocats FTW!]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by tb75252 on 2011-01-21
> **uRock said:**
> You had to make a password during the ubuntu install. How have you been running updates without a password?

This link may be helpful. [Psychocats FTW!]("http://www.psychocats.net/ubuntu/resetpassword")

When updates runs, it wants to know the  _root_ (the System Administrator) password before installing patches.  I have no problem with that as I know what that password is.  What I want to do is create a login screen for the _user_ account(s).  Right now, I do not get such a login screen when I boot up.

The link you gave looks promising.  I'll take a look at it tomorrow.  Do you know if the method suggested creates a login screen?

---

### Post by ubudog on 2011-01-21
To create a password for yourself, open a terminal (Applications>Accessories>Terminal) and type the following...

```
passwd
```

If you don't already have a password, it should ask for a new password.  Set one, then try the login screen.  Maybe that will work.  Not sure... Anyway, good luck!  

PS: Psychocats is an awesome site.  Very helpful.

---

### Post by uRock on 2011-01-21
> **tb75252 said:**
> When updates runs, it wants to know the  _root_ (the System Administrator) password before installing patches.  I have no problem with that as I know what that password is.  What I want to do is create a login screen for the _user_ account(s).  Right now, I do not get such a login screen when I boot up.

The link you gave looks promising.  I'll take a look at it tomorrow.  Do you know if the method suggested creates a login screen?
That is the password for your user account as well. In Users & Groups, you can tell it to start requiring the password to log in.

---

### Post by ubudog on 2011-01-21
> **uRock said:**
> That is the password for your user account as well. In Users & Groups, you can tell it to start requiring the password to log in.

@tb - Did that work?

---

### Post by tb75252 on 2011-01-21
> **uRock said:**
> That is the password for your user account as well. In Users & Groups, you can tell it to start requiring the password to log in.

Since I am a newbie, let me make sure I understand what you are saying:  If I set one user account (or more than one user account, for that matter!) within the Ubuntu installation and I want that user to log in whenever he/she uses the computer, are you saying that he/she would have to use the same password that I created for the _root_ account?

Can't I just set up a different password for the user?  It seems to me that, from the point of view of security, it is not a good idea to use the same password.  I am probably misunderstanding what you are saying...  :-)

---

### Post by tb75252 on 2011-01-21
> **ubudog said:**
> @tb - Did that work?


Have not tried yet...

---

### Post by uRock on 2011-01-21
> **tb75252 said:**
> Since I am a newbie, let me make sure I understand what you are saying:  If I set one user account (or more than one user account, for that matter!) within the Ubuntu installation and I want that user to log in whenever he/she uses the computer, are you saying that he/she would have to use the same password that I created for the _root_ account?No, _your_ user account password is the same as the root password. 

> Can't I just set up a different password for the user?  It seems to me that, from the point of view of security, it is not a good idea to use the same password.  I am probably misunderstanding what you are saying...  :-)When you create new accounts in the User and Groups application you will be asked to give that person a password.

---

### Post by tb75252 on 2011-01-21
> **uRock said:**
> No, _your_ user account password is the same as the root password. 

When you create new accounts in the User and Groups application you will be asked to give that person a password.

Thanks for the clarification!  I'll give it a try this evening and see what happens.

---

### Post by ubudog on 2011-01-21
> **tb75252 said:**
> Thanks for the clarification!  I'll give it a try this evening and see what happens.

Ok, cool.  Good luck, and keep us informed!  :p

---

### Post by tb75252 on 2011-01-21
> **ubudog said:**
> Ok, cool.  Good luck, and keep us informed!  :p

This is what I did to create a login screen asking for user name and password:

1)  System -> Administration -> Users and Groups.  Select the ***Change*** button near the ***Password*** line of the user account.  Select ***Set Password By Hand***, enter the original password (which for me was the one that I used for creating the root account) and then create a new password.
2)  System -> Administration -> Login Screen.  Unlock the popup window using the password just created and select ***Show The Screen For Choosing Who Will Log In***.

When you re-boot you should be presented with a login screen.

It turns out that as a default Ubuntu has no password for the root user.  (Source:  [http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu)).  So I did exactly what the link suggested:  I opened a Terminal window and typed in ***sudo passwd***.  It first asked me to enter the user name password (created as per instructions above) and then it asked me to create and confirm a password for root.  For safety reasons I recommend that the root and user name(s) passwords not be the same.

I'll be testing things in the next few days and report back if I run into problems...

---

