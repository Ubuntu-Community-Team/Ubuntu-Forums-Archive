---
title: "Log In Problem"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-04-16
Sometime back I installed "SKIM" and after sometimes when i rebooted and went inside, the log in screen reappears even after giving the password again and again! It is not going inside!

Please Help

Thank you

---

### Post by 1991sudarshan on 2011-04-16
???????

---

### Post by 1991sudarshan on 2011-04-16
!!

---

### Post by jtarin on 2011-04-16
It sounds as if you are inputting the wrong password.
Did you try uninstalling it to any affect?

---

### Post by 1991sudarshan on 2011-04-16
> **jtarin said:**
> It sounds as if you are inputting the wrong password.
Did you try uninstalling it to any affect?

Eventhough I gave correct password, it goes inside for a second and logs out immdiately and come to log in screen again and again!!

---

### Post by 1991sudarshan on 2011-04-16
**cat ~/.xsession-errors**

i tried this command and i got this command



[B]Xsession: X session started for kevin at Sat Apr 16 20:33:35 IST 2011
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Smart Common Input Method 1.4.9

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.9

Starting SCIM as daemon ...
SCIM has been successfully launched.
/home/kevin/.xsession: 4: kde-session: not found[/B]

---

### Post by jtarin on 2011-04-16
> **1991sudarshan said:**
> **cat ~/.xsession-errors**

i tried this command and i got this command



[B]Xsession: X session started for kevin at Sat Apr 16 20:33:35 IST 2011
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Smart Common Input Method 1.4.9

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.9

Starting SCIM as daemon ...
SCIM has been successfully launched.
/home/kevin/.xsession: 4: kde-session: not found[/B]

Do you have another Window manager to login with such as Fluxbox,XFCE? Login with one of those and try to repair your install.....or use the Live CD.

---

### Post by 1991sudarshan on 2011-04-16
> **jtarin said:**
> Do you have another Window manager to login with such as Fluxbox,XFCE? Login with one of those and try to repair your install.....or use the Live CD.

How to repair the install using Live cd?

---

### Post by richaoj on 2011-04-16
Boot options - choose repair installation.

---

### Post by 1991sudarshan on 2011-04-16
> **jtarin said:**
> Do you have another Window manager to login with such as Fluxbox,XFCE? Login with one of those and try to repair your install.....or use the Live CD.

I have installed fluxbox! it is going inside in the fluxbox mode! now tell me how to repair??

---

### Post by lykwydchykyn on 2011-04-16
Looks like you are trying to start kde by running "kde-session" from your .xsession script, rather than using the actually kde session .desktop file.

Which display manager are you using?  What is your session set to?

Did you install Kubuntu or install KDE on top of ubuntu?

Can you post the contents of ~/.xsession ?


AFAIK there is no such command as "kde-session"; the command to start kde has always been "startkde".

---

### Post by 1991sudarshan on 2011-04-17
Hey guys Found the solution for the problem! pls see this think

**[http://www.linuxquestions.org/questions/linux-newbie-8/kubuntu-gui-login-screen-reappears-875303/](http://www.linuxquestions.org/questions/linux-newbie-8/kubuntu-gui-login-screen-reappears-875303/)**


Thank you Everybody for your valuable suggestions

---

