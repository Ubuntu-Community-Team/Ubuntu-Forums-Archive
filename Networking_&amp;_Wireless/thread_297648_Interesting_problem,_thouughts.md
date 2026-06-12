---
title: "Interesting problem, thouughts?"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by Milambar on 2006-11-11
I just installed ubuntu-server 6.06LTS on an old thinkpad. The thinkpad does NOT have a wired ethernet port, networking is done entirely via wireless.

It has a 3com card, with a marvell 88w8335 chipset. This does not have native drivers (to my knowlege) but is reported to be working with ndiswrapper.

Now heres the problem.

How do I get ndiswrapper onto it, given that it cannot connect to the repo's as of yet.

Thoughts?

---

### Post by Milambar on 2006-11-11
Okay, I managed to resolve this myself. Heres how I did it.

On another machine that was connected to the net, and was running the same version of ubuntu, I did:
> 
sudo su -
apt-get clean
apt-get install -d ndiswrapper-common ndiswrapper-utils*
tar cvzf /media/usbdrive/ndis.tgz /var/cache/apt/archives/*.deb
sync


I then unplugged the memorystick and transferred it to the other computer, and extracted the files in the archive I'd just created to /tmp, then did..

> 
dpkg -i /tmp/*.deb


What amazed me, is it actually worked. That machine is now connected to the net, and working quite happily.

Note - The -d switch in the apt-get statement, tells it to download, but not install. That was the key here.

---

