---
title: "DVD playing problems (Jurassic Park)"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by iminhell on 2008-12-04
I've only played one movie so far, Shooter (burnt copy) (good movie btw) and it played well after I got sound to work (had to dump all the pulseaudio junk). But I can't play Jurassic Park (store bought copy).
I can get the FBI warning to play on VLC, Movie Player and Gxine (which I like the best, just easy to use).

This is what it tells me in the log (user.log, hope that is the correct one)

"Dec  3 21:33:52 john-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 "


This is what is on the disc:

[IMG]http://i34.photobucket.com/albums/d120/iminhell/Screenshot-JURASSIC169-FileBrowser.png[/IMG]
(obviously it's mounted if I can open and view the files)

Really not sure what it's issue is.




Also looking through the logs I found this:

"Dec  4 02:53:48 john-desktop kernel: [19328.505050] ACPI: Unable to turn cooling device [f7411f18] 'on'"

It's repetitive since I started using Ubuntu about a week ago. I'm guessing it wants to turn the case fan on but cannot. Reason being is I'm using a manually controlled unit from Silverstone.
Can I just disable that command somewhere so it doesn't keep freaking out?


-John


*edit, I keep forgetting to mention what version I have; 8.10

---

### Post by mapes12 on 2008-12-04
Hi John

This may help: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Mark

---

### Post by iminhell on 2008-12-04
Just tried playing another burnt DVD and this is what pops up:

[IMG]http://i34.photobucket.com/albums/d120/iminhell/Screenshot-2.png[/IMG]

DVD was ripped in Windows with DVD Decrypter (ISO mode) mounted with Daemon Tools then burnt to a DVD+R with DVD Fab Decrypter (I think). (looking for cross over programs for Linux also)

Exact same way the other one that did play was done, same as I do all mine.

Far as I know I have all the correct codecs. What command can I type to check and get something for you guys to look over?

---

### Post by philinux on 2008-12-04
Have you got the medibuntu stuff?

If not click link below.

---

### Post by iminhell on 2008-12-04
Yup. Have libdvdcss2, libdvdread3, libdvdcss-dev, gxine and the w32codecs for audio
Basically everything that was in here -> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Plus full Studio upgrades (minus the pulseaudioo like I mentioned).

I tried re-installing but no go. I'm really at a loss here.

---

### Post by iminhell on 2008-12-04
Any new ideas?

---

### Post by Tatty on 2008-12-04
Have you tried setting the region with regionset?  I sometimes have to do that after a new installation.

---

### Post by iminhell on 2008-12-04
I'm leary on that program -> [http://linvdr.org/projects/linvdr/index.en.php](http://linvdr.org/projects/linvdr/index.en.php)

If I'm reading correct I have to pretty much uninstall all of Ubuntu (all my updates/programs/etc) put this on first, then install Ubuntu again with all my updates/programs/etc ... ?

Seems like a waste of time personally.

---

### Post by crjackson on 2008-12-04
This is what I usually do: [http://buck-nasty.blogspot.com/2008/11/install-audio-and-video-codecs-in.html](http://buck-nasty.blogspot.com/2008/11/install-audio-and-video-codecs-in.html)

It pretty much never lets me down, but it seems you've done most of this already.

I will say, that I HAVE run across 2 movies that would not be decrypted and would not play on Linux. The ONLY way I was ever able to watch them under Linux was to RIP / STRIP / RE-BURN the movie.

---

### Post by iminhell on 2008-12-08
This is ridiculous. I am going to uninstall Ubuntu for the 5th time and try again. It has to be a driver conflict that I am not finding. Every once in a while I get some ******** about 'I don't have proper permission', FK if I don't. I'm the damn administrator you cowardly POS.

(insert picture of me beating up the PC in a vacant lot with a bat)

---

### Post by iminhell on 2008-12-09
Hey what do ya know. Fresh install, correct codecs and I have video, BUT NO ******* SOUND.
This is god damn aggravating.

OH, and it apparently ate Windows. So now I'm stuck with this worthless crap and have to try to get Windows to work again. It did right after the install. ******* ********.

Nothing like having 800 useless DVD's that I can't hear. Eh guess I'll just have to hum along. :popcorn:

Honestly, what advantages does Ubuntu really have, I'd really like to know?

---

### Post by sambita on 2008-12-09
> **iminhell said:**
> Yup. Have libdvdcss2, libdvdread3, libdvdcss-dev, gxine and the w32codecs for audio


How about libdvdnav4?? i recommend you install that package and give it a shot, specially since thats what it seems to be asking for. 

You can find it in synaptic.

Edit: Seems like my post was a little late, do you have sound problems with other applications or just playing dvd?

---

