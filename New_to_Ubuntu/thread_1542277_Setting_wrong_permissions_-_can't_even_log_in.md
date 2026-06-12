---
title: "Setting wrong permissions - can't even log in"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by poisonborz on 2010-07-30
Hola,
I think I screwed up my Ubuntu installation - stupidly, I set wrong file permissions on the OS files.
Ubuntu now can't start, and I can't even log in in console: (/bin/bash: permission denied)

Is there a way I could fix things, or do I have to format/reinstall? I use Ubuntu 10.04.

Update: Yes, I've read around a bit, and found [this]("http://tinyurl.com/36hwkhb") thread. But to make matters worse, for conserving screen space, I've removed the recovery option from my grub menu... and the console doesn't seem to recognize the chown command.

---

### Post by LowSky on 2010-07-30
I'm just going to say reinstalling wouldnb't be a bad idea. It sounds like you tried a few too many ideas all at once and unfortunatly you did some damamge.

Just to ask What kind of Space were you tring to save by removing the recovery option from GRUB? Also what kind of file permission did you try to set up?

---

### Post by poisonborz on 2010-07-30
Sigh...
I wanted to set permissions so that only root, and two other users could access the OS filesystem. Obviously fiddling with the permissions page after right clicking on the drive in Nautilus (and thus setting permissions for each file) was not the best idea.
With GRUB, I like to have the fewest lines possible, and I just removed the line thinking I wouldn't need it.

---

### Post by da burger on 2010-07-30
Just a suggestion (and I'm not sure it would work) but could you change the permissions from a live cd? If you know the changes you made you could use chroot in or something. Just an idea.

---

