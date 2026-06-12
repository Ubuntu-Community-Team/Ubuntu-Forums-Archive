---
title: "Ubantu telnet session"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by rohangaur on 2011-05-09
Hello 

I am new to **Ubantu. 10.10 ** and I have configured the HYPER V virtualisation and installed the three ubantu operating system on it, Then I installed the **TELNET **server on it and made the users. When users try telnet to ubantu only three four connection are established and even thoese connection get **hanged even their DELETE AND BACKSPACE key does not work.**

Pls could somebody tell me how to configure it so that our users are able to connect to the ubantu without any problem and work upon UNIX.

any help appreciated

Regards

Rohan Gaur
System Administrator

---

### Post by taseedorf on 2011-05-11
Don't use telnet.  Use ssh.

---

### Post by kaldor on 2011-05-11
> **taseedorf said:**
> Don't use telnet.  Use ssh.

Or VNC if you need a GUI.

To install SSH, run this in terminal:

```
sudo apt-get install openssh-server openssh-client
```

You also have a few GUI options. PuTTY on Windows lets you connect via SSH to Ubuntu in a GUI.

---

### Post by seawolf167 on 2011-05-11
> **kaldor said:**
> or vnc if you need a gui.

To install ssh, run this in terminal:

```
sudo apt-get install openssh-server openssh-client
```you also  have a few gui options. Putty on windows lets you connect via ssh to  ubuntu in a gui.


+1, telnet is *way* insecure

---

### Post by lugoteehalt on 2011-05-11
Yes, telnet is insecure silly.  It should be uninstalled.

---

