---
title: "Can't Enter Pasword in TTY1?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Maccer_ on 2009-02-14
I wanted to install new nvidia drivers for ubuntu, but when I'm on TTY1(Ctrl+Alt+F1) I can't seem to enter a password after I specified the username "root".

Also, what is root's password? I used WUBI to install ubuntu because my MBR is slightly screwed over. :P

---

### Post by Archmage on 2009-02-14
The useraccount root is disabled in Ubuntu. Log in with your username and password and use sudo to perform root tasks.

You will ask for your userpassword when doing sudo every 15 minutes.

E.g. sudo rm /root/.mplayer/config to remove a file in the root-directoy.

---

### Post by davideotape on 2009-02-14
Roots default password is "toor" I think.

---

### Post by Dr Small on 2009-02-14
There is no root password, by default.
Login as your user account, and use sudo.

---

### Post by Maccer_ on 2009-02-14
Thanks for the very quick replies. When I login with my username, I can't enter my password either. How come?

---

### Post by damis648 on 2009-02-14
> **Dr Small said:**
> There is no root password, by default.
Login as your user account, and use sudo.

I thought it was randomly generated? Anyway, perhaps you don't realize that when logging into TTY1, your password does not show as you type for security reasons?

---

### Post by Dr Small on 2009-02-14
> **Maccer_ said:**
> Thanks for the very quick replies. When I login with my username, I can't enter my password either. How come?
Your password is being entered, just not visible on the screen, for security reasons.

---

### Post by Dr Small on 2009-02-14
> **damis648 said:**
> I thought it was randomly generated? Anyway, perhaps you don't realize that when logging into TTY1, your password does not show as you type for security reasons?
I didn't think so, as I have always been told that the root account is disabled by default, so there would be no password.

---

### Post by Maccer_ on 2009-02-14
> **Dr Small said:**
> Your password is being entered, just not visible on the screen, for security reasons.

:) Thanks for the information. I can log in now, but, I need a root password to install the nvidia drivers. Thanks for the quick support.

---

### Post by amauk on 2009-02-14
> **Maccer_ said:**
> but, I need a root password to install the nvidia drivers.No you don't

Type
```
sudo su
```
this will get you to a root terminal

---

### Post by Dr Small on 2009-02-14
> **Maccer_ said:**
> :) Thanks for the information. I can log in now, but, I need a root password to install the nvidia drivers. Thanks for the quick support.
Using sudo gives you root privileges. Please check out the following article:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Maccer_ on 2009-02-14
> **amauk said:**
> No you don't

Type
```
sudo su
```
this will get you to a root terminal

SUDO says it can't find su. :P (Or something along those lines) I typed "sodu su" after I logged in.
Edit: Very quick replies, hard to catch up.

---

### Post by Dr Small on 2009-02-14
> **Maccer_ said:**
> SUDO says it can't find su. :P (Or something along those lines) I typed "sodu su" after I logged in.
Edit: Very quick replies, hard to catch up.
It's **sudo** as in "**s**uper **u**ser **do**" :D

---

### Post by Kareeser on 2009-02-14
Append "sudo" to the command you wish to run.

i.e.
```
 sudo ./install
```

---

### Post by Maccer_ on 2009-02-14
Can somebody give me exact directions? This is stressing my brain out. :s Sudo install [NAME].run doesn't work... ugh, please help. :(

---

### Post by Maccer_ on 2009-02-14
I see how to use sudo su, but... it asks me for a password, mine doesn't work... Linux is awesome, advanced, but confusing. :/

---

### Post by amauk on 2009-02-14
well, you're typing in the wrong password
make sure caps lock isn't on or anything

---

