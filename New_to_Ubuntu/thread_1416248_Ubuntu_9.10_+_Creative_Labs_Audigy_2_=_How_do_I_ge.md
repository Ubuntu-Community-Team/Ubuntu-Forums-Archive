---
title: "Ubuntu 9.10 + Creative Labs Audigy 2 = How do I get 5.1 sound and the mic working?"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by diablo75 on 2010-02-25
I just replaced the onboard sound on my computer with an old Audigy 2 ZS that I had laying around in another unused PC that I have used for several years in and out of many computers over the years.  Never had a problem with it.

I did disable the on-board audio chipset in the BIOS so it wouldn't interfere and it does not show up in my sound configuration any more.  So when I open up my Sound Preferences, I see this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148242&stc=1&d=1267148280[/IMG]

I managed to find the huge fan-out list that shows me other configurations that the card could be put into, such as "Analog Surround 5.1 Output" and so on.  Here's what that looks like:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148243&stc=1&d=1267148483[/IMG]

The multitude of options from this screen is rather confusing, but I realize it's all there so as to be available to the numerous kinds of audio cards out there besides my own and their own hardware capabilities.  All I want is for my 5.1 output to work (Front L/R, Rear L/R, Center and Subwoofer) and for my microphone to work.  Well... doesn't work out the way I'd hope.

If I select, say, "Analog Surround 5.1 Output" and then proceed to play something like a movie, the audio is extremely "tinny", as in... it sounds like it's being played back on a speaker made out of tin or aluminum.  In other words, horrible.  Even restarting the system to try again produces the same result.  Reverting back to "Stereo Duplex" makes things sound well.  So at the least I can have stereo sound...

But then there's the problem with the mic.  Before I type anything more about it, I should preface by stating that I tested the Mic using my Windows XP partition and had no problems with it, so I know it's plugged into the correct jack...

Anyway, in the Sound Preferences box, I've tried all of the options in the list that include "Mono input" or "Stereo Input" and attempted to do a Skype test call, but nothing is heard by Skype.  I've also attempted to record audio using Audacity but it didn't pick anything up either.  What's more confusing to me is that there is just one input listed there in the first place... which made me think about the Line-In jack on the sound card... why isn't there an option in the list that includes two inputs (Line In and Mic), because there's at least that many aren't there?  If we're cutting it down to one, are any missing?  And if so, which one?

So basically it would seem that right now I'm limited down to stereo only output and no mic input that works.  What should I do?

---

### Post by smmalmansoori on 2010-02-25
Check out the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by diablo75 on 2010-02-26
Thanks for the link to that troubleshooting guide but it wasn't much help.  I read the entire first post and it looks as though it's intended to be read by people who aren't getting any sound at all.  It walks you through the steps to see if your card is being detected, and mine is.  It walks you through the two different ways to reinstall the modules that enable the card to work, and I used the apt-get method to purge and replace mine with a fresh copy and reboot.  That didn't work.

So then I decided to just start from scratch and reinstall the OS.  The thing about my setup is I did a manual partitioning so that 80 GB are for my / partition, and a much larger partition is my /home.  So when I need to reinstall, I just format the / partition and set mount points for it and the /home, leaving /home untouched.  When I fire the new install up for the first time, everything on my desktop (with the exception of additional software not included by default) is just the way I left it.  And I was kind of disappointed to see that this included the settings within my Sound Preferences.  Stereo Duplex was still selected, even the little sound alerts theme (Bark) was still selected, and the MIC still doesn't work (tested with a fresh install of Audacity).

So what this looks like to me is, some sort of setting is screwing things up and it's in one of the hidden files/folders in my /home folder.  I started by renaming the /.pulse folder to /.pulseOLD and it replaced it with a fresh one on reboot but the settings were still the same as before, so that wasn't the one I needed to erase.  And after thumbing through several other places I'm not sure what else I can try to remove/rename to see if it will replace the necessary settings with what I need to get my soundcard to work right.  Any ideas?  Because, to be honest, this seems more like a problem with Pulse Audio than it is kernel modules.

---

### Post by diablo75 on 2010-02-26
UPDATE:

I did a:

```
sudo apt-get purge pulseaudio
```

and rebooted.  Sound worked.  In fact it works a lot better.  I popped in my 5.1 surround sound copy of NIN's Downward Spiral (which I've been using for testing since this fiasco began) and VLC now offers under the Audio>Devices> menu 5.1 sound, which never was an option while running with PulseAudio.

I installed alsamixergui and used it to play around with the sound levels and they respond the way they're supposed to.  Though I wasn't yet able to get the mic working.  I didn't spend more than a few seconds trying because I wanted to see what would happen if I reinstalled pulse audio.

So I installed PulseAudio again, rebooted.  And we're back to square one.  Pulse thinks my cards default should be stereo sound and the mic still doesn't work.

I'd like to remove Pulse once and for all and get the old mixer icon back on my upper panel like what used to be there back in the days of Ubuntu 7.10.  Anyone know how to do that?

---

### Post by piratemurray on 2010-03-10
I don't have the exact same problem with 5.1 but I too have Audigy 2 and Pulseaudio problems.

I got round this by doing a purge of Pulseaudio on Karmic as you did. But since installing Lucid Pulseaudio has come back and my problems are reoccurring.

Is Pulseaudio just sh*t or is it just sh*t with an Audigy 2 card?

Also running 64bit if that makes a difference in the discussion?

---

### Post by J V on 2010-03-10
Pulseaudio is very good, but like most things linux, not on everything, thats why we have 10 ways to do anything, one at least will work :)

Architecture shoulden't make a difference with audio

---

### Post by ratcheer on 2010-03-10
I am using Karmic, ALSA, and Pulse Audio with an Audigy 2 card. I have it set to 5.1 output and the sound is good, although I am not certain it is actually 5.1. I honestly have more trouble configuring ALSA than PA. And I don't use a microphone, so I have no idea about that part of it.

Tim

---

### Post by diablo75 on 2010-03-10
I managed to make good without pulse.  This thread might help those who are trying to get away from it:  [http://ubuntuforums.org/showthread.php?t=1417544](http://ubuntuforums.org/showthread.php?t=1417544)

---

### Post by Objekt on 2010-03-10
I'm quite confused.  As you can see in my signature, I have exactly the same sound card as the thread starter, and am also running Ubuntu 9.10.  Yet I do not have microphone problems.

I do have other PulseAudio problems, or more properly, problems with a minority of applications.  A few (Teamspeak 2 and 3, I'm looking at you!) do not play nicely with PulseAudio, mostly because the app's developers just don't care.

I've tried removing PulseAudio entirely, but after doing so I had NO sound.  Because I couldn't figure out how to configure ALSA, I reinstalled PulseAudio.

I also have a motherboard with built-in sound, some sort of Analog Devices chipset, which I do not use since I installed the Audigy.  However, I did not have to disable the built-in sound in BIOS to get the Audigy to work.  I simply don't have anything plugged into the built-in sound's jacks, so I never hear from it (pun intended).

All that aside, I have not tried any of the multi-channel sound options, beyond stereo.  I cannot do it in Windows either, as I do not have the required hardware.  I have neither multi-element, surround sound headphones, nor multiple speakers (Altec Lansing VS 4221 here).  So for all I know, 5+ channel sound wouldn't work.

---

