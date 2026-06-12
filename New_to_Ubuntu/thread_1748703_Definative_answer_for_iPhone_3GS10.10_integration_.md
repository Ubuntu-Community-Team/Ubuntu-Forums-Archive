---
title: "Definative answer for iPhone 3GS/10.10 integration? Please."
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Murray Wight on 2011-05-03
Hi all.

New to Linux/Ubuntu. Big isn't it? Wow.

Problem is i can't get my iPhone 3GS to play with my desktop.

Ubuntu sees it but can't mount it. The one time i imported some code from somewhere from within the maze of these forums, it worked, but then stopped with a lock down error and i have never been able to reproduce it OR find the instructions/code again.

Could someone, for the sake of my sanity, PLEASE help with a definative set of instructions OR a link to a set of complete instructions.

I am seriously considering getting my iMac back off my daughter over this. iPhone connectivity is critical to my needs.

All help appreciated and apologies if you guys have to go over this again, but i really did try to search and fix by myself.

Cheers
Murray

Sorry, Dell laptop Ubuntu 10.10 iPhone 3GS iOS 4.3.1(?) (latest)

---

### Post by Murray Wight on 2011-05-03
bump

---

### Post by Murray Wight on 2011-05-04
Bump. Sorry about this. I'm desperate.

---

### Post by jamesjenner on 2011-05-04
G'day mate,

Sorry but I cannot give you a definitive answer, however I'm in a similar situation. 

Under 10.10 I never could get my iPhone 3GS to work. Under 11.04 I was amazed to see my iPhone to come up and I could even see the music on it via the Banshee media player. I just presumed everything was working so after much stuffing around I found out that the last update from Apple stops Bashee from working with the iPhone. I presume they're working on it but no go right now.

I can however with the latest Banshee manage my Podcasts. Don't try and manage music however as there appears to be some problem in being able to convert the sound files when transferring to the iPhone and it ends up being one big mess. Also if you try and transfer your music from your phone to your computer, well don't bother. The music isn't converted back to MP3. 

Based on what I've seen I suspect that it will work in the future and I think I read somewhere that your fine if you jail break your phone (not something I'm willing to do). 

Hmm... I do have a spare phone though, maybe if I get time I'll give jail breaking a crack.

Cheers,

James

---

### Post by Murray Wight on 2011-05-04
Thanks James.

Upgraded to 11.04 and nearly vomitted all over my screen. Too scared/ignorant to try again even with classic settings but will do it in a thrice if the 3GS works.

It worked for you out of the box?

Cheers
Murray

---

### Post by jamesjenner on 2011-05-04
> **Murray Wight said:**
> Upgraded to 11.04 and nearly vomitted all over my screen. Too scared/ignorant to try again even with classic settings but will do it in a thrice if the 3GS works.

My initial reaction was negative. I wasn't keen on the changes at all. However I have a personal policy of not trying to customise the heck out of my OS as IMHO it makes it difficult from a maintenance point of view. 

After giving it a chance over a few days (and finding a very handy reference for the keyboard shortcuts) I actually found it quite nice, like the extra space for the desktop and find the shortcuts quite intuitive and helpful (especially the window control related shortcuts, they're fantastic).

I should say that I'm pretty biased in always trying out developments in the area of UI.

> **Murray Wight said:**
> It worked for you out of the box?

Well kinda, these are the problems I found:

[LIST]
[*]Sometimes you connect the iPhone and it doesn't work and if you disconnect and reconnect it works fine (slight annoyance, work around possible, just reconnect).
[*]You cannot copy music to the device (note I only have MP3's, may be a different issue with the apple encoded music, i forget the type).
[*]When I tried to transfer music from my iPhone to Linux it removed my playlists. This may actually have been caused by replicating podcasts to the iPhone. It copies the files but as is (weird file naming convention that Apple use, and no conversion to Mp3), i suspect if you rename and have the right codec support you could play them, i didn't bother.
[*]Some unusual behavour with the replication of podcasts to the iPhone. I subscribe to Coffee Break French, which has quite a lot of podcasts. The first replication put half under one title and half under another. The second time it put all but one under one title and the rest under another. Not sure what the deal is with that.
[/LIST]

Things that worked out of the box:
[LIST]
[*]Able to see application file area, which apparently lets you access files that the apps can generate. If the apps support it. I think this is more a benefit for jail broken iPhones but not sure.  Not sure if you can transfer files to it, didn't try.
[*]Can play music from your iPhone via your Computer
[*]You can see the photos and transfer them.
[/LIST]

Personal opinion of Banshee is that it's incredibly slow. Not sure if it was because of my iPhone being connected, I should experiment. However if you change from one playlist to another it seems to take a while to register. Doesn't have customisable sort options that I could see. Though I could update multiple tracks and has an option to change mp3's when you update info about the songs (didn't test, just noticed the option). 

Of course I haven't done proper testing, just my subjective experience over the weekend just gone, your experience may vary. If you have the older version of the iPhone firmware then you could try banshee on 10.10, I don't believe there is any special reason why it would only work on 11.04 other than they changed the default media player (it may not work on 10.10, but from the results when i was searching, I get the impression that it does).

Hope that helps mate.

---

### Post by Murray Wight on 2011-05-04
Thanks James. Good stuff.

I made the jump from Mac OS X Snow Leopard to Ubuntu 10.10 to 11.04 over about a three day computer centered haze, i was a dribbling mess afterwards. Not being able to use my iPhone at the end of the process was a real let down.

I will try again. First I will upgrade 10.10 to 64bit then have another go at 11.04 with classic setup and take it from there.

I really appreciate your input, maybe together we can optimise the setup.

I will report back here later today/this evening.

Have you looked at joining local Ubuntu groups? Might give that a go too.

Cheers
Murray

---

### Post by CVGH on 2011-05-04
Have you tried this:

```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```Works on my iPhone 4 ok, get a dbus error but mounts ok and can see pix and audio...

This is where it comes from:

[http://www.libimobiledevice.org](http://www.libimobiledevice.org)

Brian

---

### Post by Murray Wight on 2011-05-05
Hi Brian. Yeah, tried that. No go. Thanks anyway.

Well Brian and James, and anyone else interested, I have solved the problem as it affects me.

In short, 11.04 works out of the box. Perfect. I even have apps that store files (diary, etc) that I usually have to sync through iTunes that i can get direct access to, in text mode, with the standard file browser on 11.04 classic desk top. Lovely. My computer is so fresh it has never even heard of iTunes let alone require it.

Whether or not all the other functions (video, audio, etc) work is not the point here.

I could NEVER get 10.10 and my 32Gb iPhone 3GS with iOS4.3.1(?) to mount. This solves that problem for me and may help others.

I have a Dell 1545 laptop, Intel Core Duo, 2.1GHz, running 64bit, 3GB, 320GB. I started with Live CD 10.10 from Ubuntu User cover. Installed 10.10. Accepted all upgrades offered by Update Manager(***Except "Upgrade to 11.04"***). Would not mount iPhone. So that's a standard 32 bit install AFAIK.

I then upgraded, from the Ubuntu User's next cover, to the 64bit version of 10.10. Same procedure through Update Manager but this time accepted the 11.04 upgrade option offered.

Reboot. Login under Classic Desktop. Connected iPhone and BAM. There it was. So, I'm sold.

So that's 10.10 32 bit upgraded to 64 bit upgraded to 11.04 (64 bit, I geuss).

Having said that, I think that this is the point that libmobile(?) and others can be used. I will have a play but, as I said, A greenfields install of 11.04 solved my 'mounting' "DBS error" style problems flat.


Good luck
Cheers
Murray

---

### Post by jamesjenner on 2011-05-06
> **Murray Wight said:**
> Having said that, I think that this is the point that libmobile(?) and others can be used. I will have a play but, as I said, A greenfields install of 11.04 solved my 'mounting' "DBS error" style 

Hmm maybe that is were I went wrong. I'm similar to you in that I'm running 11.04 64. However I did an upgrade. I should note that I hadn't bothered to try and get my iphone working previously, so I didn't have anything installed that was trying to connect to th iphone.

Do you get the following three windows when you connect your iPhone?

[LIST]
[*]you have just inserted a medium with digital photos. Choose what application to launch. *defaulting to Shotwell Photo Manager*
[*]You have just inserted  a digital audio player. Choose what application to launch. *defaulting to Banshee Media Player*
[*]Documents on <phone name>'s *iPhone opened in whatever you call the file browser*
[/LIST]

Beware though that transferring mp3's is a big headache and you may loose your play lists and songs. Googling turned up a lot of problems in this area.

Oh do you get performance problems in Banshee? I find changing what is selected (a playlist, the phone, another playlist, etc) has a large delay before it shows what you tried to do. I only have around 1000 songs (mp3's) in the library, 7 playlists and maybe 100ish podcasts of around 15 mins each.

Cheers,

James.

---

### Post by Tony Flury on 2011-05-06
Only answer I found was Virtual Box and Windows XP Guest OS.

I could not get an Linux application to recognise the Phone, and sync it, so now - I run Itunes under my Guest OS. Simples.

---

