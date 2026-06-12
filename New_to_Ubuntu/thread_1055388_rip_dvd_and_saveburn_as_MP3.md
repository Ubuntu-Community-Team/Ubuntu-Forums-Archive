---
title: "rip dvd and save/burn as MP3"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-30
hi everybody
can anyone recommend an application to copy/rip a dvd and save the music tracks as MP3 so i can play them on my player? 
i shall also be looking on synaptic/google but if anyone knows of a good one (if such a thing exists/is possible anyway) i will be very grateful.
thanks for any help
nigel

---

### Post by Coreigh on 2009-01-30
I *think* handbrake can separate the audio from the video.

There is a new Handbrake GUI version available for Hardy and Intrepid
Add this to your apt sources (/etc/apt/sources.list):
> deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) hardy main

Change hardy to intrepid if you have intrepid (8.10)

then```
sudo apt-get update
```
then```
sudo apt-get install handbrake* 
```

The asterisk is a wildcard, there should be 4 handbrake packages.

---

### Post by capnthommo on 2009-01-30
hi coreigh, thanks.  i shall certainly check this out.  i am aiming to lift music tracks from dvd-r/rw and save them as mp3 in my music file/ipod.  so i want to gather a selection and pick the most straightforward cos i am not all that tech minded.
thanks again
nigel
:guitar:

---

### Post by ajgreeny on 2009-01-30
You can also use **audacity** from the repos to capture the sounds from your sound card and then export the captured sound as mp3.  I know it works as I have done it.

---

### Post by capnthommo on 2009-01-30
hi ajgreeny
thanks thats another one to check out.
cheers
nigel

---

### Post by niteshifter on 2009-01-30
Hi,

Have a look at this [page]("http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html") (ubuntugeek.com) "How to Rip DVD audio to mp3 or ogg".

The thing about grabbing audio via Audacity is it's slow, that is - you get it as you play it. The above is fast - as fast as your system can process the tracks.

---

### Post by capnthommo on 2009-01-30
hi niteshifter.  okay then, i checked out the link but i couldn't get very far with it.  do you have any more detailed instruction or advice to offer?  
i take your point about audacity but at least i know it works, having tried it - simplicity is more important than speed for me.  i'm not looking at commercial levels here, just to be able to pull the odd song from dvds of live gigs, save them in my music file and play them, and maybe burn onto a cd.  
so you can see why i would want to lift just the audio because
       1.  i don't need the video track.  
       2.  the video will most likely not burn to cd anyway, will it.
i am assuming that this can in fact be done - i have found several how tos that seem to offer a solution/application but nothing seems to quite fit the bill - they all seem to want to just copy the dvd, or save it to file or only copy cd format, when what i want is something that will work trans-format.
if i had the skill i would try writing my own but alas i am a humble carpenter!
thanks a lot for the help
nigel

---

