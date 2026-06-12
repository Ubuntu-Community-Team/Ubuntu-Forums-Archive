---
title: "uninstall specific updates"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by oh my on 2009-08-21
Hi,

I would like to uninstall one specific update. Is that possible?

I updated my xorg-xserver-video-intel two weeks ago and since then my PC freezes when I use desktop effects. I would like to uninstall that update (and freeze the package) to be able to use my PC again.

regards

---

### Post by ajgreeny on 2009-08-21
If you use synaptic, highlight the package and in the properties of that see if a previous version is still available.  If so try Package > Force Version from the menus.  Certainly in my system there are two versions available.

---

### Post by oh my on 2009-08-21
Hi,

thanks, that will certainly come in handy in time. :)

Sadly I only have one version listed in that menu, so I can not use it. :(

regards

---

### Post by slakkie on 2009-08-21
You could try pinning. Let me explain this with the curl package:

```

curl:
  Installed: 7.18.0-1ubuntu2
  Candidate: 7.18.0-1ubuntu2.2
  Version table:
     7.18.0-1ubuntu2.2 0
        500 http://nl.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
 *** 7.18.0-1ubuntu2 0
        500 http://nl.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

```

In order for me to stay at this version, I need to pin curl at this particular version. You do this in the preferences file, which is stored in /etc/apt/preferences:

```

Package: curl
Pin: version 7.18.0-1ubuntu2
Pin-Priority: 1001

```

Now, when I run apt-cache policy again you will notice that I it will not upgrade:

```

 apt-cache policy curl
curl:
  Installed: 7.18.0-1ubuntu2
  Candidate: 7.18.0-1ubuntu2
  Package pin: 7.18.0-1ubuntu2
  Version table:
     7.18.0-1ubuntu2.2 1001
        500 http://nl.archive.ubuntu.com hardy-updates/main Packages
        500 http://security.ubuntu.com hardy-security/main Packages
 *** 7.18.0-1ubuntu2 1001
        500 http://nl.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

```

If you already upgraded to a newer version, you can remove the package and then install it again, it will select the correct version. For more information about pinning: 

[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

### Post by oh my on 2009-08-21
Hi,

awesome, thanks! 
That is exactly what I was looking for. :)

regards

---

