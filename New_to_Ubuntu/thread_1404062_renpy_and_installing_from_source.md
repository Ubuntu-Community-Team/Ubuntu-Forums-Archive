---
title: "renpy and installing from source"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-02-11
So, renpy crashes on karmic. However, I noticed on renpy's site that its an older version. They have the newer version but just as a .tar file. Is there an easy way to turn it into a .deb?

---

### Post by yeats on 2010-02-11
> So, renpy crashes on karmic.

Do you want to get more specific about what's crashing?  Perhaps the problem is something specific to your system that can be troubleshot and fixed.

> However, I noticed on renpy's site that its an older version.

The repo versions of software will always be at least a point version or two behind (depending on the release cycle of the program).  The website version will be newer, especially since karmic was released a few months ago.  This is to ensure a stable system.  Newer versions will likely be put in the next release.

> They have the newer version but just as a .tar file. Is there an easy way to turn it into a .deb? 

No - that's not the way you'd want to go.  You might want to do some reading about [installing software on Ubuntu]("https://help.ubuntu.com/community/InstallingSoftware"). 

If I were you, I would try and figure out why the program is crashing as opposed to trying to install the new version.

---

### Post by LunaticHiatus on 2010-02-11
I already did a bug report awhile ago and I was informed it was a fault with the program, not with how ubuntu was running it. Either way, I ran the new source and it runs fine. But I don't care for installing stuff from source and figured it would be handy to have a .deb around for friends and whatnot

---

### Post by mcduck on 2010-02-11
> **LunaticHiatus said:**
> I already did a bug report awhile ago and I was informed it was a fault with the program, not with how ubuntu was running it. Either way, I ran the new source and it runs fine. But I don't care for installing stuff from source and figured it would be handy to have a .deb around for friends and whatnot

When compiling programs from source you can use checkinstall to turn it into .deb packages.

Just smake sure you have checkinstall installed, and then when compiling, instead of "*sudo make install*" use "*sudo checkinstall*". That will create a .deb package for you and then install that through the package maangement, making the compiled program easy to uninstall if you need to.

But be aware that checkinstall doesn't make "correct" .deb packages, it doesn't add information about dependencies etc, so if you want to use the same .deb package on another system you ened to make sure you ahve insatlled are dependencies manually beforehands. For thta reason .deb packages made with checkinstall are not usually suitable for public distribution (apart from very small apps that have no dependencies).

Making proper .deb packages is a bit more involved process. :)

---

