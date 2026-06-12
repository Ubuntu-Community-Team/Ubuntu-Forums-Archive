---
title: "OpenSSH"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by meddyliol on 2009-01-20
Hi, I am running Ubuntu 8.04 and I would like to have a remote access facility so that I can configure my Son's Ubuntu remotely. I have read that OpenSSH can be used. Looking at some of the download sites I have downloaded two files:
OpenSSH-2.1.1p4-vs-openbsd.diff.gz 

and

OpenSSH-2.1.1p4.tar.gz

Are these the correct files? If so, how do I install them?

Thanks

Brian :)

---

### Post by sankarv on 2009-01-20
jus search for openssh from the package manager in ubuntu, u can right click and install it, its the most easiest way to install the same...


btw u can unzip those filea and if its source code then inside the unzipped dir path, from terminal run ./configure, make, make install to install the same....


however the former method is simpler for any package which is already in the ubuntu package repository..

---

### Post by nothingspecial on 2009-01-20
```
sudo apt-get install ssh
```

---

### Post by meddyliol on 2009-01-20
I have searched for openssh in the package manager but nothing came up.

:)

---

### Post by nothingspecial on 2009-01-20
Like I said, you need the package ```
ssh
```

---

### Post by meddyliol on 2009-01-20
I have tried running 'sudo apt-get install ssh', am I supposed to see something happening? because nothing appears to. Sorry for being so stupid (with Linux) but I am trying to learn. By the way, what is a good book for beginners, must be in simple language if you get my drift.

Thanks in anticipation

Brian :popcorn:

---

### Post by nothingspecial on 2009-01-20
did it not ask for your password? type it in, you wont see it then hit enter.[URL="http://linuxcommand.org/"][COLOR="Red"]

Good place for to learn[/COLOR][/URL]

---

### Post by eightmillion on 2009-01-20
The package isn't called 'ssh'. There are two packages, 'openssh-client' and openssh-server'. The client package allows you to connect to other computers over ssh. The server package allows others to connect to you over ssh.

> sudo aptitude install openssh-client openssh-server

Edit: There is an ssh package. That's news to me.

> Description: secure shell client and server (metapackage)
 This metapackage is a convenient way to install both the OpenSSH client
 and the OpenSSH server. It provides nothing in and of itself, so you
 may remove it if nothing depends on it.

---

### Post by tarps87 on 2009-01-20
It should request you password if the package is correct, if your not try running it in the terminal so you can see the output.
Try looking at:
[https://help.ubuntu.com/8.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.10/serverguide/C/openssh-server.html)
This is the one I used to help me set up my server, it also includes the installation and setup.

I would suggest using the documentation here:
[https://help.ubuntu.com/](https://help.ubuntu.com/)
and this forum as Ubuntu develops quickly (6 month release cycle) it doesn't take long for the books to get out of date, but I'm sure if you want someone will be able to recommend one

---

### Post by meddyliol on 2009-01-20
Thanks to everyone and to the links that tarps87 gave.

I will take it all on board and have a go at this remote access malarkey.

Thanks

Brian :)

---

### Post by nothingspecial on 2009-01-20
> **eightmillion said:**
> The package isn't called 'ssh'. There are two packages, 'openssh-client' and openssh-server'. The client package allows you to connect to other computers over ssh. The server package allows others to connect to you over ssh.



Edit: There is an ssh package. That's news to me.
```


 apt-cache search ssh
backuppc - high-performance, enterprise-grade system for backing up PCs
bzr - easy to use distributed version control system
gftp-common - shared files for other gFTP packages
gftp-gtk - X/GTK+ FTP client
gnome-keyring - GNOME keyring services (daemon and tools)
ldm - LTSP display manager
ldm-ubuntu-themes - Themes for the LTSP Display Manager
libcryptui-dev - the UI library for DBUS functions exported by seahorse (development)
libcryptui0 - the UI library for DBUS functions exported by seahorse
libgnome-keyring-dev - Development files for GNOME keyring service
libgnome-keyring0 - GObject bindings for PKCS#11
libgp11-0 - GNOME keyring services library
libgp11-dev - Development files for the PKCS#11 GObject bindings
libjsch-java - java secure channel
libjsch-java-doc - java secure channel examples
libndesk-dbus-glib1.0-cil - CLI implementation of D-Bus (GLib mainloop integration)
libndesk-dbus1.0-cil - CLI implementation of D-Bus
libpam-gnome-keyring - PAM module to unlock the GNOME keyring upon login
libpam-opie - Use OTPs for PAM authentication
openssh-blacklist - list of default blacklisted OpenSSH RSA and DSA keys
openssh-blacklist-extra - list of non-default blacklisted OpenSSH RSA and DSA keys
openssh-client - secure shell client, an rlogin/rsh/rcp replacement
openssh-server - secure shell server, an rshd replacement
python-paramiko - Make ssh v2 connections with python
python-twisted-conch - The Twisted SSH Implementation
seahorse - A Gnome front end for GnuPG
seahorse-plugins - seahorse plugins and utilities for encryption in GNOME
[COLOR="Red"]ssh - secure shell client and server (metapackage)[/COLOR]
```

There it is at the bottom in red.

******EDIT*****Oooops didn`t see your edit untill I`d posted******EDIT******

---

### Post by JaJaBinks on 2009-01-21
Open a terminal window (Applications> Accessories> Terminal)
type code: sudo apt-get install openssh-server openssh-client

after entering your password, they will be downloaded and installed

---

### Post by theozzlives on 2009-01-21
> **meddyliol said:**
> I have tried running 'sudo apt-get install ssh', am I supposed to see something happening? because nothing appears to. Sorry for being so stupid (with Linux) but I am trying to learn. By the way, what is a good book for beginners, must be in simple language if you get my drift.

Thanks in anticipation

Brian :popcorn:

I like tech manuals, but the first book I read was Ubuntu Linux Bible... Amazon has one for 8.10

---

### Post by Bölvaður on 2009-01-21
openssh-client is default on 8.10, so it should be already on your computer.
but openssh-server needs to be installed on the target computer.

You can install via System &#8594; Administration &#8594; Synaptic Package Manager
or just "sudo apt-get install openssh-server" and type in your password (note that you will not get any feedback while typing, you have to press enter to know if you typed the password correctly)

---

