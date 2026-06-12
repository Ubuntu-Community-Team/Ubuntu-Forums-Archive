---
title: "About /dev/net/tun permission"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by frankabel on 2007-05-20
Hi all!

How can I set the permission of  /dev/net/tun changing some  /etc/udev/rules.d/ file?

I can make:

sudo chown root.vboxusers /dev/net/tun
sudo chmod g+rw /dev/net/tun

and all is fine, Even I can put those commands in the /etc/rc.local script, but I just wandering the right way(some  change in the /etc/udev/rules.d/ files) of do that.

See  [http://www.debianhelp.org/node/4863](http://www.debianhelp.org/node/4863) before give some suggestion, there are a lot of suggestions that don't solve my problem.

Salute
Frank Abel

---

### Post by Pollywoggy on 2007-05-20
> **frankabel said:**
> Hi all!

How can I set the permission of  /dev/net/tun changing some  /etc/udev/rules.d/ file?

I can make:

sudo chown root.vboxusers /dev/net/tun
sudo chmod g+rw /dev/net/tun

and all is fine, Even I can put those commands in the /etc/rc.local script, but I just wandering the right way(some  change in the /etc/udev/rules.d/ files) of do that.

See  [http://www.debianhelp.org/node/4863](http://www.debianhelp.org/node/4863) before give some suggestion, there are a lot of suggestions that don't solve my problem.

Salute
Frank Abel

Take a look at this article:

[http://www.linux-mag.com/id/3015/](http://www.linux-mag.com/id/3015/)

You might have to register an account (it's free) in order to read the article.

---

### Post by breaking on 2008-01-21
Here's the "don't sell your soul by registering"-version:
[http://64.233.183.104/search?q=cache:8ze99Ms1uMsJ:www.linux-mag.com/id/3015+mastering+udev&hl=en&ct=clnk&cd=1](http://64.233.183.104/search?q=cache:8ze99Ms1uMsJ:www.linux-mag.com/id/3015+mastering+udev&hl=en&ct=clnk&cd=1)

Update:
The change you need to do in short:
Set the permission to persist across reboots, by editing as root /etc/udev/rules.d/20-names.rules and changing:
KERNEL=="tun",                          NAME="net/%k" 
to
KERNEL=="tun",                          NAME="net/%k",  GROUP="vboxusers",     MODE="0660"

---

