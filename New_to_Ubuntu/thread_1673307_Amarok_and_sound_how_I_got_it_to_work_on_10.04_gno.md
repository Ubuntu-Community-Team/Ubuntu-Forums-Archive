---
title: "Amarok and sound: how I got it to work on 10.04 gnome"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-01-22
Ubuntu Community:

I get alot from the community, so this is a chance of mine to give back a little. I'm not sure if this solution will work for everybody, but it did for me, this time. Hopefully, someone more knowledgeable will chime in and correct my errors, or give definitive guidance, and explain the reasons the function of each command so that readers can learn how their system really works.

I did this:

[COLOR="SeaGreen"][B]sudo apt-get remove amarok
sudo apt-get install amarok
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils[/B][/COLOR]

And, next:


[COLOR="SeaGreen"][B]sudo apt-get install phonon-backend-xine
sudo aptitude install libxine1-ffmpeg
sudo aptitude install ubuntu-restricted-extras[/B][/COLOR]

Now, make sure you have chosen the right sound card, not just for your system, but for Amarok, also: 

[COLOR="SeaGreen"]**System > sound > output > choose your soundcard name from the list**[/COLOR]

then

[COLOR="SeaGreen"]**Open Amarok --> Setting --> Configure Amarok --> Playback --> Configure Phonon (move the name of your soundcard to the top of the list, click apply, then test)**[/COLOR]

I hope this works for somebody else.

Sincerely,
Phil Smith
Duluth, GA

ps. I'm not going to mark this "SOLVED" since I don't know whether it will work for everyone.

---

### Post by Life On Mars on 2011-01-22
Thanks for that, Phil :-)

I didn't need to remove and reinstall anything, just added the missing phonon-backend-xine (I had the other packages installed already), restarted Amarok and everything works perfectly now :-)

---

### Post by Old Jimma on 2011-01-22
If music be the food of love, play on;
Give me excess of it!

Twefthnight.
The Bard of Avon

---

