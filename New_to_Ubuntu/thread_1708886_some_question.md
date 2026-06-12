---
title: "some question"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by yashar3600 on 2011-03-17
hi
i want to know that how can i install vlc player and scilab on ubuntu 10.10?
i downloaded vlc and scilab from their web sites and exracted them but i do not know how to install them?
is there any pictorial guide or vivid guide?

i want install ubuntu 10.04.2LTS instead of ubuntu 10.10 but the windows installer wubi that i dowloaded from ubuntu.com just install ubuntu 10.10.
i download wubi for ubuntu 10.04.1 but this one try to download ubuntu 10.04.1 and do not install ubuntu 10.04.2 LTS.
what should i do?
thanks

---

### Post by vanadium on 2011-03-17
Use "Applications - Ubuntu software center" as much as possible to install software (including VLC and scilab). Fast, very easy, no searching and no chance to break your system.

---

### Post by uRock on 2011-03-17
Hello and welcome to the forums!
> **yashar3600 said:**
> hi
i want to know that how can i install vlc player and scilab on ubuntu 10.10? Both of these can be installed via the Ubuntu Software Center in you Applications menu.
> i downloaded vlc and scilab from their web sites and exracted them but i do not know how to install them?
is there any pictorial guide or vivid guide?Delete them and use the versions in the Ubuntu Software Center.

> i want install ubuntu 10.04.2LTS instead of ubuntu 10.10 but the windows installer wubi that i dowloaded from ubuntu.com just install ubuntu 10.10.
i download wubi for ubuntu 10.04.1 but this one try to download ubuntu 10.04.1 and do not install ubuntu 10.04.2 LTS.
what should i do?
thanksYou can use the 10.04.1 installer. Once you run updates it will become 10.04.2. The only difference between 10.04, 10.04.1 and 10.04.2 are a hand full of updates.

Cheers,
uRock

---

### Post by yashar3600 on 2011-03-17
thanks.
but i am curious to know how to install them without ubuntu software center.
and since i do not have unlimited and high speed internet connection i can not install softwares after each time that i reinstall my operating system.
overall i have to download softwares from internet via another system and then transfer them to my laptop
is there any guideline?

---

### Post by bcbc on 2011-03-17
> **yashar3600 said:**
> hi
i want to know that how can i install vlc player and scilab on ubuntu 10.10?
i downloaded vlc and scilab from their web sites and exracted them but i do not know how to install them?
is there any pictorial guide or vivid guide?

i want install ubuntu 10.04.2LTS instead of ubuntu 10.10 but the windows installer wubi that i dowloaded from ubuntu.com just install ubuntu 10.10.
i download wubi for ubuntu 10.04.1 but this one try to download ubuntu 10.04.1 and do not install ubuntu 10.04.2 LTS.
what should i do?
thanks
The wubi.exe on [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) is the incorrect release (10.04.1). This does not work anymore because there is no 10.04.1 available for download. Even if you have a 10.04.1 desktop ISO, wubi will still check online for the md5 sums and then fail because they are not available. (see [bug 722955]("https://bugs.launchpad.net/wubi/+bug/722955"))

So if you want 10.04, use the wubi.exe from here [http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe) 

It's better to download the 10.04.2 ISO yourself. 1) to reuse if required, and 2) to create a bootable CD or USB as a rescue disk, which is a good idea, even with Wubi. (If you download the ISO you can use the Wubi.exe on that as it's the correct version).

Finally, wubi is good for trying out Ubuntu, but keep important data backed up outside of Ubuntu (outside the virtual disk).

---

### Post by kaldor on 2011-03-17
> **yashar3600 said:**
> thanks.
but i am curious to know how to install them without ubuntu software center.
and since i do not have unlimited and high speed internet connection i can not install softwares after each time that i reinstall my operating system.
overall i have to download softwares from internet via another system and then transfer them to my laptop
is there any guideline?

This isn't Windows; you're supposed to use the Software Centre where possible.. much cleaner that way and easier to update without problems. When looking for non-software centre stuff, make sure you find a *.deb* file.

---

