---
title: "keyring and login wont dissapear"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by ellisblake on 2011-03-19
i am the only user and i want to get rid of these things...

Have tried many things but nothing came out of it...

i.e
 some people suggested that i disable the daemon by going here...system->preferences-.startup apps...
I couldnt find any keyring daemon.I could only find the following and have already disabled:
1.certificate and key storage.gnome keyring pks11 component.
2.secret storage service:gnome keyring:secret service
3.ssh key agent:gnome keyring:sshkey..

Some also suggested to go to ubuntu software center and see if i have the keyring daemon installed...and surprise ..no such thing exists..

other suggestions were to go to gconf editor and find the app gnome keyring and disable the 3 files...ssh,secrets,and pkcs11...which i did but no success/

Another issue i have is that i dont know how to get rid of little window on boot up which asks me for password.

Tried the following and didn't work system ->administration->users and groups...
I changed my account type to "admin"and "password:not asked on login"
Nothing happened and no changes were made on login...I am still asked for password...And obviously once i login i am asked for the second password form the keyring ...

So i would be very grateful if anyone could come up with some workable solution...hopefully

ubuntu 10.10

---

### Post by cariboo on 2011-03-19
The reason you are being asked for a keyring password is because you use auto login. If you don't want to enter a keyring password on every boot, change the keyring password to a blank one. 

Go to Passwords & Encryption Keys, and right click the password and select change password, the rest should be pretty self evident from there.

---

### Post by ellisblake on 2011-03-20
thank you...thank you....:P

that worked very well...

---

