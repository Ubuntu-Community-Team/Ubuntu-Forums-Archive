---
title: "Working Microphone suddenly not working"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by MaxVK on 2009-06-07
Hi. I have gone from a perfectly working mic to not working at all, and for the life of me I have no idea what I may have changed to cause the problem.

In my Sound Preferences window I have the following:
Sound Events: Autodetect
Music and Movies: Autodetect
Audio Conferencing:
    Playback: Autodetect
    Sound Capture: ALSA

The sound card is an SBLive 5.1 and the mic is plugged into the jack at the back, NOT the jack at the front of the system. If I open the volume controls and un-mute the Microphone my voice comes out loud and clear, but if I try to record my voice using the Sound Recorder program, the input choice is "Capture" (I'm sure it was working like this before!) and nothing gets recorded.

In Audacity Iv tried all of the options for recording input but with no result - anything recorded simply does not pick up any sound.

Just to make sure you know: The mic was working perfectly up until about an hour ago, although the only thing I (thought) I changed was the mic level. I can still un-mute the mic and hear myself as clear as day.

Anyone got any ideas how to set this pesky thing back up? It was working by default and I don't know what Iv done to change it.

cheers

Max

---

### Post by MaxVK on 2009-06-08
Well this has become painful. Iv followed half a dozen articles on how to set this thing up properly (again), Iv even gone so far as to install things that were not there when it was working before.

However, Iv have so far managed to get the mic working in so far as I can speak through the speakers to it, but thats as far as it goes. I can mute it or I can hear myself through it, but it will not record.

This is by far the biggest and most frustrating pain that Iv suffered since I started using Ubuntu (I didn't have these problems on 7.10 - Same hardware), and more to the point, the blasted thing WAS working fine, in both the standard sound recorder and Audacity.

I'm in need of some help here please - Anything! For heavens sake the thing was working until yesterday and I didn't set *anything* up, it just worked. As far as I can remember the only thing I changed was the mic level from within the volume controls. Now it just *will not* record.

Cheers

Max

---

### Post by MaxVK on 2009-06-09
Okay, I cant give an exact idea of what I did, but its fixed, and roughly, this is how I did it:

Firstly it seems that Pulse Audio is actually a pain, so I followed some advice from [here]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") to kind of turn it off. Please note that I didn't follow *all* of the instructions, just the ones to turn off Pulse and setup the Microphone.

At first all this didn't seem to make too much difference. I could still hear my voice but record nothing, however, the SBLive has a set of jacks and inputs on the front of the system too, and Iv been testing with these as well as the standard ports at the back.

Interestingly for the first time the mic input on the front panel worked, and more to the point it recorded first time! The port on the back still does not.

So its fixed and to be honest I'm not entirely sure how - I followed some instructions and I fiddled with levels etc, and suddenly its working.

Anyway, I hope this might help someone, and if you need any more information regarding my setup, let me know - I might not be able to add much in the way of actual help, but I can let you know my settings.

Max

---

