---
title: "Sound issues when running a game"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by jendie on 2010-12-17
Hi everyone, I've been searching for a solution for this for a while, but no luck.

Whenever I run certain games (Cortex Command, Hedgewars, The Mana World) the main volume increases and decreases rapidly. In some cases, moving the mouse pointer seems to make it worse. Even after I exit the game it fluctuates from muting itself and maxing the volume for about a minute.

I'm running Lucid 64bit on an HP Pavillion dv4, Intel G45 sound card.

Any ideas?

-Jennifer

---

### Post by jendie on 2010-12-17
I just tried running some of the games while checking out the ALSA mixer. The master volume keeps trying to max out, and the PCM volume stays maxed no matter what. No matter how many times I try to bring the volume slider down, the sound automatically increases. :\

---

### Post by jendie on 2010-12-18
bump

---

### Post by Eiji Takanaka on 2010-12-18
I'm not sure if alsa is the mainstream audio device anymore, wasn't it taken over by pulseaudio? Perhaps the games your running might be more inclined to run with pulseaudio. Worth a shot anyways. Although i'm not completely up-to-date with the latest sound programs, so maybe its been changed for the latest ubuntu release.

---

### Post by jendie on 2010-12-18
> **Eiji Takanaka said:**
> I'm not sure if alsa is the mainstream audio device anymore, wasn't it taken over by pulseaudio? Perhaps the games your running might be more inclined to run with pulseaudio. Worth a shot anyways. Although i'm not completely up-to-date with the latest sound programs, so maybe its been changed for the latest ubuntu release.

So if PulseAudio is the default, how would I go about making sure everything is working properly? (Besides the Sound Preferences.) And what exactly is the difference between ALSA and PulseAudio?

---

### Post by Eiji Takanaka on 2010-12-18
Good question(s) I'll answer what i know.

Alsa was the default sound interface/device until fairly recently when pulseaudio was introduced. Pulseaudio had(perhaps still has, although i haven't encountered any lately) a fair number of bugs resulting in a number of people resorting back to 'alsa' either by completly uninstalling pulseaudio or temporarily killing the daemon before running the required program. (bit of a long-winded process as you had to tat about with the config files, before doing the whole killswitch thing.). 

It's usually the other way round i.e pulseaudio causing the problems/conflicts and needs tempo disabling. I'm not entirely sure how to completely disable alsa other than perhaps uninstalling it, and installing pulse audio if its not allready installed. 

It sounds like a strange bug though, almost as if your movements of the mouse are still controlling the sound-mixer applet/interface, in which case perhaps a process is failing to background properly. 

Try the whole installing a different sound interface though, temporarily see if that solves your problem. ;)

---

### Post by jendie on 2010-12-18
Thanks for your help - I'll give that a shot and let you know how it works. :)

---

### Post by Eiji Takanaka on 2010-12-18
No problemos

Good luck chica! ;)

---

### Post by jendie on 2010-12-18
Well, I removed PulseAudio, and it solved my original problem, but there was no sound at all with one game. The other two had sound but refused to get past the loading screen. :\

So I reinstalled PulseAudio and everything is back to normal except the sound indicator is missing despite re-adding the applet and restarting gnome panel.

---

### Post by jendie on 2010-12-19
Well the problem turned out to be with the dv4's media touch bar thing at the top. I guess it just doesn't wanna play nice with Ubuntu.

For anyone else with this problem, it's a really easy fix:

System > Preferences > Keyboard Shortcuts

Then remap the XF86 Mute, Volume Down, and Volume Up to whatever you want. To reset it to the default, just click on each mapping and use the touch panel for the respective settings.

Thanks again for your replies, Eiji!

-Jennifer

---

### Post by Eiji Takanaka on 2010-12-19
Hey Jen, i was going to reply last night, but a good film came on, so i got sidetracked, crank, (i've been meaning to watch it for a while ;)P. Sorry about that. 

I was just scanning through the posts, to try and find your one (i keep forgetting to follow threads =P) But alas you have made it easy for me. 

Glad you found a solution to your problem =), did you manage to get pulseaudio and alsa working properly again?

- dan

---

### Post by jendie on 2010-12-19
> **Eiji Takanaka said:**
> Glad you found a solution to your problem =), did you manage to get pulseaudio and alsa working properly again?

So am I! It was driving me insane for weeks. :P
Luckily Pulse and ALSA are working fine again, and I restored the panel applet. Next time I'll test the easier potential solutions first before removing important components. Heh heh.

Thanks again!

-Jennifer

---

### Post by Eiji Takanaka on 2010-12-19
Haha yeah thats sometimes the best way! ;). I'm glad you fixed your system back to normal man, other than the little uninstall/reinstall gem it mighta been kinda hard to ascertain what was wrong with it over the internet, and i could of ended up giving more wonderful 'advice' which complicates matters further. 

Haha how did you restore the applet and fix alsa/pulseaudio operability? (outta curiosity ;) 

Why were those keys messing things up anyways? I mean you fixed it by changing them to different keys right, but are they jammed or anything? Or a bug in the games?

- dan ;)

---

### Post by jendie on 2010-12-19
> **Eiji Takanaka said:**
> Haha yeah thats sometimes the best way! ;). I'm glad you fixed your system back to normal man, other than the little uninstall/reinstall gem it mighta been kinda hard to ascertain what was wrong with it over the internet, and i could of ended up giving more wonderful 'advice' which complicates matters further.

Yeah, it was a very vague, peculiar issue that was hard to explain. Plus, I've only been using Linux for six months. 

> Haha how did you restore the applet and fix alsa/pulseaudio operability? (outta curiosity ;)

Again, another really simple fix. I just had to reinstall indicator-sound via software center. :P

> Why were those keys messing things up anyways? I mean you fixed it by changing them to different keys right, but are they jammed or anything? Or a bug in the games?

My laptop has one of those touch volume controls above the keyboard. When I was using Windows 7 there were no problems, but once I switched to Ubuntu that's when those games had volume issues. So I mapped the volume controls to alt+page up and alt+page down as a quick fix.

There's also an annoying quirk with the touch WiFi indicator. When connected the LED should stay blue, but it flashes between blue and amber whenever data is transmitted.

---

### Post by Eiji Takanaka on 2010-12-19
I don't believe in flattery i think it turns people into proverbial mr hankeys, but if your that competent that you've developed work arounds to the problems you've just aforementioned, and only been using linux 6 months, i think you'll be right at home with linux, lets put it that way. I think the phrase i'm thinking of which i am sadly devoid of the capability to exercise, is 'lateral thinking'. 

I've been using linux a few years now, i do love it, but sometimes i do tend to go for the bazooka to eliminate a simple insect infestation, where a simple boot stomp might suffice, Metaphorically speaking of course. 

But the biggest positive asset, about linux and ubuntu imho, is how much you actually learn. Its like suddenly out of nowhere you become fairly competent at writing scripts, or navigating around the terminal e.t.c.  If we introduced this learn it yourself and dont be a lazy git, mentality at a young age into schools, the help each other and yourself sorta thing, man our species could be so far advanced by now, but noooooooo help yourself, money money money. 

Anyways its late im ranting, kudos to you for solving your problem dudette!

- dan

---

### Post by Eiji Takanaka on 2010-12-19
P.s wifi and ubuntu seems to be a funny one, i had so many problems getting wifi to work on my netbook to start, it wasn't even funny. So i don't think your alone on that one at least ;).

---

### Post by jendie on 2010-12-19
Aw thanks! What really helped me resolve the issue was the amazing community. It just took bouncing some ideas around and lots of Googling to get to the solution. :)

I'm loving it so far. In the summer Lifehacker had a post about Ubuntu, and after going from Windows to Mac and Windows again, I wanted a change. And I'm very glad I tried it. :) I know some say Mint is one of the best distros for beginners, but Ubuntu seemed to be the better option. I completely ditched Windows a few months in, and now I'm slowly converting my family, heh heh.

It's great to be constantly learning new things like new terminal commands and such. Linux is full of options and that's what's so awesome about it. :)

Now I'll end my rant, ha ha! Thanks again and have a good one.

-Jennifer

---

### Post by Eiji Takanaka on 2010-12-19
Not at all dudette, its cool to speak to like minded people. Yeah i know i tried to convert my family but they aren't big fans haha ah well. It was my mums boyfriend who showed me it about 3 years ago now, to start with i was like whoa man, why isn't stuff working!, but once you get past the whole 'i want it all and i want it now!' freddy mercuryesque ;) mindset that previous operating systems seem to propogate, Then it is mega rewarding i think. 

When you develop a work around of your own or approach a problem and working with others overcome or resolve that problem, its super rewarding! With ahem other operating systems you just sit down and someone else has done all the hard work, with ubuntu it feels like everyone tries to chip in best they can, and this working together community is in my view one of the really cool things about ubuntu. 

I've never really tried mac so the verdicts out on that one, but yeah once you decide you can live without windows and embark instead on the good ship mkfs ext4, then it certainly seems you start learning a lot more in general. Perhaps though this is an illusion of knowledge. I think a real test would be losing internet ability for example, if we do not have that knowledge source to tap into, perhaps then is the true test, haha. =P. I think sometimes in todays day and age we rely so heavily on the internet for our knowledge are we actually getting cleverer in general? or merely more competent librarians essentially. 

Who knows.

The point is you've made that first step and your still on your feet, and imho it really is that first step that i imagine most people consider resorting back to the simple way of life of windows. But once you realise just how compromised (haha super spy talk =P) it is in pretty much every way, and how much you start to learn with ubuntu, it would seem like insanity.com to switch back. I was very very tempted to switch back to windows after not having wi-fi working and a couple of other small things, when i first tried it, but im kinda glad i didnt. 

The one bad thing if you will about ubuntu is sometimes the degree to which normal communications are guided onto a slightly crazed politically correct viewpoint.
   I understand why this might be done, but the way in which it is done can and is in my view some what totalitarian, and almost 'brain-washing' If you don't agree with my mind-set sod off sort of mentality. This i disagree with completely, but then if its merely info/help your after and nothing else, this place is great. The way in which people are almost 'shaped' to conform is wrong in my eyes, but then thats probably why i occasionally have little misunderstandings with the powers that be, resulting in infractions and occasional bannings. If they can adjust this slightly so as to maintain a freedom of speech as opposed to oppress/censor what they do not agree with, then i think it would be a totally cool place. This common sense policing approach would perhaps be preferable in the real-world as well as the cyber one, but there we go. =P

Anyways very pleasant chatting with you jen, and glad you sorted your problems sweetheart.

- dan

---

