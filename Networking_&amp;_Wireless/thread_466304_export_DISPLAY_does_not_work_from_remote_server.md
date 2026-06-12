---
title: "export DISPLAY does not work from remote server"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by Petter72 on 2007-06-06
I have installed Ubuntu Feisty Fawn on my laptop. I use telnet to connect to another Unix machine, where I want to launch an X application, which GUI shall appear on my local screen.

On my laptop i type xhost +, on the server I type export DISPLAY=laptop-ip-address:0.0 and I have already removed the option -nolisten tcp in /etc/X11/xinit/Xserverrc.
Still, I cant ge any X application to launch from the server, I always get
 Error: Can't open display: ip-address:0.0

Any ideas what might be wrong ?

Thanks

Petter

---

### Post by Mr. C. on 2007-06-06
See: [http://ubuntuforums.org/showthread.php?t=446725&highlight=xhost&page=2](http://ubuntuforums.org/showthread.php?t=446725&highlight=xhost&page=2)

---

### Post by Petter72 on 2007-06-07
Thanks a bunch, doing System->Admin->Login Window in the tab Security uncheck 'Deny incoming TCP connections' did it !!!!

---

### Post by netztier on 2007-06-07
> **Petter72 said:**
> Thanks a bunch, doing System->Admin->Login Window in the tab Security uncheck 'Deny incoming TCP connections' did it !!!!

What you also could've done: Use SSH instead of telnet and launch it with the -X option:

```
ssh -X yourlogin@remotehost
```

If the remote server supports X11 forwarding, this will automatically configure the $DISPLAY variable on the remote system and create port forwarding configuration for X11.

Like this - and this is the main security advantage - your local X server would see the X connection coming from localhost, and you don't have to open the "incoming TCP connections".

best regards

Marc

---

