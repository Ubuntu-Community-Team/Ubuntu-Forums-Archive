---
title: "Mobile Broadband Connection"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by ankit.vader on 2010-04-11
I use CDMA mobile broadband connection. Whenever I use network manager I get a message for a CDMA password. I'm certain that I did'nt give any such password. So every time I've to delete the exsisting connection and make a new one to access internet. Please Help:(

---

### Post by redbook4574 on 2010-04-11
> **ankit.vader said:**
> I use CDMA mobile broadband connection. Whenever I use network manager I get a message for a CDMA password. I'm certain that I did'nt give any such password. So every time I've to delete the exsisting connection and make a new one to access internet. Please Help:(

Are you using auto-login ????

---

### Post by ankit.vader on 2010-04-11
yes

---

### Post by redbook4574 on 2010-04-11
> **ankit.vader said:**
> yes

In that case it is asking for your root password, the best way I have found round this is to disable auto login.

---

### Post by ankit.vader on 2010-04-11
i tried the root password, it did'nt work

---

### Post by azertyh on 2010-04-11
hi,
are you sure that your mobile broadband hasn't a password?
in my case, the username and the password are set in the network manager.

---

### Post by 3rdalbum on 2010-04-11
> **redbook4574 said:**
> In that case it is asking for your root password, the best way I have found round this is to disable auto login.

There's no root password in Ubuntu!

It should be asking for the password to unlock your keyring. This is whatever you set it as originally, the first time you set up your connection in Network Manager. Often this ends off being your user account's password due to user laziness (I should know.. my keyring password is my user password too).

It might not be asking for the keyring password anyway. Can you confirm for us that it's asking for the keyring password, or that disabling auto-login stops the prompting? (System > Administration > Login Screen).

---

### Post by ankit.vader on 2010-04-11
@azertyh:: the username and password u r referring to are set in my network manager also. when I connect using network manager it first asks root password, then it asks another password for CDMA technologies which is different from my root password and password used in network manager.

---

### Post by ankit.vader on 2010-04-12
this is the password i'm referring

---

### Post by ankit.vader on 2010-04-12
please help!!
i'm tired of deleting and creating connection every time I need access internet:confused:

---

