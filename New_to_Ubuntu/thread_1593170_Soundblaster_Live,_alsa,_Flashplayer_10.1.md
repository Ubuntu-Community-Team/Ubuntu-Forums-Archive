---
title: "Soundblaster Live, alsa, Flashplayer 10.1"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by lotusalive on 2010-10-11
I'm in 'Sound' trouble that I don't quite understand.  Have tried to work it out myself over the past 10 days.  emach has only ever played alsa.
Newly installed SoundblasterLive card HAS WORKED 2x during the past week. 
(Prior to installing it, I think I might have blown my mother-board sound, & Bios is not recognizing the optical DVD-drive...) Reran all Medibuntu, BUT the site for flashplayer 10 is now saying Synaptics has the newer version...  My sound is still not playing on web.  [Sound is just fine on Desktop with both movie & mp3 files.]  The new Adobe Flash "Square" for 32-bit, libflashplayer.so will not install on my system, Err Msg = Unsupported Archive.  I'm using Apache 2 web server.  Will someone direct me, if you know what is happening here ?  Thanks in advance.  :confused::guitar:

---

### Post by lotusalive on 2010-10-11
It's definately the Synaptics Adobe Flashplayer 10.1 update that is not working on my Sys, due to libflashplayer.so = Unsupported Archive.  Flashplayer-installer & Flashplayer free non-free are not working either...  Should I upgrade Alsa, or upgrade to Karmic for this, or just WAIT ? ? ?

---

### Post by lotusalive on 2010-10-12
Also, can someone tell my why it looks like my Filesystem '64' architecture is like defunct ?  the '386 / 686' part seems active, but when I looked at the '64' in attempt to install libflashplayer.so, it was completely inactive... (not that I know much about what I'm looking at, i just couldn't open any of it...)  :confused:

---

### Post by lotusalive on 2010-10-12
Update Mgr for Adobe 10.1 in Synaptic, also has msg: 'Failed to detect distribution.'

In Synaptic, I see under Distribution: 'Always prefer highest version' is ticked.  I tried to change it back to 'Always prefer Jaunty,' but after restart, it defaults itself back to 'Always prefer highest version.'  Is there a way I can 'fix' this ? 

I've added commands for libdvdread4, & css.sh from a previous thread I had on movies.  I've also reinstalled Adobe from web, over-riding 'higher version' that Update Mgr wants to give me, but no web vids are playing at all...  I DID have vid w/o sound, but now I have nothing at all, 'black rectangle' where vid is supposed to be !  Restarting now, for giggles... lol :)

---

### Post by sandyd on 2010-10-12
I think you need -> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by lotusalive on 2010-10-12
Thank YOU, Sandyd :P   Will try there !  [I love my Shiretoko, 3.5.12.  Seamonkey has never installed properly, nor upgraded from their site download on my sys.  Firefox 3.6.10 does not install Adobe Flash any better than Shiretoko, lol :)  And I've been no good at using Konqueror, lol  ;(...]

1st reboot KEPT 'Prefer Jaunty' in Distribution, but 2nd reboot reverted to 'Prefer Highest Version' !  Can't figure that one out...  :confused:

---

### Post by ratcheer on 2010-10-12
By any chance, do you have an onboard sound module as well as the Soundblaster card? If so, your system is probably installing the onboard sound as the "first" sound module, with the Soundblaster next.

If that is what is happening, Flash will never have sound. It MUST use the first sound module detected by your system.

Run alsamixer. Look and see which soundcard it displays on the initial screen. If its not the Soundblaster, you have some work to do on your alsa configuration. Let me know.

Tim

---

### Post by lotusalive on 2010-10-12
Wow T, alsamixer is a bit out of my league, lol :), but yes, SBLive is what it says its seeing First...  I've ticked all Sync buttons to 'on,' & turned up LFE, Center, Surround, & Playback that were all completely turned down...  now must restart browser...  will come back.

---

### Post by lotusalive on 2010-10-12
Also, after Add-On from Sandyd, I have web vid again, still no sound yet. Checking with browser restart.

---

### Post by lotusalive on 2010-10-12
Alsamixergui = Card: PulseAudio, Chip: PulseAudio.  I have 3 screenshots of process, if you want me to post them.  
/proc/asound/version: ALSA Driver Version 1.0.18rc3.

ALSA Mixer (gamix) is where SBLive is showing up as primary.  I've ticked everything Sync and all vols maxed.

I'm LOST, still no web vid sound.  My pal who installed SBLive Card & abso wonder Logitech speaker system could help me.  What should we do ? :confused:

---

### Post by lotusalive on 2010-10-12
I have had web-sound WITH the SBLive Card installed 2x over the past 14 days, but don't know how I did it, partly because of confusion over flash !  Right now, I have all the Synaptic PulseAudio progs installed except the following progs: PulseAudioHALdbg, libsdl1.2debian-pulseaudio, pulseaudio-utils-dbg, vlc-plugin-pulse, libsdl1.2debian-all, flashplugin-nonfree-esound-oss.  Are there any 'sound' progs in Synaptics that someone might suggest for web sound ?  Web games are rendering again, w/o sound, but as I say it has worked 2x during past 14 days with this SBLive Card installed...  Maybe it's Adobe who is messing with the new web configs... ?
All info appreciated. :)

---

### Post by ratcheer on 2010-10-12
Please run "aplay -l" and post the output.

Tim

---

### Post by lotusalive on 2010-10-13
Hi T, thks :)  Output in terminal is merely ">" at both desktop, root, and with sudo before command.  All 'Tests' play sound at System>Sound>Preferences, except 'Audio Conferencing>Sound Capture,' where "Test" plays nothing.  All are set to SBLive! [CT4620] (rev3, serial: 0x211102) Multichannel Playback (ALSA), but Sound Capture is set to same prefix with Multichannel Capture/PT Playback (ALSA).  Default Mixer Tracks Device is set to HDA Intel (Alsa Mixer).  Still no web sound, but desktop movie & mp3 is still sounding great, lol :)

---

### Post by lotusalive on 2010-10-15
This Link is the best 'answer' I've found about adobe flashplayer 10.1 for Jaunty generic kernel 86_64:   [http://plugindoc.mozdev.org/linux-amd64.html#flash]("http://plugindoc.mozdev.org/linux-amd64.html#flash") 
It is in alpha development, currently, requiring removal of all npwrapper.libflashplayer.so software from Synaptic Pkg Mgr.  The main conflict is that doing this would include removing xulrunner, taking out the 3.5 Mozilla Browser with it, kind of moots the point, there. :)  There are other options that might work also, installing a Crossover product is one listed, & there are also instructions for DEB based distributions here that may help, if anyone is suddenly having 'no sound' with the current adobe 10.0 & 10.1, like I am.  (I will post back if this Link happens to get adobe flashplayer working for me.)

---

### Post by lotusalive on 2010-10-16
Solved with the Sound Fixes at: [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html")  Thanks you guys. :guitar:  I should have looked down the page sooner. :):KS

---

### Post by lotusalive on 2010-11-05
Well, this is STILL an Unsolved Thread.  Web Sound has worked only intermittently during the past 30 days.  The fix above that I used for sound is no longer working for me on the web.  I still have desktop sound, but no web sound for a week solid, after tinkering with it quite a bit.  Wish I had a better understanding of why Adobe would let this happen to Linux Users.

I took a look at Google's Chromium, but the Flash downloads would not install on my system, with strange errors for 32-bit downloads.  (I don't care for the Chromium Browser, no toolbar.  Maybe I didn't work with it long enough.)

---

### Post by lotusalive on 2010-11-05
Can anyone tell me why I am getting these error messages ?

> root@lightening-desktop:/home/lightening# aplay -|
> sudo apt-get upgrade firefox
sudo: unable to resolve host lightening-desktop
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Access denied

aplay: main:590: audio open error: Connection refused
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@lightening-desktop:/home/lightening# 


Command works if I'm not at root.

---

### Post by lotusalive on 2010-11-08
I see that I was tired & frustrated, lol, & combined 2 commands, lol, but it still gave me some insights, lol ! :)  > root@lightening-desktop:/home/lightening# aplay -|
> sudo apt-get upgrade firefox

I DID upgrade Firefox, but now it wants me to Configure Java App for x/shockwave, lol, which I don't know how to do !  I started using AskUbuntu for that question of java, but still no reply...  I know you all are really busy.  I found AskUbuntu, read Mo's Blog too, as a result of Flash-Aid & FlashVideoReplacer not working for me in 9.04-9.10.  I know what's happening with the web, is just another of the many changes of leaps & bounds we've all had to make over the years of desktop/web, lol, i'm lucky to have been a long time observer, so, in case you don't know it, I really, really, appreciate you all SO MUCH for all you've done for me over the past 2 years...:KS:KS

---

### Post by diablo75 on 2010-11-08
> **sandyd said:**
> I think you need -> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

+1

Came in here to suggest the same extension.

---

