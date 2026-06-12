---
title: "root password forgot"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by aju1991 on 2011-08-02
I forgot my ubuntu os root password.
 I only know the user password.
 Is there any way to know my root password?????????
 please help me.....
 please...................

---

### Post by Vishal Agarwal on 2011-08-02
while installing ubuntu; it asks for a user login. that login is equivalent to super log in with the sudo command. try any command with sudo as:
sudo ifconfig

this will ask you for your sudo user password and you can work with that.

---

### Post by Elfy on 2011-08-02
Is this the debian root password again?

---

### Post by haqking on 2011-08-02
> **aju1991 said:**
> I forgot my ubuntu os root password.
 I only know the user password.
 Is there any way to know my root password?????????
 please help me.....
 please...................


unless you specifically enabled the root account and gave it a password there is no root password as it is disabled by default in Ubuntu.

Whenever it asks you for superuser credentials it requires your own password to temporarily eleveate priveleges using sudo, this depends on you being in the sudo group which you should be.

Do not enable the root account, it is not needed and poses a security risk if you do so.

---

