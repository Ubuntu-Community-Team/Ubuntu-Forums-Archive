---
title: "Restoring xorg.conf and having problems!"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by kb010 on 2009-07-24
So I posted yesterday about trying to get Farm town working and I ended up messing up my ATI graphics. Anyways, I wanted to revert my xorg.conf back to what it was before I made the mistake. 

When i type in sudo dpkg-reconfigure xserver-xorg it goes through the formatting (blue) screens, but then comes up saying" xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf .20090724152005
and below that it says: root@kendra-laptop:~#

what am I doing wrong? I feel like a total idiot, and it's driving me crazy that I can't get it to restart without the graphics just....going haywire.

any help would be really really appreciated!

---

### Post by mapes12 on 2009-07-24
What version of Ubu are you running?

---

### Post by kb010 on 2009-07-24
9.04

---

### Post by mapes12 on 2009-07-24
Editing the xorg.conf file in 9.04 no longer works. The configuration has been passed across to an automated probe the name of which I can't recall. But this link may help you out: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by realzippy on 2009-07-24
you can reach a terminal with CTRL+ALT+F2 ?

---

### Post by kb010 on 2009-07-24
currently I have been starting it under recovery mode and then selecting root menu with networking (or something to that nature). it then goes through a series of text and comes up with root@kendra-laptop: ~#
when i hit control-alt-F2 it takes me to a blank screen with a blinking underscore.

---

### Post by realzippy on 2009-07-24
ok,so when you are at your root terminal,you can remove your broken video-driver,do not know,is it fglrx?

---

### Post by kb010 on 2009-07-24
I don't know. What i am hearing is that it is impossible to return xorg.conf back to what it was before this all happened. is this correct? Am I better off just re-installing?

---

### Post by realzippy on 2009-07-24
maybe reinstalling is faster than repairing a broken video driver step by step on the forum.
The xorg.conf of course can be rescued;just delete it,there will be a new one.
If you could reach a terminal and knew your video driver,you could remove it by:

sudo apt-get --purge remove name-ofthe-driver

E.G.:

sudo apt-get --purge remove fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx fglrx-amdcccle libamdxvba1 

if it is the amd driver...

---

### Post by mapes12 on 2009-07-24
> Am I better off just re-installing?That's what I would do.

Make sure you backup to external media any of your documents in /home. So that you don't have to waste bandwith for any updates and currently installed applications you can copy them to a CD/DVD using aptoncd to easily reinstall them. It's in Synaptic. Also note any FF's addons you may want to reinstall afterwards.

Did this myself yesterday and it worked following a HDD upgrade.

---

### Post by LewRockwell on 2009-07-24
> **kb010 said:**
> I don't know. What i am hearing is that it is impossible to return xorg.conf back to what it was before this all happened. is this correct? Am I better off just re-installing?

Normally, when responding to this type of off-site/remote trouble-call, it is in fact wise to re-install

The main reason for this is that by the time we've all discovered EXACTLY what has and hasn't been done...and tried to sort it all out...your re-install would already be complete and you'd be back up and running again

Not only that, but sometimes the best way to learn is to have some repetition involved...just chalk it up to some extra experience...

.

---

### Post by kb010 on 2009-07-24
Understood. I am just going to re-install. this has become way too much headache. Anyways, Thanks for your advice. =]

---

### Post by LewRockwell on 2009-07-24
> **kb010 said:**
> Understood. I am just going to re-install. this has become way too much headache. Anyways, Thanks for your advice. =]

yes, we left before the hurricane and avoided the headaches also...

.

---

### Post by edu1962 on 2009-07-25
Maybe [[COLOR="Red"]this[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=90&t=20326&p=120317&hilit=displayconfig#p120317") can help you out.

It's a solution from a mint-forum to install displayconfig-gtk. 

Didn't try it yet, i prefer to stick with 8.04 due to the sis671 video-card i have in my laptop.

---

