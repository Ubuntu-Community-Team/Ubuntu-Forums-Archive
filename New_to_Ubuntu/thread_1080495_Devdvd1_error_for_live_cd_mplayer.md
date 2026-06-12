---
title: "Dev/dvd1 error for live cd mplayer"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-25
hello guys, was wondering is there something I can fix so I dont have to put a 1 infront of the dev/dvd in the mplayer preferences/misc options everytime I want to watch my batman The dark knight movie? is there something I can do while customizing the cd, and it doesnt work when its on the option dev/dvd0. its only when I use a dvd on a live cd but when I change the 0 to a 1 it works fine and loads up and everything but when I dont it saids something like cant find url  with stream or something like that. cant stream to the url maybe.

---

### Post by ericeclifford on 2009-02-25
Is there something I can type in terminal while I make the live cd to change this?

---

### Post by llamabr on 2009-02-25
I don't understand the problem.  You want to start mplayer from the cli, but you don't want to type the 1?  mplayer will start wherever you want, but you have to tell it where to start.  

mplayer has a gui.  maybe you'd prefer that?

---

### Post by ericeclifford on 2009-02-25
I just want the mplayer to play on a live cd 8.04.2 ubuntu version. It does but theres a problem. in its preferences under misc (ON the live cd) theres a dvd device line that saids dev/dvd0, this is causing it to error out with streaming from a url or unable to locate stream of url. BUT if I change that particular line to dev/dvd1 it will work perfectly on the live cd. I want to have that line to read dev/dvd1 by default so I dont have to erase the 0 in front of dev/dvd every time and add a 1 everythime. is this possible to change that default line to something else while customizing the live cd.

---

### Post by llamabr on 2009-02-25
On the livecd?  I don't think so.

Technically, I think you could mount the iso, make the changes including your config, make a new iso, burn that to disk, and make your own livecd, which would respect your changes.

I don't see why this wouldn't work.

---

### Post by ericeclifford on 2009-02-25
Well I when you mount the iso image on a harddrive I dont see the files dev/dvd0 and dev/dvd1.  I need a way to look at the mplayer before its unpacked and whatknot and find a config file to change the default option of picking dev/dvd0 to dev/dvd1 or even better dev/dvd   .  But So far havnt found this file.

---

### Post by ericeclifford on 2009-02-25
Kinda bump but was wonder has anyone have any luck with VLC working on a live cd of 8.04.2 LTS version, I cant seem to get the video part to work for my movie but the audio works just no screen for video. Or does anyone know anything else that works besides totem vlc and mplayer because totem freezes my whole computer everytime then comes up as a resource error or something on both hard drive and live cd version.

Btw I got ubuntu-restricted-formats downloaded and I got libdvdcss2 and a few other libs I cant remember off my head and I got medibuntu repos in and did update/upgrade during the live cd process before I started to add in programs and stuff.

---

### Post by ericeclifford on 2009-02-26
bump Mplayer on a livecd default preference>misc> is for the dvd device dev/dvd it needs to be dev/dvd1 for a live cd , but if you boot off a harddrive it only needs to be dev/dvd.

---

### Post by ericeclifford on 2009-02-26
Help :(

---

