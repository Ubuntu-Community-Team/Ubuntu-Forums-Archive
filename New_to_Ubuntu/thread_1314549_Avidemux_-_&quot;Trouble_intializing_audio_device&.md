---
title: "Avidemux - &quot;Trouble intializing audio device&quot;"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by duncv89 on 2009-11-04
Hey

Just trying to edit a video in Avidemux but the sound doesnt seem to be working properly, seems like it was a common problem but hasn't really come up recently.

And i have tried some of the ways from a few years ago, like changing the default audio to alsa, and thats what it is at and it doesnt help.

Any help would be appreciated.

Thanks.

D

---

### Post by therabyte on 2009-11-04
I m having the same problem. Just installed Avidemux on Karmic and got no audio.

Audio setting is set to Alsa, but tried all the other options and still no audio.

---

### Post by Danny94 on 2009-11-05
Hey guys. I had the same problem with karmic. I finally seem to have got it partially fixed by installing alsa-oss-wrapper. then i set my output to oss or sdl and both worked but studdered. Hope that helps.

---

### Post by bumanie on 2009-11-05
I had that happen with one file, but strangely all other files have not had sound issues - may be try another video file and see if it works with it. Can't really help - in the end, I concluded it was a glitch/gremlin in that one file.

---

### Post by rjbeeth on 2009-11-05
After upgrading to Karmic I've discovered a problem too.... it doesn't seem to matter what program acquires the device the first time... it just never lets go after that and nothing else works....

Sounds play fine during reboot but once I'm logged in it's first come first serve and a reboot seems to be required to change programs that can run the device.

I first noticed this with flash player, I was able to play avi's without any problem (the first audio that I tried) but when I tried to play a flash video, it played with no sound.

Various things were tried including upgrading the alsa driver and libraries to the latest version... a reboot was required and firefox was still on the youtube page. After the reboot, when firefox loaded the video AND sound played but now my avi videos sort of locked up. The program said it was playing but it would not move....

Experimentation ensued. And I found that after a reboot regardless of what program acquired the sound card first - it worked.... but nothing else did... 

In all cases, regardless of program that could not play a sound, the same entry was found in my syslog
pulseaudio[3371]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy

I've even tried installing paman (pulse audio manager) but nothing has changed....

Any ideas? Any way to release the device manually till a fix comes out?

---

### Post by hellomoto on 2009-11-11
Has anyone fixed this problem yet?

I always used to change avidemux auido prefs from ALSA to default to get it to work but avidemux does not allow you to input text into these fields now. I tried changing the settings in the config files but that did not work either.

I get sound with avidemux when using OSS but is stutery and makes time syncing videos extremely difficult.

---

### Post by therabyte on 2009-11-11
I haven't fixed the problem so I switched to the "Pitivi Video Editor", which has all the features I require and it's available from synaptic without adding extra sources.

If you decide to use Pitivi, you have to remove the following packages, if they're installed in your system:


[LIST]
[*]gstreamer0.10-fluendo-mp3
[*]gstreamer0.10-fluendo-mpegdemux
[*]gstreamer0.10-fluendo-mpegmux
[/LIST]

I had to remove the mp3 package mentioned above in order to get the sound to work. The removal had no undesired side effects in my system (all other applications, including video and mp3 players, are still working fine).

---

### Post by dannyboy79 on 2009-11-11
> **hellomoto said:**
> Has anyone fixed this problem yet?

I always used to change avidemux auido prefs from ALSA to default to get it to work but avidemux does not allow you to input text into these fields now. I tried changing the settings in the config files but that did not work either.

I get sound with avidemux when using OSS but is stutery and makes time syncing videos extremely difficult.

sounds like a pretty standard pulseaudio issue. review the pulseaudio solution threads and you should be all good. i know that when my sound stops working cause firefox grabbed it first before I opened say hulu desktop, i just have to close firefox, open terminal, restart pulseaudio with sudo /etc/init.d/pulseaudio restart and then open hulu desktop and sound is back. good luck. from what I have been reading I am not impressed with karmic at all. they should hava definitely solved the pulseaudio issues. Linux Magazine shreaded Ubuntu a new a__hole because of teh poor quality of Karmic. It's a shame because Ubuntu claims to be easy to use but every release there's something wrong, this isn't a little thing either I might add! Sound, wireless networking, power management shoudl all be top priority. I am still using Jaunty for now because i'd have to upgrade all my boxes because all 4 of my machines run mythtv and from jaunty to karmic, mythtv made a major revision so can't just upgrade one box, have to upgrade them all.

---

### Post by aliciapg on 2009-12-21
I'm having the same problem. In avidemux for 9.04 I could simply type in default for audio and it was instantly fixed. Now in 9.10 they removed the option to type. So....that no longer works. Anyone have a fix?
[I]
This worked for me. ^-^
"You can tell Avidemux to use OSS and then start the application using &#8220;padsp Avidemux&#8221;."
 - [https://bugs.launchpad.net/ubuntu/karmic/+source/avidemux/+bug/215560]("https://bugs.launchpad.net/ubuntu/karmic/+source/avidemux/+bug/215560")[/I]

---

