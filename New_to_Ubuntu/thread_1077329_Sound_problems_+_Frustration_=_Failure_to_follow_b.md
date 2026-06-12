---
title: "Sound problems + Frustration = Failure to follow basic problem-solving protocol"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Fer Servadu on 2009-02-22
This post could easily go in the Multimedia forum, since it has to do with my struggle to get sound working on my new system. But it really has to do with general problem-solving in Linux, so I'm putting it here.

My problem was that I wasn't able to get sound into the system via the break-out box for my M-Audio Delta 66 card. I had system sounds, Rhythmbox, Flash, etc, but analog input just wasn't there. I fiddled unsuccessfully with the sound preferences, with the mixer, with Jack, PulseAudio. I have a huge folder of bookmarks to threads, forums, sites, and how-tos that I thought might relate to the problem.

I started getting frustrated. Rebooting over and over again with no result was putting me over the edge, and I started losing track of each change that I made and, worse, I started making multiple changes without really knowing what I was doing.

I somehow became convinced that the issue was that the system was acting up over the presence the onboard audio card and the separate Delta 66 card. I found a suggestion somewhere to add the line ```
pcm.!default front:M66
``` to my .asoundrc file. I did that and rebooted. No change.

I fiddled around with some more settings, and suddenly, unexpectedly, I get sound coming out of my speakers from my guitar! I can't tell you how happy and relieved I was. Loaded Jack, and everything looked good. I loaded Ardour and had sound going in and sound coming out. I had sound in all of my recording applications and I was ready to settle in and start using my system in all of its capacity.

A little while later, I decided to take a break and kill some time on YouTube. I clicked on a video... and no sound came out.

You can imagine my frustration. Now I had good analog sound coming in to my audio applications, but I had absolutely zero sound from any other source. Nothing from FireFox, nothing from Rhythmbox, no test tone from System>Preferences>Sound.

I started the whole process over again. Fiddling with this, tinkering with that, rebooting, rebooting, and rebooting. I eventually came to the conclusion that I had bricked ALSA beyond all recognition, and so I purged and reinstalled the entire sound system. Still no sound beyond the analog source.

After a long session trying to find changes to ALSA that hadn't been affected by the reinstall, I finally remembered the .asoundrc file. I opened it up and discovered that my change was still there. Although I still thought that this was the one change that had made my analog input work, I decided to comment out the line I had added and reboot the system...

And everything worked. System sound, analog input, the whole shebang worked. 

It turns out that I had initially had my mixer settings set incorrectly. But I didn't realize this fact and fix it until the same session in which I altered the .asoundrc file. But I was so frustrated, and my head was swimming so much from all of my efforts, that I conflated the two changes.

To make a long story only slightly longer, these are the lessons learned, from a guy who already knew better:

[LIST]
[*] Don't let frustration get the better of you.
[*] Keep track of each change that you make to your system, so that you can go back and undo them if you see no change or make things worse.
[*] Make one change at a time, unless you're sure that multiple changes are necessary and/or linked as part of the same solution.
[*] Make every effort to understand what you're doing. E.g., don't just blindly copy and paste, don't just blindly follow instructions.
[*] If you're new to Linux, remember that even guys like me who have experience with multiple distros on multiple platforms can find themselves in unfamiliar territory and stupidly screw things up.
[*] And, finally, *don't let frustration get the better of you.*
[/LIST]

Sorry for the long, long story, but maybe sharing my embarrassing predicament will encourage others to stick with it and find the solutions they need.

---

### Post by blueridgedog on 2009-02-22
Bravo...by the way, a recent linux journal article covered the use of external mixers for professional audio.

---

