---
title: "going round in circles trying to get flash working firefox"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by jasonwatkins on 2009-04-12
Ok, i've returned to linux after a long while so i'm still kind of finding my linux feet again somewhat.

i'm trying to get flash working in firefox and not really getting anywhere and i'm starting to get a bit stumped.

i should also point out that i'm actually using the KDE release of linux mint V6, which has the guts of Intrepid Ibex (8.10) as far as i'm aware so i'm hoping the general principle will be the same - anyway, you guys on the forum are better than them ;)

What i've tried so far ..

In Synaptic : uninstalling flashplugin-nonfree and installing adobe-flashplugin
                   uninstalling adobe-flashplugin and re-installing flashplugin-nonfree
                   installing both
                   installing neither (obviously that won't isn't going to work but it was worth a try ! :D)

searching these here forums for "flash problems" and trying ..

```
apt-remove --purge -y flashplugin-nonfree nspluginwrapper
apt-install flashplugin-nonfree
```

also downloading the .deb package directly from adobe, which is 'install_flash_player_10_linux.deb' and installing that.  it tells me there is a newer version in the software channel, but i still try this one anyway.

i've also tried ..

```
aptitude purge flashplugin-nonfree flashplugin-nonfree-extrasound adobe-flashplugin nspluginwrapper
```

and then

```
aptitude install flashplugin-nonfree
```

i've also tried downloading the tar.gz version of the latest flashplugin and copying the libflashplayer.so file to /usr/lib/mozilla/plugins and also to /usr/lib/firefox-3.0.8/plugins.

i've also tried downloading and installing version 9 of the flash plugin.

and .. NOTHING works .. when I go to youtube, or try and play a game, i just get an empty square where the flash content should be.   is it a case of me not seeing the wood for the trees ?

any help greatly appreciated .. thanks ..

---

### Post by Eisenwinter on 2009-04-12
Go to the adobe website, get the file called libflashplayer-<something>.tar.gz, save it to your home directory.

Open up the terminal:

```
tar xvf libflashplayer-[press tab to complete the filename]
mkdir ~/.mozilla/plugins/
mv libflashplayer.so ~/.mozilla/plugins/

```

Make sure you do this while firefox is **closed**.

Restart firefox after doing it, and go to some website.

If firefox crashes when you go to websites with flash in them, open up the terminal again, and do this:
```
sudo apt-get install curl
```

---

### Post by jasonwatkins on 2009-04-12
sorry, but that didn't work.

what i did ..

ran this first to start with a clean slate

```
aptitude purge flashplugin-nonfree flashplugin-nonfree-extrasound adobe-flashplugin nspluginwrapper
```

then 

```
apt-get clean && apt-get autoremove
```

installed the adobe plugin from synaptic

did what you said, got the tar.gz file from adobe (install_flash_player_10.tar.gz) and extracted it.  made the plugins directory in $HOME/.mozilla and moved the libflashplayer.so into it

restarted firefox, went to youtube and still get a blank, empty box where the youtube video should be.

tried installing curl as well at that point, but still get a blank box.

i then tried uninstalling the ubuntu restricted extras package in synaptic and installing the kubuntu restricted extras package instead, tried all of the above and still nothing.

sorry to be such a pain :)

---

### Post by jasonwatkins on 2009-04-12
still trying to get this going without any luck - going to try and re-install the ubuntu restricted extras on the command line to see if that makes any difference.

---

### Post by llamabr on 2009-04-12
It sucks to reinstall fresh for a little thing like this.

When installing flash, there are a number of ways to get it in, but only do one.  Once you get it coming from different directions, you'll mess each one up.

---

### Post by jasonwatkins on 2009-04-12
> **llamabr said:**
> Once you get it coming from different directions, you'll mess each one up.

that's why i've tried a complete purge on some occasions, just in case there have been any clashes or conflicts - no such luck.

---

### Post by aktiwers on 2009-04-12
Maybe you have the free flash player installed, Gnash that is?
```
sudo apt-get remove gnash
```

---

### Post by bumanie on 2009-04-12
I found following [this]("http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html") was the only way to get flash going on my 64bit ubuntu. The flash is still alpha, but at present seems stable, but that may not be the case as development continues.

---

### Post by aktiwers on 2009-04-12
I am running flash on 64bit and it very stable imo :)

---

### Post by gandaran on 2009-04-12
> **jasonwatkins said:**
> Ok, i've returned to linux after a long while so i'm still kind of finding my linux feet again somewhat.

i'm trying to get flash working in firefox and not really getting anywhere and i'm starting to get a bit stumped.

i should also point out that i'm actually using the KDE release of linux mint V6, which has the guts of Intrepid Ibex (8.10) as far as i'm aware so i'm hoping the general principle will be the same - anyway, you guys on the forum are better than them ;)

What i've tried so far ..

In Synaptic : uninstalling flashplugin-nonfree and installing adobe-flashplugin
                   uninstalling adobe-flashplugin and re-installing flashplugin-nonfree
                   installing both
                   installing neither (obviously that won't isn't going to work but it was worth a try ! :D)

searching these here forums for "flash problems" and trying ..

```
apt-remove --purge -y flashplugin-nonfree nspluginwrapper
apt-install flashplugin-nonfree
```

also downloading the .deb package directly from adobe, which is 'install_flash_player_10_linux.deb' and installing that.  it tells me there is a newer version in the software channel, but i still try this one anyway.

i've also tried ..

```
aptitude purge flashplugin-nonfree flashplugin-nonfree-extrasound adobe-flashplugin nspluginwrapper
```

and then

```
aptitude install flashplugin-nonfree
```

i've also tried downloading the tar.gz version of the latest flashplugin and copying the libflashplayer.so file to /usr/lib/mozilla/plugins and also to /usr/lib/firefox-3.0.8/plugins.

i've also tried downloading and installing version 9 of the flash plugin.

and .. NOTHING works .. when I go to youtube, or try and play a game, i just get an empty square where the flash content should be.   is it a case of me not seeing the wood for the trees ?

any help greatly appreciated .. thanks ..

doesn't flash work out of the box in linux mint?
linux mint comes with all codecs preinstalled!
maybe you have messed up something, post the full output by typing this code in firefox url bar
```
about:plugins
```
and the output of **locate libflash** type in terminal.

---

### Post by jasonwatkins on 2009-04-12
> **aktiwers said:**
> Maybe you have the free flash player installed, Gnash that is?
```
sudo apt-get remove gnash
```

No, that's not installed.  I do only have the 32-bit incarnation for the record.

ok, i've done the 'about: plugins' command - i've tried to select the most relevant as it's pretty huge.

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

```
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes

```

```
QuickTime Plug-in 7.4.5

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes

```

```
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
```

```
mplayerplug-in 3.55

    File name: mplayerplug-in.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes

```

> **gandaran said:**
> doesn't flash work out of the box in linux mint?

this is what i thought :)

the output of the 'locate libflash' command is as follows ..

```
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
```

---

### Post by gandaran on 2009-04-12
> /usr/lib/adobe-flashplugin/libflashplayer.so

is adobe-flashplugin the only flash package installed? nothing else in /usr/lib/mozilla/plugins? make sure you don't have any libflashplayer.so file installed somewhere just the adobe-flashplugin, now you have to install all updates for this package to work, install updates first and reinstall the adobe-flashplugin, should work.
question, do you have flashblock addon installed?

---

### Post by jasonwatkins on 2009-04-12
> **gandaran said:**
> is adobe-flashplugin the only flash package installed?

it is, yeah

> **gandaran said:**
> nothing else in /usr/lib/mozilla/plugins?

there was one copy of libflashplayer.so left over there,but it's now gone. i've made sure all other copies apart from adobe-flashplugin are gone as well.

> **gandaran said:**
> now you have to install all updates for this package to work

what updates would those be ? Is it worth doing another purge of everything and maybe re-installing the restricted extras ?

> **gandaran said:**
> do you have flashblock addon installed?

No

---

### Post by jasonwatkins on 2009-04-12
the annoying thing about this in a way is that i only really went with linux mint because that's the distro i had on my PC a few years back when I last used linux as my sole OS.

i half wish i'd gone with kubuntu in a way .. i might actually download it and if i can't get this flash problem sorted by tonight, i'll just try kubuntu instead.

i'll just have to re-partition the hard drive again .. re-load my music .. yada yada yada :)

---

### Post by jasonwatkins on 2009-04-13
funny thing is, i got to a point last night where i decided i'd give up on mint and just re-do the whole thing again with kubuntu.

had to re-partition the hard drive overnight, re-installed everything, set everything up e.t.c.....

went to youtube and the video plays fine .. with no sound :)

i'm currently trawling the forums looking for a solution ..

---

### Post by jasonwatkins on 2009-04-13
cracked it .. found a command to reset ALSA, ran it and i now have full sound on youtube.

thanks for everyone's help :D

---

### Post by jasonwatkins on 2009-04-13
ok, wondering if anyone could possibly help ?

for reasons i haven't yet worked out, i am now completely back to square one with no flash and just a grey, blank square whenever i go to youtube

i've tried a complete purge of everything flash-related and installed the official adobe plugin, reset alsa and nothing

i've installed the flash-plugin nonfree, reset alsa and nothing

it's getting a bit ridiculous now

---

### Post by jasonwatkins on 2009-04-13
the only thing i seem to have done is to install and run compiz, so i've used adept to uninstall everything i've recently done, but i now appear to have lost the top bar of the window .. (whatever the technical term is .. the bar with the 'X' on it to close the window) :)

---

### Post by jasonwatkins on 2009-04-13
ok, here we are again.

i uninstalled everything compiz related, and ran the command ..

```
aptitude purge flashplugin-nonfree flashplugin-nonfree-extrasound adobe-flashplugin nspluginwrapper
```

which appeared to purge the rest of the compiz related stuff as well as getting rid of the flash plugins.

i rebooted, then did CTRL+Backspace to reboot the X-Server and selected the KDE environment from the startup menu and i'm assuming that the fact that i couldn't do CTRL+ALT to rotate the desktop meant that compiz had been removed.

**_with ubuntu-restrictedextras_**

installed adobe plugin, copied libflashplayer.so to $HOME/.mozilla/plugins - nothing
installed flashplugin-nonfree - nothing
installed adobe plugin, restarted alsa - nothing
installed flashplugin-nonfree, restarted also - nothing
installed curl - nothing

**_with [u]k_ubuntu-restrictedextras[/u]**

as above .. all nothing

did 'about : plugins' in firefox

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

gnash isn't installed either

think that's covered everything up until this point.

it's 12:48am in the UK, so i'm going to bed as the prospect of having to re-format again and spend another 7 hours re-partitioning my hard drive .. again .. for the second time in 3 days .. is rather disheartening.

at least if i have to reformat, i'd be eternally grateful if someone could give me an idea for when i wake up in a few hours - at least i can kick off the re-partitioning and go out somewhere ... thanks :)

---

### Post by jasonwatkins on 2009-04-13
or if anyone could suggest another distro that has some kind of flash pre-loaded, i might have to consider that one .. thanks

---

### Post by jasonwatkins on 2009-04-14
well .. thanks for the input and all that .. guess i'm reformatting .. again

---

### Post by gandaran on 2009-04-14
are you running a 64-bits OS system? if correct then your problem is solved, install 64-bits flash!
follow this [guide]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml")

---

### Post by Jakey_TheSnake on 2009-04-14
Ubuntu should practically out of the box, just download and double-click [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by jasonwatkins on 2009-04-14
> **gandaran said:**
> are you running a 64-bits OS system?

No, i only have a regular setup on my PC so i was only running the 32 bit version.

anyway, i do appear to have actually discovered the *real* root of the problem.

what i was doing on my windows partition was backing up my firefox profile, with all the settings, plugins, bookmarks e.t.c. and just copying the directory, in full, right over the top of the profile directory in linux.

so what i think was happening was that i was overwriting all the linux-relevant information regarding plugins e.t.c. and causing a conflict.

when i reformatted, i backed up my firefox profile and only selected bookmarks, passwords and cookies and copied that *into* the linux profile directory.  since i only had bookmarks, passwords and cookies, it was ok to overwrite the relevant linux files as all of the information regarding plugins e.t.c. was unaffected.

tried it on a mandriva installation and it worked, so i reformatted again and re-installed linux mint V6 KDE and did the same thing and it all works fine now, and has survived multiple reboots :)

lesson learnt I think :D

---

### Post by jasonwatkins on 2009-04-14
ah well .. it was all going so well ..

i have now lost flash .. again ...

i have done nothing to the firefox profile - the only thing i can think of that might have done something is an "apt-get autoremove" that i ran.

other than that i'm really reaching the end of my tether here because this is beyond a joke now - it's farcical.  i'm not *that* incompetent ...

---

### Post by jasonwatkins on 2009-04-14
you know what, i don't want to spend another 3 days trying to get this working so i'm going to reboot back to the windows partition for an hour's worth of PES 2009 before i go to bed and it's more than likely i'll just forget linux alltogether tomorrow .. i'll just continue to fry my brain on windows

---

### Post by jasonwatkins on 2009-04-15
well, thanks for the input but i tried completely removing firefox in synaptic, rebooting and re-installing and still didn't get flash back so screw it, i'm going to reformat and go back to windows.

---

### Post by jasonwatkins on 2009-04-15
well i guess the adage of "just one more go" proved fruitful here because i re-removed firefox in synaptic, including the restricted extras.

i also removed the .mozilla directory as well and rebooted.

went to adept and re-installed firefox with adblock plus and the flash plugin and it worked.

i think the moral of the story must be that the firefox profile in windows will not port over in any sense whatsoever.

i want to try doing the passwords seperately because i don't want to manually re-login to about 30 odd websites, but at least i know how to fix it now .. finally, so again, thanks for the input ..

---

### Post by gandaran on 2009-04-15
> i think the moral of the story must be that the firefox profile in windows will not port over in any sense whatsoever.
I back up the whole .mozilla folder in windows and never had any problem.> went to adept and re-installed firefox with adblock plus and the flash plugin and it worked.
check adblock addon, maybe this is the problem. 
you don't need to reinstall firefox, just delete the home .mozilla folder and restart firefox, see if it works

---

### Post by jasonwatkins on 2009-04-15
> **gandaran said:**
> I back up the whole .mozilla folder in windows and never had any problem.
check adblock addon, maybe this is the problem. 
you don't need to reinstall firefox, just delete the home .mozilla folder and restart firefox, see if it works

well i might try that now because my big plan above has proven to be a false start - i've been out all day and i've just booted my machine up to catch up and once again, i no longer have flash working.

and this is straight from a clean install

it *has* to be something to do with the addons - there's no other logical explanation.

---

### Post by markofealing on 2009-04-17
Very interesting, I've got the same problem with Ubuntu 8.10.

Like you I took my Mozilla Firefox profile from Windows, but from what I've established so far this isn't the cause of the problem. To test , with firefox closed, I renamed the .mozilla folder in my Home folder to .mozilla.old. I then ran Firefox and this gave me a clean .mozilla folder. Same problem, when you go to youtube or use the BBC iplayer Firefox just locks up.

Like you I've removed Flash and have re-installed the Ubuntu non-free version of Flash. No joy!

So I decided to try an alternative browser, as I'm running Ubuntu I installed Epithany and had exactly the same experience as Firefox. In your case you could install Konqueor.



I run Ubuntu and Kubuntu on a variety of PCs and have never had this problem before.

What is your hardware configuration? Mine is:

AMD Athlon XP 2800+
PC Chips M848A motherboard
2Gb RAM
ATI Radeon 9600
SoundBlaster Live! 5.1

I suggest you install Ubuntu/ Kubuntu and get Flash working, **but do not apply any updates**. Use the PC as normal for a few days and see if Flash continues to work, if it does then it would appear that an update is breaking Flash in your particular configuration.

Try playing an .FLV file from your file manager and see if it playes. In my case this worked okay and played in Totem. This proves Flash works, although outside a browser!

In the meantime I'm going to do some more digging as I don't fancy re-installing Ubuntu on my PC!

---

### Post by markofealing on 2009-04-18
Okay, I've done some more digging and have established the following:

1. Flash enabled websites do work, I just need to click the play button in the middle of the big grey window!
2. Sites using SWF flash files playback okay.

After reading this post [http://www.tweak3d.net/forums/ftech/youtube-video-problems-firefox-freezes-2-seconds-32861-3](http://www.tweak3d.net/forums/ftech/youtube-video-problems-firefox-freezes-2-seconds-32861-3) which is related to Windows and Firefox but in this case (same difference) it looks like there is a problem with Flash 9. In my case I have in Firefox Plugins Shockwave Flash 9.0 r999. On two of my PCs where streaming Flash Video works fine i.e. BBC iPlayer and youtube, it is Shockwave Flash 10.0 r22.

The next step is to work out how to change this to Flash 10.0 r22.

---

### Post by markofealing on 2009-04-18
I upgraded the Flash plugin to 10.0.22.87 [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) but it was still showing Flash 9 in Firefox!

Found the following on the Mozilla Knowledgebase website kb.mozillazine.org/Flash_(Firefox)#Linux_and_Solaris . Really excellent link for trouble shooting Flash problems in Firefox. [COLOR="Red"]Turns out that there is a bug in version 9 of Flash which can cause playback issues with youtube and similar sites.[/COLOR]

Removed flashplugin-nonfree from firefox with:

sudo apt-get remove flashplugin-nonfree 

Flash was still present in Firefox so did the following (as instructed in the link):

*If the uninstall don't work: 1. type about:config in the address bar and press Enter. Find the option plugin.expose_full_path and change the value to "true" (double-clicking the preference name will toggle the setting). 2. type about:plugins and locate the flash plugin. *

    File name: /usr/lib/swfdec-mozilla/libswfdecmozilla.so
    Shockwave Flash 9.0 r999

*Removed the plugin files (both .so and .xpt).* 

I could only find the .so file so just delted this file. 

Noticed in /etc/alternatives two broken links to the above for mozilla-flashplugin and midbrowser-flashplugin and in /usr/lib/firefox/plugins another broken link for flashplugin-alternative, pointing to  /etc/alternatives. As these were just links linking back to the deleted .so file I decided to leave, at least for now!

Restarted Firefox, checked that the flash plugin was still removds and then re-installed the Adobe plugin (back to the Adobe website) using the Ubuntu 8.04+ deb package via the package manager. 

Restarted Firefox. Chceked plugins again and now got:

    Shockwave Flash 10.0 r22.

Entering in the address bar about plugins showed the following for Shockwave Flash (I decided to leave the full path information exposed) 

    File name: /usr/lib/adobe-flashplugin/libflashplayer.so
    Shockwave Flash 10.0 r22

All was now looking good so, went to the BBC iplayer website and played a program. It worked, previously Firefox whould hang.

[COLOR="Red"]**Flash is fixed in Firefox!!**:D[/COLOR]

Whilst I was on the BBC website, I took the opportunity to install the BBC iPlayer for Linux (uses Adobe Air), this works really well!

Hopefully the above will help you fix your Flash/ Firefox problem.

---

### Post by jasonwatkins on 2009-04-18
mark, thanks for all your hard work and investigation :)

i do actually have the current version of flash installed - if i do 'about: config' i get "Shockwave Flash 10.0 r22" as well.

i have, however, stumbled upon the root cause of the problem - foxytunes and XMMS.  i literally found this not half an hour ago :)

if i use foxytunes to select XMMS as my player, i lose flash.

amarok works fine, although 'yuk' does crash for whatever reason.  i've even installed the latest version of foxytunes which is 3.5.4.1 and it still does the same thing.

i've done it multiple times and the result is still the same - start firefox and select the configuration option in foxytunes, select the 'player' submenu and choose XMMS and flash goes.

i've even sat on a bbc webpage with a large iplayer window in front of me, selected XMMS as the player on foxytunes, refreshed the page and the iplayer window vanishes.  the daft thing is, is that once selected, XMMS works fine - i have full control over it in firefox and the song title displays in the status bar as it should.

i just lose flash :)

i'm currently looking around to see if there's anyone else who has the same issue and if so, i can report it to the developers as a bug.

---

### Post by markofealing on 2009-04-18
You're welcome.

Having been a Windows "Power User" for many years and recently moving my main PC to Ubuntu, the effort in the long run is worth the short term pain of getting things working.

Best of luck, but most of all don't give up on Linux. ;-)

---

### Post by jackhe22 on 2009-04-18
I had the exact same problem, ive made a YouTube video on how to fix it, but I will tell you here quickly:

Install the .deb package from the website like normal, (or reinstall)
Open your disc drive and browse to:
/usr/lib/mozilla/plugins

The file in there which is flash, click copy.

Now, open your home folder and press Ctrl+H to show hidden folders, from there open the folder .mozilla If there is no plugins folder make one. Paste the file in there, and it works!

---

### Post by jasonwatkins on 2009-04-18
> **jackhe22 said:**
> I had the exact same problem, ive made a YouTube video on how to fix it, but I will tell you here quickly

could you link to the video please ?

i'm curious :)

---

