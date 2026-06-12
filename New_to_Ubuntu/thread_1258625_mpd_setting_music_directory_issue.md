---
title: "mpd setting music_directory issue"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by chlasio on 2009-09-05
So I've downloaded mpd and gmpc, when I tried to set my music directory in mpd over the terminal this pops up;

sudo in -s /media/disk/MUSIC
[sudo] password for user: 
sudo: in: command not found

So I've tried without ''in''
( I didn't know how to see the directory name so I've just opened the folder music with terminal and copied the name from there, please correct me if i did wrong, im a big noob :( )
that music directory is on my windows partition if it helps with the issue.
sudo -s /media/disk/MUSIC
/media/disk/MUSIC: /media/disk/MUSIC: is a directory

then i typed;
[I]sudo mpd –create-db

And this error showed;
** ERROR **: problems opening file –create-db for reading: No such file or directory

aborting...
Aborted

[/I]I've also tried to edit mpd.conf file with text editor to change my directory, it didnt worked so i reversed the actions i did. Any help would be really useful, I don't know what to do. :(

---

### Post by Liolikas on 2009-09-05
>I've also tried to edit mpd.conf
Yes you should use this.

man mpd.conf for more info.

---

### Post by chlasio on 2009-09-05
I've edited music directory in mpd.conf again but nothing changes in gmpc ( can't see the directory that i've changed )
I've checked that help file as well, but it just explains what music_directory, etc. means.

Nvm, I sorted it out. Just needed to add symlink to the default directory. :)

---

