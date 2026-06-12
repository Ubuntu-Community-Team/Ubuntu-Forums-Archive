---
title: "Software Updates"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Sunfist on 2011-04-26
I was wondering if there is a some way of telling, when a new version of a program comes out, how long it will be before it actually shows up as an update in the update manager? I am still running Firefox 3.6 (I believe) and version 4 has been available for a while now, just kind of wondering when it will show up as an update?

---

### Post by K_45 on 2011-04-26
Software in Ubuntu is frozen before its released and only security updates are sent through, i.e. Ubuntu is not a rolling release. If you want updated packages, you'll need to add repositories and/or PPA's like so:

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by qamelian on 2011-04-26
> **Sunfist said:**
> I was wondering if there is a some way of telling, when a new version of a program comes out, how long it will be before it actually shows up as an update in the update manager? I am still running Firefox 3.6 (I believe) and version 4 has been available for a while now, just kind of wondering when it will show up as an update?
Major version upgrades only occur when you update to a new release of Ubuntu. Within a specific release of Ubuntu, applications only receive critical bug fixes and security updates.

---

### Post by yetiman64 on 2011-04-26
For stability reasons most program versions are put on a "freeze" in each new release of Ubuntu. This means you will stay at version 3.6.x of firefox with your current install (btw. are you on Lucid your profile says 8.10 Intrepid ?).

There are the occasions when a newer version is made available to older releases via the "backports" repository, but I don't think that is the case with firefox (not sure though).

Another way to install version 4 of firefox is to enable the "stable" PPA (personal package archive) for it. Here is a [[COLOR=Blue]--link--[/COLOR]]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable?field.series_filter=") to the Mozilla stable PPA. Instructions to use it are on the page. Keeping the PPA installed and turned on will install and keep updated version 4 of firefox on your system.

---

