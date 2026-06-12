---
title: "Constant Flash Problems in FFox"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-10-30
Hi all,

I've scoured the forums and Google for information on how to fix my ongoing Flash problems in Firefox, but am fruitless thus far.  It's misbehaving not only for flash videos, like on Youtube, but also for a lot of sites that, I presume, use flash (such as some sites that I need to use for online classes). Here's what I've done so far:

Installed the Flash Player .deb package from flash.com
Installed the flashplugin-nonfree package
Tried flash in a different browser (Opera).  It DOES work (for the most part) in Opera, and it's what I use whenever I need to view something in Flash as of right now...but I'd prefer FFox.
Installed Gnash as a last desperate attempt.

I'm not sure where I should go from here.  In FFox, my about:plugins page reads as so:

**MIME Type:** application/x-shockwave-flash **Description:** Adobe Flash Movie  **Enabled:** Yes
**MIME Type:** application/futuresplash  **Description: **Futuresplash Movie  **Enabled:** Yes

Any suggestions?

EDIT:  I'm running (I think) 32bit.  ("uname -m" gives me i686)

---

### Post by kansasnoob on 2009-10-30
You didn't mention which version of Ububtu you're using. Please post the output from terminal of:

```
cat /etc/issue
```

---

### Post by Wataru8675 on 2009-10-30
Crud!!  So much for my attempt at a thorough description of my problem...  I'm running Jaunty 9.04...which is what I'm presuming you wanted from cat /etc/issue.

---

### Post by lovinglinux on 2009-10-30
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by Slave2Metal on 2009-10-31
I'm new to linux and ran into this as well.  Ended up removing version 3.0, removing one of the plugins, swfmozilla gnash I believe, and installed 3.5.3. Sorry, but I do not recall any more, other than having two firefox versions installed at the same time.  Works fine for all flash content so far. Not quite sure which plugin I removed though.

---

### Post by Wataru8675 on 2009-10-31
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

You're my new hero.  Also, I'm bookmarking this thread for future reference......

---

### Post by lovinglinux on 2009-10-31
> **Wataru8675 said:**
> You're my new hero.  Also, I'm bookmarking this thread for future reference......

:)

---

