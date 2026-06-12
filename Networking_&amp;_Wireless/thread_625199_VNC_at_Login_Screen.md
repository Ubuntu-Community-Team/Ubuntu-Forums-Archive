---
title: "VNC at Login Screen"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by Danikar on 2007-11-27
Currently I am at work, I reboot my machine at home and now I can not VNC into it.

I just used the one that is built into Ubuntu.  My assumption would be is because it is sitting at the login screen and maybe it only accepts connections when you are logged into your desktop.

Is there a way to set it up so that I can either log it in though SSH. Or, make it so it will accept VNC connections at the login screen?

---

### Post by Jose Catre-Vandis on 2007-11-27
Search the forum for [COLOR="Sienna"]VNC with resumable sessions[/COLOR]. This will show you how to VNC to the gdm.

If you want to login via ssh you will need to install openssh-server on your home machine first, then use ssh or putty (on Windows) from work.

---

### Post by Danikar on 2007-11-27
Yeah I already set up SSH on the computer, thanks for the information.  I'll look at that now.

---

### Post by Danikar on 2007-11-27
I followed the how to on setting it up here.

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Now when I try connecting, ipaddress:1 I get an error

"ReadExact: Socket error while reading"

Still playing with it, but im stuck. =(

---

