---
title: "Can you use Ubuntu 10.04 Desktop as a server"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-05-03
I was trying to make an Ubuntu server. I didn't want to install the Server Edition because I'm not that good with the command prompt, so I was wondering if I could use the Desktop Edition as the same way.

---

### Post by Primefalcon on 2010-05-03
Sure it's just not recommended since the gui uses extra resources, I have one set up on this machine as a dev enviro actually for testing

just search synaptic for apache2, php5, mysql-server and phpmyadmin and you should be well setup

---

### Post by theweasel2345 on 2010-05-03
What extras would you recommend uninstalling?
and also what kind of server do you run?

---

### Post by jcwmoore on 2010-05-03
install apache and you have an instant web server.  openoffice.org is probably the first thing that I would remove if you want your desktop install to be strictly a server.

---

### Post by readycarpenter on 2010-05-03
or just install the server version, then run sudo apt-get install ubuntu-desktop


or on desktop version run sudo apt-get install ubuntu-server



both versions are the same, except they are packaged with different apps, desktop version comes with all the basic desktop apps, while the server edition has all the basic server apps and no desktop after you get all configured through the desktop, you can easily disable the desktop.

here is a good article 
[http://ubuntuforums.org/showthread.php?t=195070](http://ubuntuforums.org/showthread.php?t=195070)

cheers

---

### Post by GSF1200S on 2010-05-03
It depends on what kind of server you want to setup. I have my primary desktop setup with ssh. Basically, this allows me to access my desktop from remote locations (at school for me) from my netbook using the desktop as a file server. If a file server is all you need, you can install ssh:
```
sudo apt-get install ssh
```
and then start it:
```
sudo /etc/init.d/ssh start
```
ssh also allows you to control the computer remotely. I can update, reboot, run apt commands, scripts, or even use X11 forwarading (which opens GUI apps running on my desktop on the remote client) from a remote client. ssh is also encrypted and far more secure than using ftp for instance.

---

### Post by rabidcentipede on 2010-05-03
How much ram/HD space does your computer have?

Unless you have a bunch of stuff running at once, it probably won't matter that much whether you uninstall the random "extras" that come with the Desktop version.

But, as others have said, php, ssh, apache, and mysql would be the main things that I would set up.

---

### Post by 3rdalbum on 2010-05-04
I have an Atom machine with 1gig of RAM, running Ubuntu Desktop as a file/torrent server. So yes, Ubuntu Desktop is just Ubuntu Server but with a GUI.

---

### Post by theweasel2345 on 2010-05-04
I have a hp with a pentium 4 and 512k ram. How do I find my http proxy

---

### Post by I12crash on 2010-08-12
Unless you are using a proxy you would just leave it blank.

---

### Post by bodhi.zazen on 2010-08-12
> **theweasel2345 said:**
> I was trying to make an Ubuntu server. I didn't want to install the Server Edition because I'm not that good with the command prompt, so I was wondering if I could use the Desktop Edition as the same way.

This is an old thread.

A graphical desktop is, IMO, of little or no use on a dedicated server.

You can certainly run services on a Desktop, apache, samba, nfs, ftp, ssh, etc. There is nothing wrong with doing that on a LAN.

But if you are running a dedicated server, or if you are allowing access from the internet (port forwarding) I would strongly advise you reconsider.

First off, the more applications you have the more potential vulnerabilities.

Second, Gnome / KDE / XFCE are not very conducive to server management. Most of server management is stating / stopping services and editing configuration files, which can be done without X.

If you want a graphical interface look at web tools such as webmin, phpmyadmin, etc.

---

