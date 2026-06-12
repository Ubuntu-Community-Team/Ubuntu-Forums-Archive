---
title: "GDM Screen not showing up"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by ajaydprabhu on 2009-04-19
Hi - I just started using Ubuntu 2 months back and i am in love with it.... But i guess i messed up with some services .... When i boot into Ubuntu 8.10 instead of showing the login screen i get "Not optimum mode - Recommended mode - 1280 * 1024 60 hz". I know if hass something to do with Screen resolution..If i do ctrl  + Alt + bck space it takes me to command line login. I tried to start the GDM from there but did not help...(sudo /etc/init.d/GDM start)

(This might help - Recently - I had disabled some services unknowingly. I believe GDM was one of them. Is there any way to enable services from command line).


pleeeeeeeeease help me get my login screen back....

---

### Post by muted1987 on 2009-04-19
have you tried to stop the gdm service first the restart it or you can try to reconfigure x using this command

sudo dpkg-reconfigure xserver-xorg

---

### Post by ajaydprabhu on 2009-04-19
Thanks for responding muted1987.......Let me try that and will get back to you.

---

### Post by ajaydprabhu on 2009-04-19
hi muted1987.. I get the below message after running the command suggested by you..
Xserver-Xorg postinst warning:overwriting possibly customised configuration file; backup in /etc/X11/Xorg.conf 20090419154242

Still i do not see the login screen. 

Also when i do a ctrl+alt+back sapce i get following message on screen 
kinit:no resume image
doing normal boot
* stopping firestarter firewall
acpid: client connected from 5957[0:0]

---

