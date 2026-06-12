---
title: "Logging to samba shares breaks vnc password authentication on Edgy 6.10"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by anolma on 2007-04-14
Hello,

I have this kind of scenario:

1. Vnc4server and Samba are running and I can log into Ubuntu box by Vnc client.
2. Ubuntu box has Samba in it and it uses samba user and samba password authentication and I can log into samba shares and move files etc.
3. After I have logged into samba and closed vnc client I cant reconnect with vnc withouth rebooting Ubuntu box. (Ssh connection works and samba shares continue to work.)

Im using vnc4server/edgy release begause this how-to succested that current vnc4server does not work begause of a bug:
[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

Samba is set by using this as a basis of installation:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)



So my question is where should I start to look up what is wrong?

Thanks for any help that you can provide.

---

