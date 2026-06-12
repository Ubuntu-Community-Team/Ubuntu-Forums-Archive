---
title: "Move /usr/games to /home"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by wobwill on 2010-05-14
Hi,

I am sure this is well documented, but I am unable to see it for looking. I am using an Asus 901 netbook with UNR 10.04 Lucid. The Asus has two drives a 4Gb and an 16Gb. I have / on the 4Gb and swap and /home on the 16Gb drive.

I would like to move /usr/games to space on the 16Gb drive. There is no free space on the drive so this will have to be in /home. How do I move the folder making sure that any new games I install from the repositories are installed to /usr/games?

Many Thanks

Will.

---

### Post by Black Hawk on 2010-05-14
I don't know if this is the best way to do this, but you could remove all the games sitting in /usr/games and move /usr/games. Make sure /usr/games is completely empty and add a line to /etc/fstab to make /usr/games sit on your 16GB drive. If you don't know how to add entries to /etc/fstab there is a rather comprehensive guide here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

EDIT: Oh and then you of cource need to reinstall your games in order to play them :P

---

