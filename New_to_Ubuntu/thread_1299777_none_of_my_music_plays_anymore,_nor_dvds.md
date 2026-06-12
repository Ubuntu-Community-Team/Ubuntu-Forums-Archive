---
title: "none of my music plays anymore, nor dvds"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by adamogardner on 2009-10-24
My .flac files and such used to play fine with only an occasional not play.  Now they don't.  I drag them into the default music player (totem is it) and nothing..  DVDs don't play either, but never did to the best of my knowledge.  I would like it all to work again.

---

### Post by rampageoberon on 2009-10-24
The below links may be helpful for your problem.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Hope it helps

---

### Post by Keith Hedger on 2009-10-24
Flacs are not a restricted format so should play ok, what does totem say when you try to play them, have you tried a different player ( quod libet,rhythmbox etc )? Have you tried reinstalling totem as You may have accidentally broke it?
The more info You give the better people will be able to help you, just saying "It don't work" isn't very helpful.

---

### Post by adamogardner on 2009-10-24
Keith Hedger,  you were great as the joker.   OK, so when I say .flac files and such I mean "unrestricted files and others.  That pretty much runs the gamut, doesn't it?  What do I know.  And when I say I drag files into totem and "nothing",  I mean literally, nothing.  It just doesn't work.  There is no message; nada.  I did try to reinstall it.  But perhaps I did it wrong?:

adamogardner@CRONUS:~$ sudo apt-get remove totem
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libadns1 wireshark-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  totem
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
After this operation, 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 248944 files and directories currently installed.)
Removing totem ...
adamogardner@CRONUS:~$ sudo apt-get install totem
sudo: unable to resolve host CRONUS
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libadns1 wireshark-common
Use 'apt-get autoremove' to remove them.
Recommended packages:
  totem-plugins-extra
The following NEW packages will be installed:
  totem
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 41.0kB of archives.
After this operation, 86.0kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main totem 2.22.1-0ubuntu3 [41.0kB]
Fetched 41.0kB in 4s (9025B/s)
Selecting previously deselected package totem.
(Reading database ... 248938 files and directories currently installed.)
Unpacking totem (from .../totem_2.22.1-0ubuntu3_all.deb) ...
Setting up totem (2.22.1-0ubuntu3) ...

---

### Post by adamogardner on 2009-10-28
back in the day if I hovered my mouse over the music file it would play.  it doesn't do that anymore.

---

### Post by vexorian on 2009-10-28
Could it be a sound mixer issue? pulseaudio assigning music playback to another device maybe?

I mean, do you get a player window but don't listen the music or does absolutely nothing happens?

---

### Post by adamogardner on 2009-10-28
\oops, posted twice somehow

---

### Post by vexorian on 2009-10-28
Does sound work elsewhere?

---

### Post by ikt on 2009-10-28
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

is the sound troubleshooting wiki with some advice.

It is however very strange that your sound is no longer working, do you still have the original Live CD? 

I would boot onto the live cd to see if sound works on it, there is always the possibility of damaged speakers, plugs not fully in correctly etc.

---

### Post by adamogardner on 2009-10-28
> **vexorian said:**
> Could it be a sound mixer issue? pulseaudio assigning music playback to another device maybe?

I mean, do you get a player window but don't listen the music or does absolutely nothing happens?

Yes, Totem opens, but when I drag a music file into it it doesn't play.  though the pause button IS revealed in the player, meaning that it is in play mode. (if that means anything)  
Sound mixerand pulse audio is something I know nothing about.  Ah I have tried other music players,  vlc, amarok.  What do I do?  That's probably it?  I'll check my preffered applications

---

### Post by adamogardner on 2009-10-28
> **ikt said:**
> [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

is the sound troubleshooting wiki with some advice.

It is however very strange that your sound is no longer working, do you still have the original Live CD? 

I would boot onto the live cd to see if sound works on it, there is always the possibility of damaged speakers, plugs not fully in correctly etc.

No I get sound from internet and such.  just not out of my music player.  thanks for the link

---

### Post by dearingj on 2009-10-28
Perhaps your flac and dvd codecs got messed up somehow. Try this:

sudo apt-get install libflac8 libdvdread4 --reinstall

---

### Post by vexorian on 2009-10-28
> **adamogardner said:**
> No I get sound from internet and such.  just not out of my music player.  thanks for the link
It could still be a problem.

Do you see a volume icon in your task tray?

Right click\ volume control.

It will show you a lot of volume controls, try playing out with those and find one that is muted (maybe there's one affecting music?)

---

### Post by adamogardner on 2009-10-28
> **dearingj said:**
> Perhaps your flac and dvd codecs got messed up somehow. Try this:

sudo apt-get install libflac8 libdvdread4 --reinstall

couldn't find package libdvdread4

---

### Post by adamogardner on 2009-10-28
it works,  I had to change preffered applications and then restart.  thankyou.

---

### Post by adamogardner on 2009-10-29
So I got totem to work.  but now my browser won't play sound.  Totem isn't running.  How do I fix this.  I think this was the reason I changed media players in the first place.

---

