---
title: "Privoxy installation question"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-08-08
Privoxy is supposed to be installed as a user, however, it wants to install to /usr/local/etc/ which is owned by root. I'm "assuming" this area is owned by root for a reason and don't want to just blindly change the permissions. Is it ok to do so or am I missing something?

---

### Post by bodhi.zazen on 2010-08-08
What makes you think privoxy should be installed as a user ?

```
sudo apt-get install privoxy
```

Then edit the config file (gksu gedit /etc/privoxy/config ) and change the line "listen-address localhost:8118" to ```
listen-address 127.0.0.1:8118
```

And restart privoxy

```
sudo service privoxy restart
```

Although privoxy is called as root, the init script will change the user and group to privoxy.

If you wish to further secure privoxy, use apparmor.

Here is a link to my apparmor privoxy profile :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.sbin.privoxy](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.sbin.privoxy)

---

### Post by Rumpletumbler on 2010-08-08
Thank you. I'll try that. 

I read it here. 

[http://www.privoxy.org/user-manual/installation.html#INSTALLATION-DEB](http://www.privoxy.org/user-manual/installation.html#INSTALLATION-DEB)

> You should configure/install/run Privoxy as  an unprivileged user, preferably by  creating a "privoxy" user  and group just for this purpose.  

---

### Post by bodhi.zazen on 2010-08-08
> **Rumpletumbler said:**
> Thank you. I'll try that. 

I read it here. 

[http://www.privoxy.org/user-manual/installation.html#INSTALLATION-DEB](http://www.privoxy.org/user-manual/installation.html#INSTALLATION-DEB)

The Ubuntu package maintainers (MOTU - Masters of the Universe) take care of those issues for you (init scripts, configuration files, and changing the effective user/group to privoxy).

---

### Post by Rumpletumbler on 2010-08-08
Thanks again for the help and the config file. 

I had initially installed via the software center but it installs 3.0.15-3 which is a beta released in Oct of 2009 it appears. 

I was after 3.0.16 which came out in February of this year and shows as stable. I downloaded it and was fumbling with the installation per my first post.

I "assume" that apt-get and the software center use the same repository's as it shows the currently installed version is the latest version which of course really isn't. 

That's something else to chase down. I have lots to learn but am enjoying it.

---

### Post by bodhi.zazen on 2010-08-08
You are probably fine with that version.

You could try the .deb from privoxy, but you may need to manually configure privoxy after.

---

