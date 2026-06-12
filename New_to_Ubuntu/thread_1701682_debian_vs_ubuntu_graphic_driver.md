---
title: "debian vs ubuntu graphic driver"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Pranaone on 2011-03-06
Hi guys, after the latest debian release squeeze, I wanted to try out debian,and go back to the roots of ubuntu. But one thing bother's me, debian doesn't do well with my old intel gpu (i865g). But ubuntu always works nicely with my gpu. I'm confused even having updated my mesa drivers and xorg to the latest i still don't seem able to get any 3d acceleration under debian. But under ubuntu its flawless. I know that ubuntu uses custom made drivers, but what i want to know is what part of the driver do the tweak to get it work like that? I don't mind if you guys answer it technically, i would prefer it the most. Because the sole purpose i took up linux is to learn it.

---

### Post by Jebus_ on 2011-03-06
> **Pranaone said:**
> Hi guys, after the latest
debian release squeeze, I
wanted to try out debian,
and go back to the roots of
ubuntu. But one thing
bother's me, debian doesn't
do well with my old intel
gpu (i865g). But ubuntu
always works nicely with
my gpu. I'm confused even
having updated my mesa
drivers and xorg to the
latest i still don't seem able
to get any 3d acceleration
under debian. But under
ubuntu its flawless. I know
that ubuntu uses custom
made drivers, but what i
want to know is what part
of the driver do the tweak
to get it work like that?
I don't mind if you guys
answer it technically, i
would prefer it the most.
Because the sole purpose i took up linux is to learn it.

Your formatting made that a pain to read :[ Also, have you checked the exact versions of xorg/video drivers etc?

---

### Post by HeadHunter00 on 2011-03-06
must be kernel related. try installing ubuntu kernel in debian.

---

### Post by HeadHunter00 on 2011-03-06
get the kernel from here: [http://packages.ubuntu.com/maverick/linux-image-2.6.35-27-generic](http://packages.ubuntu.com/maverick/linux-image-2.6.35-27-generic)

---

### Post by Pranaone on 2011-03-06
> **Jebus_ said:**
> Your formatting made that a pain to read :[ Also, have you checked the exact versions of xorg/video drivers etc?

sorry about that, i'm typing this from a cell phone as i'm away from a pc now. I will provide the version later. But i do remember having a newer version of xorg and x86intel driver than ubuntu.

---

### Post by Pranaone on 2011-03-06
thank you headhunter. But won't installing a ubuntu kernel cause dependency problems in debian?

---

### Post by Pranaone on 2011-03-06
@HeadHunter00 btw i've tried installing a liquorix kernel 2.6.37 in debian. But that didn't help. Are you sure that this is kernel related?

---

### Post by grahammechanical on 2011-03-07
I suggest that this is a matter of philosophy or ideology or religion, depending on how you look at it. My understanding is this: The Debian developers want Debian to be totally open source. The Ubuntu developers want Ubuntu to be for humans. So, in Ubuntu we are given the means to install non-open source drivers and codecs, whatever, so that we can do what we want with our machine. Is this not the reason for your difficulties?

Regards.

---

### Post by nomko on 2011-03-07
I am familiar with this issue. There are some topics on the Debian forum related to the poor font rendering. To make this story short: it has to do with the libcairo2 package under Debian.
 
 
[http://forums.debian.net/viewtopic.php?f=10&t=38534](http://forums.debian.net/viewtopic.php?f=10&t=38534)
[http://forums.debian.net/viewtopic.php?f=6&t=58173](http://forums.debian.net/viewtopic.php?f=6&t=58173)
[http://forums.debian.net/viewtopic.php?f=10&t=59728](http://forums.debian.net/viewtopic.php?f=10&t=59728)

---

