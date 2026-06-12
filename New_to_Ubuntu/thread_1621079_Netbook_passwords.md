---
title: "Netbook passwords"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by mr best buy on 2010-11-13
I have a netbook with the netbook remix on it.  Each time I turn on the computer I am asked to enter a password.  each time i do not touch the keyboard for some minutes, I must enter a password.  Question: can I turn off this feature?
:confused:

---

### Post by Paqman on 2010-11-13
You can set the machine to automatically log in to your account without needing a password. Go to Applications > System > Login Screen.

You can adjust the length of time the system takes before locking the screen under Applications > System > Screensaver.

---

### Post by sisco311 on 2010-11-13
Don't know much about the UNR, but if memory serves, the menu is a little bit different...

If you don't find "Login Screen" and/or "Screensaver", then open a terminal and run:
```
gdmsetup
```and/or
```
gnome-screensaver-preferences
```

and if you want to disable the login password, but you don't want to enable auto login, then add your user to the **nopasswdlogin** group:
```
sudo gpasswd -a **username** nopasswdlogin
```
or users-admin (System -> Adminstartion -> Users and Groups) -> select your user -> Password: .... Change -> and select *Don't ask for password on login*.

EDIT: Oh, and if you disable "Lock screen when screensaver is active" in gnome-screensaver-preferences, then you won't be prompted for a password after the screensaver activates.

---

### Post by Paqman on 2010-11-13
> **sisco311 said:**
> Don't know much about the UNR, but if memory serves, the menu is a little bit different...


Since switching to Unity, it's changed again. You have an Applications icon on the launcher, and can then filter all those results for the System category. Login Window and Screensaver will be in there.

---

### Post by sisco311 on 2010-11-13
> **Paqman said:**
> Since switching to Unity, it's changed again. You have an Applications icon on the launcher, and can then filter all those results for the System category. Login Window and Screensaver will be in there.

Cool! Thanks for the info.

---

### Post by mr best buy on 2010-11-13
I am looking how to disable the screen that says:

"Enter password to disable keyring"
I may not have the correct words.

I found the application for login and I set it for automatic login.
Now it does
I set up the screen saver
and it works fine.

But after I login I  get a message about a keyring and enter a password.  I do not see how to disable this.
Thanks in advance

---

