---
title: "lucid lynx - no sound"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-05-09
Hi Ubuntu Community:

I installed lucid lynx last night and the sould worked well...

However, this morning it doesn't work! :(

When I click on that speaker icon on the upper panel,  "mute all" is displayed.

When I click on the preferences banner on the speaker icon, "CA0106 Soundblaster" is selected under the hardware tab, and "CA0106 Soundblaster" is selected unde the output tab.

How do I get sound to work??

Thanks,
Phil

---

### Post by SKhan on 2010-05-09
i also couldn't get sound. altough vlc is playing audio files and hardware seems to be working.

---

### Post by camaron1 on 2010-05-09
> **Phil Smith said:**
> Hi Ubuntu Community:

I installed lucid lynx last night and the sould worked well...

However, this morning it doesn't work! :(

When I click on that speaker icon on the upper panel,  "mute all" is displayed.

When I click on the preferences banner on the speaker icon, "CA0106 Soundblaster" is selected under the hardware tab, and "CA0106 Soundblaster" is selected unde the output tab.

How do I get sound to work??

Thanks,
Phil

Do you have more than one sound card in your box? If that is the case the default one can change randomly on every reboot. It happend to me. There is an easy fix for it. Let me know.

---

### Post by SKhan on 2010-05-09
> **camaron1 said:**
> Do you have more than one sound card in your box? If that is the case the default one can change randomly on every reboot. It happend to me. There is an easy fix for it. Let me know.

I don't know about the original poster of this thread. but i have two sound cards. and both are not working. i tested my speakers on both. although audio files are played by vlc but there is no sound from speakers and headphones.

---

### Post by QueenZ on 2010-05-09
I also have the same problem, except i have very low sound but it varies from boot to boot. Sometimes when i start up my computer it has normal (loud) sound but other times it has very low sound.. What could be the problem?

---

### Post by camaron1 on 2010-05-09
> I don't know about the original poster of this thread. but i have two sound cards. and both are not working. i tested my speakers on both. although audio files are played by vlc but there is no sound from speakers and headphones.

OK, this is what it has worked for me in the last 3 Ubuntu releases:

**[SIZE="4"]To get your sound working:[/SIZE]**

On a terminal:  **gksudo gedit /etc/pulse/default.pa**
This will open gedit with administrative privileges. Click on **Edit** and then **preferences**. **Click Display line numbers**. On lines 45 & 46 find:

45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove sign **#** from both. Save and reboot.

[SIZE="4"]**To stop Ubuntu from switching sound cards**[/SIZE]

On a terminal:  **cat /proc/asound/modules**
This will list the names of your sound-cards. 
Now on a terminal: **sudo gedit /etc/modprobe.d/alsa-base.conf**
At the very end of the file, add the following (assuming you have 3 cards with names A, B and C and you want to have them in the order CAB) 

options snd-C index=0
options snd-A index=1
options snd-B index=2

Save and reboot.

I really hope it helps, I did the trick for me

---

### Post by QueenZ on 2010-05-09
I have been having these sound problems for the last 2 or 3 versions as well.. Thanks for for the advice, will try.

---

### Post by Old Jimma on 2010-05-09
Hi All:

I've tried the recommendations.

I'm gonna revert to Hardy Herron LTS until August. 

See you then!

All the best,
Phil

---

### Post by fooman on 2010-05-09
have you tried installing the gnome-alsamixer package?  open a terminal and type or copy/paste the following:

```
sudo apt-get install gnome-alsamixer
```

then find it in: applications > sound & video > gnome alsa mixer

adjust the volume sliders there....make sure none are muted.

hope that helps.

---

### Post by QueenZ on 2010-05-09
I think you can also try removing the .pulse directory from your ~home folder..
then restart and see if it helps

---

### Post by Franknfurterhotmale on 2010-05-09
None of the above worked for me.

The operating system freezes every five minutes and has to be unfrozen by pulling the plug.
Doing the two edits above made the freezing worse.
Undoing the soundcard order one made no difference.
I'm running it as a dual boot with Win XP, so I can now say, comparing two OS on the same hardware, that I've actually found something that's worse than Windows. 


Frank

---

### Post by Old Jimma on 2010-05-09
Hi All:

Thanks for your recommendations. 

I wanted to get back to the community here at this thread because I relized that my last post sounded spiteful...

I had to revert to Hardy because I've tried the recommendations listed here and elswhere. 

However, the biggest reason why I really had to revert to Hardy is because I am a musician (and not a very good one, at that). I use Ubuntu and Audacity in my work.

Because I'm a musician, if sound isn't working and after a fair amount of trying to get it to work, I don't have much of a choice but to revert to an older LTS that provided sound... I cannot do my work without it.

I hope this smooths over some of the feathers that I may have inadvertently ruffled. 

I was extremely encouraged by a new developement in Lucid that is well worth noting for mucicians.... in particular, Audacity has all of the effects working in Lucid (they all don't work in Hardy.. but sound works). For example, the "change tempo without changing pitch" option works in Lucid. THis helps musicians slow down phrases they hear so that they can learn exactly what other artists are doing. It is a very important feature to have.

Well... I'll be back to Lucid... probably try it in a few months again.

All the best,
Phil Smith
Duluth, GA

---

### Post by norm7446 on 2010-05-09
Not to put a spanner is the Lucid works but mine. every now and again, will boot with no sound. Then when I try to restart it only take me to the login screen. I have to manually hold the Power switch on me base unit till it goes off. But when it restarts the sound is back !!!!! Weird with a Capital We.

---

### Post by eMJayy on 2010-05-09
I guess I should add my two cents to this discussion, as I'm having the same issue as of this morning. But my story actually goes back a few days, so I'll start from the beginning...this is going to be a little wordy. 

A week ago I upgraded this machine ( a machine I built 3 weeks ago) to Lucid from Karmic. At the time of the upgrade, I was actually using the motherboard's onboard audio chip, which is a VIA VT1708S. It played 2 channel audio out of the box in both Karmic and Lucid, but it has a 5.1 HD audio feature on the onboard chip that I was hoping might have drivers in Lucid, but there weren't any. So I decided to use my Soundblaster Audigy SE card from my older box, which has worked flawlessly in Ubuntu for two years and has up to 7.1 HD audio support out of the box. 

I turned off onboard sound and installed the card and tried watching a movie in 5.1 surround to verify it was working correctly. It worked for about 20 minutes but then Xine suddenly lost sound and reported than something else was now using the audio. Since I was using Pulseaudio, I figured that something that was using Alsa might have interrupted it. Sound returned once I restarted Xine or ran any software that played back audio using pulseaudio. I tried playback of the movie with VLC and the same thing occurred there too after several minutes of 5.1 playback. Music playback through Rhythmbox was ok and wasn't interrupted at all. It was just 5.1 sound that was the problem. 

I then checked the syslog and saw this message:

[B]pulseaudio[1389]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
pulseaudio[1389]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ca0106'. Please report this issue to the ALSA developers.
pulseaudio[1389]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.[/B]

Every time the sound cut off, this message was recorded in the syslog.
The problem didn't seem to trigger very often when I used Movie player or SMPlayer, so I've used those to watch movies for the last couple of days. But this morning, sound suddenly disappeared...completely. There's no startup sound. And when I checked the syslog, sure enough there is that message appearing each time the machine is booting. My audio card is being detected, and is configured correctly. All volume setting are unmuted, including those in 'alsamixer' accessed through the terminal. I think the key to the problem is that message in the syslog. 

I was planning to do a clean install of 64-bit Lucid on this machine next weekend (I'm actually on 32-bit Lucid right now), but I think I'm going to have to do it today.

Oh, there was one thing that I forgot to mention, although I'm not sure it had anything to do with this issue. When I first ran Lucid for the first time, I encountered a problem with Rhythmbox crashing on startup. I checked the syslog and found that the problem was being caused by a component of Samba. Once I uninstalled Samba, Rhythmbox stopped crashing. I had actually installed some required Samba components a few days prior to updating to Lucid, because I wanted to network this machine to an older one to retrieve files. 

Other than this issue, Lucid is running stable on this machine.

---

### Post by eMJayy on 2010-05-09
Guys, could this be a recurrence of this bug?

[https://bugzilla.redhat.com/show_bug.cgi?id=425763](https://bugzilla.redhat.com/show_bug.cgi?id=425763)

This is looking an awful lot like my problem. In my syslog, this is what I'm seeing.

**pulseaudio[18470]: pid.c: Stale PID file, overwriting.**

And then a little later, this:

**pulseaudio[18476]: pid.c: Daemon already running.**

and then this:

[B]pulseaudio[18477]: pid.c: Daemon already running.
May  9 12:38:08 pulseaudio[18470]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
May  9 12:38:08 pulseaudio[18470]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ca0106'. Please report this issue to the ALSA developers.
May  9 12:38:08 pulseaudio[18470]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.[/B]


It seems to me that the issue being discussed in that bug report might be the cause of the problem I'm seeing here on my system.

---

### Post by SKhan on 2010-05-10
> **camaron1 said:**
> OK, this is what it has worked for me in the last 3 Ubuntu releases:

**[SIZE="4"]To get your sound working:[/SIZE]**

On a terminal:  **gksudo gedit /etc/pulse/default.pa**
This will open gedit with administrative privileges. Click on **Edit** and then **preferences**. **Click Display line numbers**. On lines 45 & 46 find:

45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove sign **#** from both. Save and reboot.

[SIZE="4"]**To stop Ubuntu from switching sound cards**[/SIZE]

On a terminal:  **cat /proc/asound/modules**
This will list the names of your sound-cards. 
Now on a terminal: **sudo gedit /etc/modprobe.d/alsa-base.conf**
At the very end of the file, add the following (assuming you have 3 cards with names A, B and C and you want to have them in the order CAB) 

options snd-C index=0
options snd-A index=1
options snd-B index=2

Save and reboot.

I really hope it helps, I did the trick for me
Thanks. I will try it but before that i wanna make it clear that one of my card is turtlebeach santa cruz card. while the other is built-in card my on dell optiplex gx270 desktop computer.
i wanna keep santa cruz. and wanna disable built-in card.
where can we see/enable/disbale hardware?

---

### Post by camaron1 on 2010-05-12
> Thanks. I will try it but before that i wanna make it clear that one of my card is turtlebeach santa cruz card. while the other is built-in card my on dell optiplex gx270 desktop computer.
i wanna keep santa cruz. and wanna disable built-in card.
where can we see/enable/disbale hardware

Give **index=0** to your preferred card and **index=1** to the other one (the on board card)

---

### Post by SKhan on 2010-05-12
> **camaron1 said:**
> Give **index=0** to your preferred card and **index=1** to the other one (the on board card)

thanks. issue solved. :)

---

### Post by camaron1 on 2010-05-12
> thanks. issue solved

Glad it worked for you

---

### Post by lidex on 2010-05-12
You can disable onboard sound in the bios.

I would recommend updating kernel and alsa packages as a generic first step in lucid. 
Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

If you have upgraded to lucid you may have old config files that may need to be removed. Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
I have also seen borked alsa installs in lucid upgrades, you may want to re-install or use the upgrade script in my sig.

Alsa defaults to muted levels so be sure to check alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

If you are experiencing a bug, please use link posted previously to report so it can be fixed. For any other issues ***please start a new thread*** and detail the problem you are having. Posting this info will be helpful as well:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by eMJayy on 2010-05-14
I figured out why I lost my sound. 

Apparently, there's an issue (very likely a bug) that caused my Audigy card to be switched from analog to IEC958 digital output at the level of Alsa. Changing the PulseAudio settings, therefore, had no effect. 

The solution was to install the GNOME ALSA Mixer from the software center and select **analog source** instead of *IEC958*.

---

### Post by wavesound on 2010-05-16
> **fooman said:**
> have you tried installing the gnome-alsamixer package?  open a terminal and type or copy/paste the following:

```
sudo apt-get install gnome-alsamixer
```

then find it in: applications > sound & video > gnome alsa mixer

adjust the volume sliders there....make sure none are muted.

hope that helps.

HI All seems I have no sound or no alsamixer now.
Was all working with my delta card even spotify was working but alas its now silent.
I'm sure some of the Devs hate sound/Music, always seem to be broken on an upgrade then eventually fixed

---

### Post by camaron1 on 2010-05-16
> HI All seems I have no sound or no alsamixer now.
Was all working with my delta card even spotify was working but alas its now silent.
I'm sure some of the Devs hate sound/Music, always seem to be broken on an upgrade then eventually fixed

It could just be a case of random switch of default card. just type **alsamixer** on a terminal and press enter. On the upper left hand side you'll see the name of your *current* default card. If it is not your Delta card follow the steps given in my previous post. 

And yes, you are right. After every installation the one and only thing I have to spend a few hours googling about, the bloody configuration files I have to twist till they bleed is sound (or the lack of)

Good luck

---

### Post by Old Jimma on 2010-05-18
Hi Y'all Ubuntu Community:

I was the guy who started this thread a while ago, and decided to look at the discussion again today.

Wow! THere were more than 1000 visits to this discussion!

Is there anybody out there who can outline a solution to "no sound" in lucid? 

It would be very helpful if the outline were written for the Complete Idiot (like me).

Yours truely,
Phil Smith
Duluth, GA

---

### Post by gazer22 on 2010-05-19
In my case, I usually have to mute and then unmute the sound from the volume applet in the panel after starting the laptop or resuming from a suspended state.

Would like to figure out how to avoid doing that, but at least I can get sound!

---

### Post by gazer22 on 2010-05-19
I'd recommend installing the pulse audio volume control (pavucontrol from synaptic) or:
```
sudo apt-get install pavucontrol
```

This should install "PulseAudio Volume Control" under "Sound & Video"

It breaks down what applications are playing (or trying to play sound) and what sounds should be getting to your speakers.

I've found it to be a nice way to see if something is muted when it shouldn't be.  Amazingly, most of my recent sound problems has been things randomly reverting to a muted state.

---

### Post by Old Jimma on 2010-05-19
Hi All:

I did a fresh install of Lucid from Hardy this evening and I was able to get sound to word very easily for the apps that matter to me. Here is what I did:

1. Audacity: edit > preferences > device. Then I chose the sound card I wanted to use. Then: edit > preferences > host. Then I chose ALSA.

2. Then on that speaker icon on the upper panel, sound preferences > hardware then I chose my soundcard. ALso, sound preferences > output then I chose my soundcard, again.

Sound now works very well.

Lucid is really great for musicians! Audacity has all of the nice features a musician would routinely want! Especially effect > change tempo

I hope Lucid works out for you, too!

Many thanks for the contributors to this thread who provided hope that I could get Lucid working well!

Phil SMith
Duluth, GA

---

### Post by lilychef on 2010-06-07
Thanks, camaron1.... Your suggestion worked for me.  My original thread can be found [here]("http://ubuntuforums.org/showthread.php?p=9424831#post9424831")...  Why do you suppose, those settings got changed in the first place?  Seems weird to me that stuff would all of the sudden stop working like that....  Thanks again!

---

### Post by camaron1 on 2010-06-07
> **lilychef said:**
> Thanks, camaron1.... Your suggestion worked for me.  My original thread can be found [here]("http://ubuntuforums.org/showthread.php?p=9424831#post9424831")...  Why do you suppose, those settings got changed in the first place?  Seems weird to me that stuff would all of the sudden stop working like that....  Thanks again!

Glad it worked for you. As I said, sound is the thing I always have to straggle to get working so I'm only happy to offer what worked for me to others. As to why this happens.... who knows eh? :)

---

### Post by Zol666taN on 2010-07-24
Thanks QueenZ : "removing the .pulse directory from your ~home folder.."

That one worked for me.

I first tried the "sudo edit on /pulse/default + restart .... " => NO result.

FYI -

I am on LL10.04 since 2 weeks - after KK9.04 since 2009/10 -
laptop is MEDION (ASUS hardware, I think) P7612 - Akoya.

Every thing works fine except Wireless (have to do it : did not work on KK either).

---

### Post by bbusenius on 2010-07-31
> **QueenZ said:**
> I think you can also try removing the .pulse directory from your ~home folder..
then restart and see if it helps

This worked for me. I updated from Karmic to Lucid. Every time I restarted my computer I would have no sound and would have to open gnome-alsa mixer to boost the levels manually. Uncommenting lines 45 and 46 mentioned in a previous post caused me to loose the functionality of my volume control buttons and when I put the comments back I lost sound entirely, however, deleting the .pulse directory in my home directory *did* fix the problem. Now I have sound even after reboot.

1. Delete the .pulse folder in your home directory ~/ (I moved and renamed mine just in case)

2. open gnome-alsa mixer and move turn the sound levels up on everything.

3. restart your computer and your settings should be preserved.

---

### Post by fopetesl on 2010-11-30
> **camaron1 said:**
> OK, this is what it has worked for me in the last 3 Ubuntu releases:

**[SIZE="4"]To get your sound working:[/SIZE]**

On a terminal:  **gksudo gedit /etc/pulse/default.pa**
This will open gedit with administrative privileges. Click on **Edit** and then **preferences**. **Click Display line numbers**. On lines 45 & 46 find:

45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove sign **#** from both. Save and reboot.

I really hope it helps, I did the trick for meDid the trick for me also :p
Thanks for the tip :lolflag:

---

### Post by camaron1 on 2010-11-30
> **fopetesl said:**
> Did the trick for me also :p
Thanks for the tip :lolflag:

Glad to hear that ;)

---

### Post by Curbuntu on 2011-09-14
> **QueenZ said:**
> I think you can also try removing the .pulse directory from your ~home folder..
then restart and see if it helps

This worked for me, too, on Lucid.  Thanks very much!

---

