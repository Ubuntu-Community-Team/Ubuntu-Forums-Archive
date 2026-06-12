---
title: "cd/playlist quit playing cannot"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by luke0927 on 2008-12-18
OK so yesterday i put in a store bought CD to test out the media player it would show the songs etc...but when you clicked play it would just sit there it would not actually play after doing the commands below it worked.  So i pulled the songs off and created a playlist and was able to play it...now it just quit working i have installed Banshee 1.4 to what i assume is correct...i don't believe the system has done any updates or anything any idea why its not working or how i can try and trouble shoot it?  

running these commands below fixed Rythmbox (i tried them again but it did not work)

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

i installed banshee according to the link below

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

---

