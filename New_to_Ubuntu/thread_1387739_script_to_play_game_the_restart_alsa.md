---
title: "script to play game the restart alsa"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Sylos on 2010-01-22
Hello all.
I am currently having a little trouble with a game (ut2003) hogging my sound drivers after I have ended the game forcing me to reload alsa after I have quit the game in order to allow any further sound.
I would like to make a script that I can use to launch the game and then, when the game ends, force-reload alsa.
I can get the launching the game bit fine but, as a noob, I dont know how to get the force-reload to be triggerred by the game being quit. Assumably there is a signal that could trigger it?

Any ideas how this can be done?

Many thanks,

---

### Post by VCoolio on 2010-01-22
Try to use && between commands; the command behind will be executed once the command before exits successfully. To reload alsa you need a password I guess, so either do
<run game> && sudo <alsa restart command>
if you use a terminal; or
<run game> && gksudo <alsa restart command>
for a launcher. It will prompt for your password when the game exits and then reload alsa.

---

