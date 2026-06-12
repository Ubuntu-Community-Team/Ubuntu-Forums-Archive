---
title: "Painfuly new, trying to replace, remove, anything with passwords"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by hutchman on 2010-08-30
I started with this pc about 6 months ago. Came w/ fresh Ubuntu install. Things happened & I didn't get back to it for around 6 months. Now can't remember (or find) where I wrote both, my user & my keyring passwords. I may have even deleted them. I also have a Ubuntu install disk but can't seem to boot from it so I can re-install, even though I push F10 at startup and choose DVD drive, it continues to start the O/S that I have no passwords for. Oh yeah, version 10.04 on a pretty old Gateway all in one.   Would appreciate any help...
Thanx, hutchman

---

### Post by Elfy on 2010-08-30
First - I would check that you are set to boot from cd.

You can change the password from recovery mode though - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by hutchman on 2010-08-30
> **forestpiskie said:**
> First - I would check that you are set to boot from cd.

You can change the password from recovery mode though - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thank you so much for your quick response. Sorry it took me so long to  get back. I did go into bios and set it to boot from cd, but it seems  that it still boots into the old O/S with an icon to open the disk in  the top left Corner of the desktop & even in the disk I don't appear  to have control. When I went to the link you sent & tried to follow  those instructions I also failed. I cant open the run window. I can  however get as far as the "Drop to root shell " thing. When I type  "passwd my username" it says that I don't exists. I've tryed everything I  can think of/find at the link you sent with no luck. I know you sent  good info, but think I just am to new at this to use it properly. 
Thanx again & anything else you might think of I will appreciate.
hutchman

---

### Post by silverglade00 on 2010-08-30
If you go back to the root shell and type in
```
ls /home
```
it should show you your username, for example "hutchman". Then you type in
```
passwd hutchman
``` and it will ask you for the password twice. You will not be able to see what you are typing for extra security, but it is working. Then you should be able to reboot normally and log in with your username and new password.

---

### Post by hutchman on 2010-08-30
> **silverglade00 said:**
> If you go back to the root shell and type in
```
ls /home
```
it should show you your username, for example "hutchman". Then you type in
```
passwd hutchman
``` and it will ask you for the password twice. You will not be able to see what you are typing for extra security, but it is working. Then you should be able to reboot normally and log in with your username and new password.
Hey there, thanx. I just did it again so I would be sure to be accurate when I tell you what happens. It says "no working leases in presistant database - sleeping.
Give root password for maintenance
(or type Control- D to continue):" then when I type a password, or anything else, it moves down two lines printing the same last two lines.

---

### Post by hutchman on 2010-08-30
> **hutchman said:**
> Hey there, thanx. I just did it again so I would be sure to be accurate when I tell you what happens. It says "no working leases in presistant database - sleeping.
Give root password for maintenance
(or type Control- D to continue):" then when I type a password, or anything else, it moves down two lines printing the same last two lines.
oups, I left out a line which is "Login incorrect" then the same two lines. This is after I type "Control-D" then enter & even when I type "or type Control-D to continue" then enter

---

