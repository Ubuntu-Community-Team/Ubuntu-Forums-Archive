---
title: "Installing ubuntu on a nas?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by zerobinary on 2011-03-08
I am just wondering is it possible to install Ubuntu on Synology ds107e?
I mean this nas is running a miniature version of linux!

---

### Post by kellemes on 2011-03-08
> **zerobinary said:**
> I am just wondering is it possible to install Ubuntu on Synology ds107e?
I mean this nas is running a miniature version of linux!

No, Ubuntu is much too heavy..
The Synology nas's are running a heavily tweaked version of Debian, afaik.
If you really need to install another version of Linux on your NAS you should probably focus on more basic and flexible distro's like Debian, Gentoo or maybe Arch..

---

### Post by aeiah on 2011-03-08
if its already running debian then why do you need ubuntu on there? to be honest you wouldnt notice any difference on something like a NAS. can you install things with apt-get like a normal debian install? that'd be the best way to go.

---

### Post by mcduck on 2011-03-08
Assuming it has an x86-compatible CPU, it might be ale to run a minimal/server Ubuntu install.

The Desktop version is out of the question, and switching it to Ubuntu probably wouldn't really benefit much, like above posters pointed out.

---

### Post by kellemes on 2011-03-08
> **aeiah said:**
> can you install things with apt-get like a normal debian install?

Most is done through the best GUI I've ever seen on a NAS.. there is a very cool package-manager with a growing list of packages.
From cli you can use [ipkg]("http://en.wikipedia.org/wiki/Ipkg").

---

### Post by aeiah on 2011-03-08
well, if you can install apt-get on it and edit the sources.list file to point to debian repositories, you've basically got the same options as ubuntu. i dont think there's anything in the ubuntu repos that isnt in the debian repos and the structure of everything is almost identical, especially on such a stripped down system.

it may be more trouble than its worth to use apt-get and sources if it isn't designed for it. i guess once you've got NFS, bittorrent and maybe mpd running on it there isnt much else to do anyway?

---

### Post by Nullius on 2012-07-05
Well, actually (I'm posting this for others that come across this topic through search engines), it isn't running Debian.
Synology made their own distro based on BusyBox ([http://www.busybox.net/](http://www.busybox.net/)).

You can install basic packages with the ipkg command (look at the Synology wiki for 'bootstrap').
If those packages won't suffice for you, you can install Ubuntu in a chroot jail. This will let you keep the amazing Synology web interface but running an Ubuntu distro 'on top of it'.

However, I wouldn't advice this to anyone not experienced with linux because it can force you to reinstall the official firmware resulting in possible data loss.

However, if you are certain you're an experienced linux user, here's a small (but incomplete!) tutorial:
[http://kristof.vanhertum.be/?p=132](http://kristof.vanhertum.be/?p=132)
If you've never done a chroot before, try it in a test environment (VM for example) first!

---

