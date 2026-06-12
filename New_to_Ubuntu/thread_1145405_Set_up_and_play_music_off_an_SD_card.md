---
title: "Set up and play music off an SD card?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by dragonwarriorfan on 2009-05-01
Using Jaunty 9.04 on a Dell 9 and hoping to find out how I can set up Rhythmbox to look for music on my SD card. I can't import and store files on my hd for space issues (4GB SSD). How do you all set up your media files? Thanks!

---

### Post by MontelEdwards on 2009-05-04
Well let's make sure that you have the appropriate codecs to play these songs.
open a terminal by going to applications>accessories>terminal
and type in ```
sudo apt-get install ubuntu-restricted-extras
``` then wait for that to finish and then there are two ways to do this. 
1. create a symbolic link to your music folder from your SD card.

Lets do that.

First go to places then computer.
Then open your SD card and in the folder where the music is, right click it and go to make link. Then right click that link, click copy, and then go to your home directory and then to your music folder and right click and paste.

Then fire up Rhythmbox and and i think tools then settings and then to import. [i am not sure where exactly it is]  and check the box that says "watch folder for files" or whatever. Then they should show up in rhythmbox.:guitar:

---

