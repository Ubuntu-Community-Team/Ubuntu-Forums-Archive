---
title: "Ubuntu Repositorys in Debian?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by penguin-of-doom on 2009-06-11
Hey,
I have used Ubuntu for a long time. I think it's really good.  But then I switched to Debian and I think it's better. But there is one thing i hate on debian. There are very old Programs in the repositorys and I'm too lazy to build the source of the programs. That takes too long. So how can I do the Repositorys of Ubuntu to Debian? I'm looking forward to your answers!

regards,
penguin-of-doom

---

### Post by Lampi on 2009-06-11
I guess you are referring to debian/stable, right? These package are "old" because the maintainers are using much more time and effort for code cleanup, bug fixing and so on (it's what they call "freeze") So these packages will be more stable and reliable than ubuntu packages will be.

If you're interessted in a "newer" debian it's best to use another release than stable.

[http://www.debian.org/releases/](http://www.debian.org/releases/)

I'd go for debian/testing - many packages will work fine, some might need  more code cleanup in order to run stable.

In the debian sense stable means "rock solid" - it's what you'd like to use in a productive server environment. You can't use buggy packages there.

---

### Post by penguin-of-doom on 2009-06-11
thank you for your answer...
but I think it would be better if in the repositorys are for example OpenOffice 3 and not the old OpenOffice 2... The same is with GIMP... I think I have to install this packages from the source ;)

regards,
penguin-of-doom

---

### Post by reeseslover531 on 2009-06-11
Which version of debian do you have installed? stable, as Lampi said, is very old you probably want to run testing or if you want to be even more on the edge, unstable.  I recommend trying that out.

---

### Post by penguin-of-doom on 2009-06-11
I am using Debian 5 Lenny... It's the newest stable yet... but can I include some repositorys e.g. for openoffice 3 or GIMP the newest stable version? OpenOffice 3 is stable, and I have installed 2.4...

regards,
penguinof-doom

---

### Post by reeseslover531 on 2009-06-11
so this is something that you should be asking in the debian forums really but your answer is [here]("http://forums.debian.net/viewtopic.php?t=33022").  Even though you are running the latest stable, the latest stable "froze" the packages a while ago which is why things are so old, you might want to change to testing or experimental.

---

### Post by Lampi on 2009-06-12
@penguin-of-doom: You are lucky! go tho the website of openoffice.org and click your way through their download site. You will find the latest open-office 3.1 as precompiled debian binaries available for download.

- Make sure you uninstall the open-office in lenny first
- download the tar archive with the debian binaries
- unpack it and use dpkg -i *.deb in the directory you unpacked the files

This runs just fine with me on Debian/Lenny, you might find precompiled deb packages on the gimp download website as well :)

---

### Post by penguin-of-doom on 2009-06-12
thank you!
But there are so many .deb files in the Binary... Have I all to dpkt -i it?

regards,
penguin-of-doom

---

### Post by Lampi on 2009-06-12
> **penguin-of-doom said:**
> thank you!
But there are so many .deb files in the Binary... Have I all to dpkt -i it?
Yes - this is common in debian - especially with a large suite like Openoffice: you split the suite into packages to make updates easier, otherwise you would have to update the whole suite.

Here is a step by step howto to walk you trough:

[list][*]open a terminal and change to the directory you unpacked the archive.[*]Then become root (type: "su" - enter root password)[*]remove the Open Office Installation of Lenny: Type: "apt-get remove openoffice*.*"[*]now install the deb archives: type: "dpkg -i *.deb"[*]there is a subdirectory - it includes a single deb file with all the OO menu entries - you want to install this one as well with "dpkg -i <paketname>.deb"[/list]
that's it! You are finished - have fun with OO 3.1!

---

### Post by snowpine on 2009-06-12
You picked the wrong distro for your needs. Debian Lenny is not designed for "lazy" people who want recent versions of applications. It's designed for situations like corporate servers where stability is the #1 priority. I would recommend upgrading from Lenny to Squeeze (testing) or better yet switching back to Ubuntu (so you can use the Ubuntu repositories).

---

### Post by penguin-of-doom on 2009-06-12
Hey,
thank you for your answers :D
I wanted to install all packages with one step, because there are problems with my GDEbi Package installer. I tried it via terminal, but this doesn't work...
is there a way to install all .debs with one step?

regards,
penguin-of-doom

---

### Post by Lampi on 2009-06-12
just tell us what you did exactly - the howto I gave you should work it you stick to it.

---

### Post by dawynn on 2009-06-12
Let's see -- some time ago, there was a huge discussion as to how Debian could be more responsive, and more up-to-date.  It came after like a 3-year time period from one "stable" version to the next.  Many ideas were proposed, including removing several of the archaic platforms from Debian.

In the end, nothing really happened to Debian itself, but Ubuntu was born, focusing specifically on i386 based machines, and a very limited set of packages (yes the Ubuntu folks still compile the "Universe" and "Multiverse" packages, but "Main" and "Restricted" are the core packages that they truly "support").  Now, instead of taking 3 years to make a new stable release, Ubuntu, with fewer packages and systems to support, can make a new stable release in 6 months.  (This may not truly reflect how Ubuntu came to be, but if its not, several colliding coincidences would lead certain people to believe, this is how Ubuntu was born)

For what its worth, if you choose to go Debian over Ubuntu --

**Choose "stable"** if you like a rock-solid, never-crash system, but expect packages to be very old by the time they even reach "stable".  Expect to see very few updates between stable releases.

**Choose "testing"** if you like fairly current packages, with very little breakage.  Expect to see a steady flow of updates, except for the "freeze" periods when they are preparing a new "stable" system.  Then expect that packages will go stale for 3 - 6 months.

**Choose "sid"** if you want the bleeding edge.  Expect to see breakage.  This is even publicized by the Debian community -- there's a reason they call this "sid" (remember Toy Story).

If you're concerned about specific packages -- look at the webpages for those particular packages.  Or even search around a bit.  Some packages have their own specific repositories.  For instance, you could use the main Ubuntu repositories for most of your software, but have separate repositories for Open Office, Opera, Wine, and several other tools that slip my mind at the moment.

Remember that Ubuntu is Debian-based, and contributes back to the Debian community.  For the most part, .deb resources are mostly compatible between the two systems.  It is recommended that you not combine both the Ubuntu and Debian repositories in your sources.list, as there is some incompatibility between core packages of the two systems, but many 3rd-party deb repositories that work with Debian will work just as well with Ubuntu and vice-versa.

This is Linux.  It's your system.  There is no MS style "Genuine Linux" validation when you install anything.  You're free to mix and match repositories as you wish.  When you have a choice, try to stick with the repositories that most closely align with your system.  Since it is your system, you're responsible for the consequences of your actions.

---

### Post by Lampi on 2009-06-13
> **dawynn said:**
> Let's see -- some time ago, there was a huge discussion as to how Debian could be more responsive, and more up-to-date.  It came after like a 3-year time period from one "stable" version to the next.  Many ideas were proposed, including removing several of the archaic platforms from Debian.
Is this when they decided to start "half time distros" like etch'Nhalf? I thought this was a great idea, cuz with the release cycles of debian/stable it's hard to keep up with current hardware. But then again: you can always compile current alsa from source if your soundchips is not supported on lenny.

---

