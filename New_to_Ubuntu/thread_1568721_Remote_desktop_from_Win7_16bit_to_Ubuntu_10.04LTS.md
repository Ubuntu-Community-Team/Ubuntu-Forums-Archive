---
title: "Remote desktop from Win7 16bit to Ubuntu 10.04LTS"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by mark.tj on 2010-09-05
Can anyone help? Trying to set up a remote desktop from Windows to Ubuntu but I want it to work when the Ubuntu system is logged out so the user can connect then log into their own session. The only way I am able to connect at all is with Teamviewer but you have to be logged in already so this is no good. VNC refuses to connect at all due to "Security Types" but I don't know what that means. Could it be because my windows PC is 64bit and the Ubuntu one is 32? Currently I am attempting to connect across the LAN and both systems are connected to the same switch so should be no firewall issues.

---

### Post by Chesamo on 2010-09-06
It's not a firewall issue. The problem is that the VNC server that's installed on Ubuntu by default (Vino) doesn't start until a user is logged in, and refuses to do so unless you configure it otherwise.

1. Open Terminal. Run this command to uninstall the default VNC server for Ubuntu (don't worry, we'll install a different one in a second): ```
sudo apt-get purge vino
```

2. Still in Terminal, enter: ```
sudo apt-get install x11vnc
``` If this command fails, you'll have to run ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup && sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update
``` Then run the apt-get install command again.

5. Then type ```
gksudo gedit /etc/init.d/rc.local
```

6. Before the exit 0 line, enter this: ```
x11vnc -safer -localhost -once -nopw -auth /var/lib/gdm/:0.Xauth -display :0
```

7. Reboot, and test your new VNC server.

Let me know how this works out for you!

---

### Post by HermanAB on 2010-09-06
Hmm, VNC is mainly a good way to get your machine compromized - somewhat like Internet Explorer 6...

The usual way to do remote management of a Linux machine is with SSH.  It is secure and can do pretty much anything VNC does and much more.  You can use Xming and PuTTY on Windows.

---

### Post by mark.tj on 2010-09-06
Thanks for both replies I am currently working away (hence the need for remote access). I will try both options out on my return and report back here.

---

### Post by asmoore82 on 2010-09-06
> **HermanAB said:**
> Hmm, VNC is mainly a good way to get your machine compromized - somewhat like Internet Explorer 6...

A very poor generalization.

*When* security is an issue - which is *not* always the case,
VNC is easy tunneled over SSH.

---

