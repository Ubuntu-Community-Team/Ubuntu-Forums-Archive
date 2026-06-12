---
title: "Configuring sound card in Ubuntu Server"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2011-05-06
Hey,

So I am trying to build a sound server out of an older box that was laying around my place, and I'm currently trying to get the card set up. The machine is headless, so I am configuring it via SSH.

What I am trying to do is test the sound by using VLC. As of right now, I am not getting any sound out of the card. When I enter
```
alsamixer
```
it brings up the mixer in the commandline, and it detects the sound card all right.

When I enter
```
aplay -l
```
it does not find any cards. BUT then I enter
```
sudo aplay -l
```
it finds a bunch of different things.

I have successfully run VLC in the terminal with sound on other machines, and what I have noticed on all of the other machines is that I do NOT need to insert "sudo" in front of the aplay command for it to return the cards in the system. Could this be part of the problem?

Anyone have any ideas as to how I can get this it work?

All help is appreciated.

-Kurt

---

### Post by jkurtisr32 on 2011-05-06
Ok, I am fairly certain that the sound is just muted, and I can't seem to figure out how to unmute from the terminal.

I installed Ubuntu on my piece-of-**** Dell laptop, and all of the settings and outputs from the checks (sudo aplay, alsamixer, etc) was the same as the box. No sound from the Dell.

I installed
sudo aptitude install gnome-desktop
and found that the speakers were muted. I don't know if Gnome changes those kinds of settings when it is installed from terminal, but if not, then I assume that the problem is the same on my box.

Any ideas on how to unmute from the terminal?

-Kurt

---

