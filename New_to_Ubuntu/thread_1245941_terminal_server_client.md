---
title: "terminal server client"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by CapitanYochua on 2009-08-21
I'm trying to use Terminal Server Client to connect to another computer that is running on linux. How should I do this exactly? From what I understand, RDP is for windows systems. But Terminal Server Client doesn't seem to allow me to change to VNC protocol. How exactly should I get this working?
Thanks for any help.

---

### Post by bchurchill on 2009-08-21
I don't know much about terminal server client, but if you're trying to troubleshoot problems the obvious things to check are that you have a good network connection (use ping), that your authentication is working right and firewalls are configured appropriately.


SSH allows you to login to a bash shell remotely.  I'm pretty sure this is the standard way of doing what you're trying to do.  Putty makes a good client on windows, and on the Ubuntu computer you can install the SSH server with 

```

sudo apt-get install openssh-server

```

I highly recommend modifying the configuration to make it secure on your computer.  See [https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html) for more details.

---

### Post by XCan on 2009-08-21
> **CapitanYochua said:**
> I'm trying to use Terminal Server Client to connect to another computer that is running on linux. How should I do this exactly? From what I understand, RDP is for windows systems. But Terminal Server Client doesn't seem to allow me to change to VNC protocol. How exactly should I get this working?
Thanks for any help.

You can enable the VNC feature by installing xvnc4viewer first. It is more bandwidth friendly, but still sucks compared to tightvnc on Windows (yes I know xtightnvcviewer exists, but the interface is nothing like Windows').

---

### Post by CapitanYochua on 2009-08-21
Okay, Thanks. So I am able to select the VNC protocol now but I'm getting "connection refused" when I try to connect. How do I go about fixing this?
Sorry, I've never used a remote desktop before.

---

### Post by XCan on 2009-08-21
You need to setup a vnc server first on the host machine. However, it is debatable how VNC is by itself in Ubuntu's standard configuration. When you enable it, don't forget to set a password. Also, it is adviced that you change the standard port if you don't want to connect to it through an SSH tunnel.

You can enable VNC (if you're using Ubuntu) in System -> Pref. -> Remote Desktop. You can change the standard port by typing

```
 gconf-editor 
```
and browsing to desktop -> gnome -> remote_access

---

