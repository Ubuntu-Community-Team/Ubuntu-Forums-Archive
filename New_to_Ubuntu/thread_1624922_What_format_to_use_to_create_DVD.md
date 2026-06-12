---
title: "What format to use to create DVD ??"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by jerrynewt on 2010-11-18
I have a downloaded movie (all perfectly legal) and it is in .avi format and was wondering if I need to use a program to change the coding to something else before making a DVD or will the .avi format work, and if so which burner should I use ? Thanks for the help.

---

### Post by Mark Phelps on 2010-11-18
To make an actual Movie DVD, you will need an app that transforms the .avi file into the files needed for a Movie DVD. I don't use Ubuntu for that, so I don't have any suggestions ... sorry.

As to burner app, the file conversion apps typically provide the option of burning the resulting Movie DVD files to a DVD, so in general, you don't need a separate burner app.

---

### Post by asmoore82 on 2010-11-18
In order to play on a standalone hardware DVD player,
the video must be strictly MPEG2 with additional restrictions.

Most people confuse DVD-Video Mastering Software with DVD Burning Software.
While there are many programs that attempt to be both,
Strictly speaking, DVD-Video Mastering means transcoding *.avi, *.flv, *.mov, etc.
to mpeg2, then optionally building a menu structure, and compiling the whole collection
into *.VOB, *.BUP, *.IFO in a VIDEO_TS folder.
DVD Burning means storing the VIDEO_TS folder in a valid ISO format
(easily thought of as an *uncompressed* archive format) and writing
it onto a physical optical disc.


tovid-gui does DVD-Video Mastering but not sure about Burning,
brasero does DVD Burning but not sure about Mastering.

I think k3b and DeVeDe attempt to do it all.

dvdflick looks like a good open-source do-it-all solution,
but I haven't personally tried it out yet and it's not in the repos.

---

### Post by owners4life5 on 2010-11-18
just to add, i just finished doing these things...download devede for making the .iso, and try nero for the burner....i know it isn.t open-source, but i have yet to find anything that works period, except for nero. use winff to change the .avi's to .mpeg's...just search winff in the software center.

here is the link to nero:
[http://www.nero.com/enu/linux4.html](http://www.nero.com/enu/linux4.html)

to get devede, just search it in the software center :)

however, if you prefer the terminal, check out this documentation for further info about making a dvd on ubuntu: [http://www.arsgeek.com/2006/08/08/how-to-burn-a-dvd-in-ubuntu-linux-and-other-distros/](http://www.arsgeek.com/2006/08/08/how-to-burn-a-dvd-in-ubuntu-linux-and-other-distros/)

if you would like some further instructions, message me, because i.m in school right now, so it is a bit difficult to monitor the thread :)

---

### Post by kostkon on 2010-11-18
I would also strongly recommend *Devede*. It will convert the video for you and then make an iso out of it. Then you'll only need to burn it to a dvd disc.

---

### Post by jerrynewt on 2010-11-18
Thanks bunches -- DEVEDE worked like a charm !!

---

