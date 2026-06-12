---
title: "Samba &amp; Nautilus"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by tebbens on 2008-05-28
I don't understand where and how Samba works via Nautilus.

In Nautilus when I share a folder where is that config stored/saved ?
Do changes to /etc/samba/smb.conf override Nautilus settings ?

How does Nautilus work with Samba....???

Thanks,
Matthew

---

### Post by jetsam on 2008-05-29
I was just completely confused by this as well and looked into it a bit.  

The nautilus-share package contains the nautilus extension that handles this.  It creates "samba usershares", which are defined in the **/var/lib/samba/usershares** directory and not in the smb.conf.  Normal shares that _are_ defined in the smb.conf still work like they should.  Shares made through the gui no longer appear in the smb.conf, unless you use a different config tool like system-config-samba or SWAT.  

There's more info here:
[http://64.233.167.104/search?q=cache:cT6uqgD_JIwJ:gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php%3Ftitle%3DAccueil%26redirect%3Dno+site:gentoo.ovibes.net+nautilus-share&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a]("http://64.233.167.104/search?q=cache:cT6uqgD_JIwJ:gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php%3Ftitle%3DAccueil%26redirect%3Dno+site:gentoo.ovibes.net+nautilus-share&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")

...which is the Google cache of this website, the (at the moment, broken) homepage of the nautilus-share extension:
[http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/]("http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/")

It seems like it may take a while to work out the kinks in Hardy's take on Samba.

---

