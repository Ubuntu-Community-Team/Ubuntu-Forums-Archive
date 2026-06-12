---
title: "Safely Remove Pulseaudio?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Sammaye on 2009-11-03
Hi everyone,

I recently upgraded to 9.10 (karmic) and instantly realized I no longer used alsa but instead pulse. This would normally be fine only my games (i.e. fallout 3 and empire total war) only run on alsa.

I have tried removing pulseaudio but this causes problems for ubuntu sound and actually breaks it. I have also tried searching for a way to actually choose my sound system but it seems ubuntu itself only really support pulseaudio (no library chooser to switch to alsa, unless I'm looking in the wrong place).

I can remove and replace pulseaudio with alsa but it destroys ubuntu's gui for sound (i.e. system->pref->sound breaks) and I have to change volume via terminal which is a pain especially in a game that won't alt-tab without crashing.

I was wandering if there was either:

a. A safe way to replace pulseaudio with alsa
b. Or use terminal to switch off pulseaudio for a given amount of time so alsa can be run on my games.

I did have a way to switch off pulseaudio but when ever I use the command now I just get:

E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

Which is a pain again.

Thanks.

---

### Post by squaregoldfish on 2009-11-03
You can disable pulse using the instructions at this address:
[URL="http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/"]
http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/[/URL]

Note that asoundconf is no longer present in Karmic, but it can be installed from the Jaunty repositories - see comments from the last couple of days on the same page.

Steve.

---

### Post by Hugo Alvarado on 2009-11-04
Here is what I did to remove pulse audio in Karmic:

sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove

sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui

sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer

restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)
-remove gstreamer0.10-pulseaudio to get sound in totem
-gnome-alsamixer is for changing the volume, not an applet but better that nothing

Enjoy!

---

### Post by nullrend on 2009-11-10
The above procedure works. I'll just repeat it for extra points, marked up properly.

Here is what I did to remove pulse audio in Karmic:

```
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
$ sudo apt-get autoremove
``````
$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
``````
$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
```restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)[INDENT]This means:
```
$ gstreamer-properties
```[/INDENT]-remove gstreamer0.10-pulseaudio to get sound in totem.[INDENT]The above commands should have taken care of that, but it never hurts to be sure when talking about the hydra that is PulseAudio.
[/INDENT]-gnome-alsamixer is for changing the volume, not an applet but better that nothing[INDENT]This means you are left without a panel applet to control volume across the board, thanks to the thoughtful efforts of Canonical to shove PulseAudio down our throats. So you need to have something to control audio with:
```
$ sudo apt-get install gnome-alsamixer
```And something to keep gnome-alsamixer within easy reach, provided by AllTray:
```
$ sudo apt-get install alltray
```[/INDENT]Now, one last word of advice. Usually the best solution is to use aptitude or synaptic to do these moves, but you'll run headfirst into their dependency resolution efforts, which command them to put PulseAudio back in your system when reinstalling gnome-alsamixer. So either you use apt-get or you reconfigure aptitude/synaptic dependency resolution to work the way you want.

---

### Post by taffyviking on 2009-11-10
Thanks Nullrend for your excellent stepwise guide to purging my laptop of PulseAudio.

Since upgrading my ancient "web radio" laptop from 9.04 to 9.10 (and then doing a clean install just to make sure) I've had nothing but hassle with the sound system including choppy sound, sound being muted or set at minimum after startup, sound stopping/muting/setting to minimum while in use and awful hammering noises while adjusting the volume using the tray app. And this just using the BBC i-player; With Rhythm box it was even worse!

How has something as bad as PulseAudio been allowed out for general use?  I'll certainly think twice about upgrading automatically to Loony Leopard (or whatever daft name they're going to call it) without waiting a couple of months and checking the forums carefully.

---

### Post by slumbergod on 2009-11-10
Yeah, I totally agree - PulseAudio was never anything but a headache for me. It crackled and popped all the time. The first thing I did was replace it after any new installation.

Imagine my delight to find Xubuntu 9.10 didn't have Pulse!!!!

---

### Post by Zoot7 on 2009-11-10
After removing Pulseaudio, I tried recompiling the gnome applets specifying to disable pulseaudio support; while I was able to get a volume applet up on the bar, my media keys didn't work.

Recompiling them with the default configure options as I type now.

---

### Post by nullrend on 2009-11-10
> **Zoot7 said:**
> After removing Pulseaudio, I tried recompiling the gnome applets specifying to disable pulseaudio support; while I was able to get a volume applet up on the bar, my media keys didn't work.

Recompiling them with the default configure options as I type now.

Let us know how that works. I just realized the volume up/down/mute keys on my keyboard no longer work after purging my system of PulseAudio. Wonder if there's a way to build a package people can install...

---

### Post by nullrend on 2009-11-10
Hmm, now you've got me wondering how Xubuntu 9.10 handles the sound subsystem. Maybe a couple of packages can be installed on Ubuntu systems to get a sound applet for the GNOME panel?

Now to be clear, I don't think PulseAudio is such a bad thing. When it works it is a thing of beauty. My problem is with Canonical's implementation of it.

---

### Post by Zoot7 on 2009-11-11
> **nullrend said:**
> Let us know how that works. I just realized the volume up/down/mute keys on my keyboard no longer work after purging my system of PulseAudio. Wonder if there's a way to build a package people can install...
I was actually able to get a volume applet on the panel, however then both my volume control keys and the rest of the media keys (play/pause etc.) no longer worked which is a bit of a deal breaker for me, so I recomplied the applets with the default options again, and installed pulse once more.
Sadly pulse is too integrated to simply remove like you could up until Karmic. :(

I'll give it another crack on that testing hard drive of mine later today.

---

### Post by Zoot7 on 2009-11-11
Hmm.. I wonder would it be possible to grab the gnome-media source from the Jaunty repos and recompile that? 
The different version of gnome might cause problems though... must give it a shot at some point.

---

### Post by robert-e on 2009-11-11
Has anyone had any success with removing PulseAudio and then installing OSSv4?  I needed to install OSSv4 since PA does not support devices dsp, needed for some programs I use (in Fedora 10).  I ask as I have a spare hard drive and would like to play with Ubuntu 9.10.
Thanks for reading.
Bob

---

### Post by jf1991999 on 2009-11-11
My primary reason for removing Pulse was that it screwed the new version of Skype.

I found that the following worked.

sudo apt-get remove pulseaudio

sudo apt-get install esound

I installed ALSA and the GNOME ALSA GUI via Synaptic.  The ALSA GUI is a rough way to control sound but at least everything now works.

---

### Post by Zoot7 on 2009-11-12
I see Debian Unstable uses Gnome 2.28 aswell. I'm wondering if I fetched the source for Gnome Media, Gnome Applets and Gnome Settings Daemon from the Unstable repositories and compiled it under Karmic.
It's worth a shot and I'll let you all know how I get on.

---

### Post by q.dinar on 2009-11-13
i have made this in ubuntu 9.04 , now flash in firefox does not work.
see about this what i do also in [http://ubuntuforums.org/showthread.php?p=8308523](http://ubuntuforums.org/showthread.php?p=8308523) .

---

### Post by Zoot7 on 2009-11-13
> **q.dinar said:**
> i have made this in ubuntu 9.04 , now flash in firefox does not work.
see about this what i do also in [http://ubuntuforums.org/showthread.php?p=8308523](http://ubuntuforums.org/showthread.php?p=8308523) .
Flash needs a plugin to work with Pulseaudio.

I went and built the flash plugin from source to get it up and running.
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install
```

or instead of make install
```
sudo checkinstall
```
to build and install a .deb package.

I now can play flash along with pretty much all other audio applications.

Why this wasn't already in the repositories baffles me... :/

---

### Post by coldReactive on 2009-11-13
> **Zoot7 said:**
> Flash needs a plugin to work with Pulseaudio.

I went and built the flash plugin from source to get it up and running.
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install
```

or instead of make install
```
sudo checkinstall
```
to build and install a .deb package.

I now can play flash along with pretty much all other audio applications.

Why this wasn't already in the repositories baffles me... :/

Because pulseaudio works for flash nicely on my end.

esound can't be ran in karmic due to the sheer volume of integration that pulseaudio emits.

---

### Post by Zoot7 on 2009-11-13
> **coldReactive said:**
> Because pulseaudio works for flash nicely on my end.
Out of interest were you able to get sound from flash along with other applications using Pulse at the same time without ever going near plugins for it?

---

### Post by coldReactive on 2009-11-13
> **Zoot7 said:**
> Out of interest were you able to get sound from flash along with other applications using Pulse at the same time without ever going near plugins for it?

I use flashplugin-nonfree (i386) on my amd64 arch ubuntu.

I can hear flash sounds while running totem music on the default install of pulseaudio.

---

### Post by Zoot7 on 2009-11-13
Strange. I've had the exact same problem with flash in each of the 3 machines I've installed Karmic on, and using that flashplugin-nonfree-pulse package sorted it in each case.

---

### Post by Elviswind on 2009-11-13
Thanks for this thread . . . the advice in post #4 to remove Pulseaudio was perfect, but since I'm running Xubuntu 9.10, I did not need to run the last few commands to install another mixer.  I should have known from the start after upgrading that something wasn't right since I suddenly had two mixers in my bar.

Not only did removing Pulseaudio fix my crappy sound that showed up after upgrading to 9.10, but I was also able to remove the workaround in /etc/rc.local and I no longer have problems with the sound starting muted.

\\:D/

---

### Post by q.dinar on 2009-11-14
no, flash has not worked when pa is uninstalled. now i try to install flashplugin-nonfree, if it will not work will try additionally to install flashplugin-nonfree-extrasound . now was installed adobe-flashplugin.

---

### Post by q.dinar on 2009-11-14
installing flashplugin-nonfree and flashplugin-nonfree-extrasound instead of adobe-flashplugin has not helped.

---

### Post by Sammaye on 2009-11-15
This is a recurring problem in Wine with pulseaudio, although just as a weird guess I kinda selected all sound drivers in winecfg and now my sound works good :).

---

### Post by Zoot7 on 2009-11-15
> **q.dinar said:**
> installing flashplugin-nonfree and flashplugin-nonfree-extrasound instead of adobe-flashplugin has not helped.
You might want to give the flashplugin-nonfree-pulse I mentioned earlier in this thread a shot. Installing that is what sorted the flash problems with pulseaudio for me.

---

### Post by coldReactive on 2009-11-15
> **Zoot7 said:**
> You might want to give the flashplugin-nonfree-pulse I mentioned earlier in this thread a shot. Installing that is what sorted the flash problems with pulseaudio for me.

You can't, there is no such package:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-pulse

```

---

### Post by Zoot7 on 2009-11-15
It doesn't exist in the repos. I had to download it and compile it from source.

---

### Post by coldReactive on 2009-11-15
> **Zoot7 said:**
> compile it from source.

Red Flag.

---

### Post by Zoot7 on 2009-11-15
> **coldReactive said:**
> Red Flag.
Red flag indeed. :(
It'd be nice if the Ubuntu devs could pick something that's stable and problem free and run with it.

---

### Post by coldReactive on 2009-11-15
> **Zoot7 said:**
> Red flag indeed. :(
It'd be nice if the Ubuntu devs could pick something that's stable and problem free and run with it.

It's too bad that ALL THREE flash players aren't stable.

---

### Post by Zoot7 on 2009-11-15
> **coldReactive said:**
> It's too bad that ALL THREE flash players aren't stable.
I gather the flash player package in the repos is broken (at least that was the word in the pipeline). 
I've installed the .deb off adobe's website, and coupled with the flash extension for pulseaudio, flash is fine on my machines.

---

### Post by coldReactive on 2009-11-15
> **Zoot7 said:**
> I gather the flash player package in the repos is broken (at least that was the word in the pipeline). 
I've installed the .deb off adobe's website, and coupled with the flash extension for pulseaudio, flash is fine on my machines.

But I'd rather not compile, so I'm stuck with instability :(

---

### Post by sandyd on 2009-11-15
> **taffyviking said:**
> Thanks Nullrend for your excellent stepwise guide to purging my laptop of PulseAudio.

Since upgrading my ancient "web radio" laptop from 9.04 to 9.10 (and then doing a clean install just to make sure) I've had nothing but hassle with the sound system including choppy sound, sound being muted or set at minimum after startup, sound stopping/muting/setting to minimum while in use and awful hammering noises while adjusting the volume using the tray app. And this just using the BBC i-player; With Rhythm box it was even worse!

How has something as bad as PulseAudio been allowed out for general use?  I'll certainly think twice about upgrading automatically to **Loony Leopard** (or whatever daft name they're going to call it) without waiting a couple of months and checking the forums carefully.
its called **Lucid Lynx **and where did i find that?
its right above this thread. ;)

---

### Post by Zoot7 on 2009-11-15
> **coldReactive said:**
> But I'd rather not compile, so I'm stuck with instability :(
Compiling isn't too bad really. I know it's not something a reasonable end user should have to do, and it's a classic example of why Linux isn't really ready for the desktop.

A great package is checkinstall, which will build the compiled code into a .deb package so it's simple remove if need be.

---

### Post by coldReactive on 2009-11-15
> **Zoot7 said:**
> Compiling isn't too bad really. I know it's not something a reasonable end user should have to do, and it's a classic example of why Linux isn't really ready for the desktop.

A great package is checkinstall, which will build the compiled code into a .deb package so it's simple remove if need be.

giftwrap will do the same.

---

### Post by Natovr on 2009-11-16
This helped me :D But what I did for volume control is to go to System > Preferences > Keyboard shortcuts, and then made a Volume Up shortcut (add button), with the command line "amixer -q set PCM 3+" (you can also use Master instead of PCM.. I used PCM because it went all the way down to mute, unlike Master). Then make another shortcut, Volume Down, with the command "amixer -q set PCM 3-"... again, you can change to Master if you want.

edit: You can use any keys you like, but I used XF86AudioRaiseVolume and XF86AudioLowerVolume which is basically "Fn+Left" and "Fn+Right" on my laptop.

It doesn't show the volume in the gnome panel, but you can still see it by running "amixer". It should change under PCM (or Master, whichever).
edit: There is probably a non-GUI way to do this.

---

### Post by gmt2027 on 2009-11-17
I was also having trouble with pulseaudio after upgrading to Karmic. Erratic output, an endless stream of "suppressed events" in the system log and strange sounds from the speakers - but the final irritation was simultaneous output over both internal speakers and headphones after a random reboot that I couldn't fix. 

I've removed pulseaudio and am using kmix as the panel applet now. It's KDE and it works. I'm beginning to reconsider going back to kubuntu.

---

### Post by q.dinar on 2009-11-17
> You might want to give the flashplugin-nonfree-pulse I mentioned earlier in this thread a shot. Installing that is what sorted the flash problems with pulseaudio for me.i have not problem with flash and pulse! it worked fine! ices2 used much processor with pulse, for that i uninstalled pulse and now when without pulse flash does not work.
please help me to configure pulse so that it does not touch one of 2 soundcards. if i can do so then i will use pulse because with pulse {flash in firefox}'s sound works.
this is in 9.04! they say in 9.10 it is easy to switch off one of soundcards from being loaded by pulse.

---

### Post by Sammaye on 2009-11-18
It isn't easy on 9.10 it is in fact almost impossible since the only real "supported" audio is pulseaudio now.

9.04, for me, used alsa...

---

### Post by Zoot7 on 2009-11-18
A bit of fiddling I did, and I now notice I can add an applet to the panel regardless of whether pulseaudio is there or not.

I'm still missing the gnome-volume-control though, which is part of the  
What I did was recompile the gnome-applets package from the repos, and add in the applet.

I really don't recommend anyone try this, you'd be better off to just stick with pulse, but if you ***really*** want that applet back after removing pulseaudio, this is one such way.

If anyone's interested here's what I did:
```
sudo apt-get install devscripts build-essential fakeroot
sudo apt-get build-dep gnome-applets
```
That'll pull in all the dependencies to build everything.

```
cd ~
mkdir build && cd build
apt-get source gnome-applets
cd gnome-applets-2.28.0
```

Then you're going to have to specify the configure options to enable the mixer applet. To do that
```
gedit debian/rules
```
Look for the line that starts with **DEB_CONFIGURE_EXTRA_FLAGS +=**
and add in **--enable-mixer-applet** on the same line, save and close.

Then run this to build the packages.
```
dpkg-buildpackage -b -j4 -D
```
once that's finished:
```
cd ..
```
To see the end result; there should now be 3 .debs in that directory, namely:
[LIST=1]
[*]gnome-applets_2.28.0-0ubuntu2_i386.deb
[*]gnome-applets-data_2.28.0-0ubuntu2_all.deb
[*]gnome-applets-dbg_2.28.0-0ubuntu2_i386.deb
[/LIST]

Lastly install them with:
```
sudo dpkg -i *.deb
```

Restart gdm (log off and log on again, reboot or run **sudo service gdm restart**), and right click on the panel and you should now be able to add a volume control applet regarless of whether pulseaudio is installed or not.

Apt is now going to want to update those 3 packages to their original version, so to hold and tell it to leave them as is do:
```
sudo -s
echo 'gnome-applets hold' | dpkg --set-selections
echo 'gnome-applets-data hold' | dpkg --set-selections
echo 'gnome-applets-dbg hold' | dpkg --set-selections
```

Now you should be able to carry on as normal.

---

### Post by Zoot7 on 2009-11-18
> **q.dinar said:**
> this is in 9.04! they say in 9.10 it is easy to switch off one of soundcards from being loaded by pulse.
If you're using 9.04 you can remove pulse, but if you want to control it do:
```
sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
```
That'll pull in all the necessary PulseAudio libraries and configuration utilities.

Then you should be able to choose the devices pulse uses in the "Pulseaudio Device Chooser" in the Sound & Video menu.
This works in Karmic, I'm not sure how you'll fair in Jaunty. I used to just remove Pulseaudio straight away.

---

### Post by JC Cheloven on 2009-11-19
Hi, I come a bit late to the party !!

First, thanks to #3 & 4.  It worked in UbuntuStudio 9.10 Karmic in a spare machine.  For me, this implies that:

- I'll be able to setup a friend's pc with UbuntuStudio. The problem was that Pulseaudio broke the sound in musescore, which he (and me for that matter) needs.

- I'll hopefully be able to use ubuntu myself in my main music-production machine, instead of 64studio beta 3. I had to switch because pulse broke compatibility with my (excellent and fully alsa supported) pci soundcard. A hamerfall dsp 9632.

Usually people will have pulse problems similar to the first one of mine. that is, apps problems. I solved these in a less drastic way. If anyone is interested:

Create the file ~/.pulse/client.conf and stuff it with a single line: ```
autospawn = no
``` After a reboot you can run ```
pulseaudio -k
``` anytime you'll do something pulse-problematic, as running musescore is. If you will do something pulse-dependent (ie, ubuntu-pulse-configured), as playing something in totem or streaming a/v in firefox, you can run pulseaudio -D before, to bring again pulse alive.

While this solved mostly the software problems, wasn't so lucky with my hardware problem. Also it is something that I wouldn't ask to do to a non tech musician friend. Facing the multi window Jack is more than enough for him ;-)

Anyway, I'll try the method of this thread and report any successes related to my hardware problem.
Greetings

---

### Post by Wilbefast on 2009-11-21
#3/4 worked really well for me, fixed a lot of problem I'd been having. Trouble of course is that I can't re-adjust the sound with the buttons any-more (as forewarned) and this is somewhat annoying since it's a laptop so I can't just turn down the speakers. 

So yeah, here's hoping somebody clever will fix it :D

---

### Post by Zoot7 on 2009-11-21
> **JC Cheloven said:**
> - I'll be able to setup a friend's pc with UbuntuStudio. The problem was that Pulseaudio broke the sound in musescore, which he (and me for that matter) needs.
One useful command for apps that don't like Pulseaudio like Musescore is **pasuspender**. The best thing to do is change your launchers to include "pasuspender" before the command to launch the app.
That way Pulse is suspended once you start that app and is brought back to life once you quit it.
I use it for Tuxguitar, Wine apps and Musescore at the moment.

---

### Post by Wilbefast on 2009-11-21
> **Zoot7 said:**
> One useful command for apps that don't like Pulseaudio like Musescore is **pasuspender**. The best thing to do is change your launchers to include "pasuspender" before the command to launch the app.
That way Pulse is suspended once you start that app and is brought back to life once you quit it.
I use it for Tuxguitar, Wine apps and Musescore at the moment.

handy... so I guess that means we'll have to reinstall it all again then...

edit: very handy in fact - I couldn't use skype without pulseaudio but now I can use certain apps that like alsa :)

edit 2: I may have spoken too soon... "Spring" (the game) for example, which doesn't play sound properly over pulseaudio, will not play any sound at all if pasuspender is used...

---

### Post by tommcd on 2009-11-22
> **nullrend said:**
> The above procedure works. I'll just repeat it for extra points, marked up properly.
Here is what I did to remove pulse audio in Karmic: .... (post #4 in this thread)

Very good tutorial, it worked for me!
The problem I have with pulse audio is that it is a huge resource hog. On my  socket 939 AMD Athlon64 3200+ CPU pulse was using 10-20+ % of my CPU. Alsa uses minimal CPU by comparison. 
I am guessing that pulse will replace alsa at some point in the future, just as alsa has replaced oss. At present, pulse just uses more system resources without adding any advantages over alsa that I can see or hear. I will stick with alsa until I can demonstrate a clear advantage for using pulse.

---

### Post by Zoot7 on 2009-11-22
> **Wilbefast said:**
> edit: very handy in fact - I couldn't use skype without pulseaudio but now I can use certain apps that like alsa :)
Yeah the new version of skype doesn't work properly without pulseaudio sadly.
And ditto having problems with Games. :(

---

### Post by mgol on 2009-11-23
> **Zoot7 said:**
> Yeah the new version of skype doesn't work properly without pulseaudio sadly.
And ditto having problems with Games. :(
I don't think that's true, why do You say so? Other sound engines are available once You remove PA.

---

### Post by Zoot7 on 2009-11-23
> **mgol said:**
> I don't think that's true, why do You say so? Other sound engines are available once You remove PA.
I could never get the new version of Skype to play nice with my USB mic minus Pulseaudio.
Of course Skype 2.0 worked away as happy as Larry with Alsa only.

---

### Post by Wilbefast on 2009-11-23
> **mgol said:**
> I don't think that's true, why do You say so? Other sound engines are available once You remove PA.

Well, I can hear but can't be heard - there's this weird thing that happens: I try to test the mike on sound-recorder when Skype is running and it doesn't work, then I close Skype and it does: somehow running Skype stops the microphone from working across the board.

Another annoying thing in 9.10 is with sound-recorder actually: constantly asking you if you want to save your file :-S

---

### Post by RoestVrijStaal on 2009-11-25
Today I completely nuked my Ubuntu installation, thanks to libpulse0.
Somehow gnome-panels, gnome-session and other components of gnome depends on this lib of pulseaudio. I really wonder why. I uninstalled libpulse0, by accident with the gnome-components... no login for me anymore.

I'm thinking about to switch to the pulseaudio-free Xubuntu:popcorn:

---

### Post by seeker5528 on 2009-11-25
> **RoestVrijStaal said:**
> Today I completely nuked my Ubuntu installation, thanks to libpulse0.
Somehow gnome-panels, gnome-session and other components of gnome depends on this lib of pulseaudio. I really wonder why. I uninstalled libpulse0, by accident with the gnome-components... no login for me anymore.

I'm thinking about to switch to the pulseaudio-free Xubuntu:popcorn:

Well, as it looks like you found out, libpulse0 is not something you want to get rid of if you are using Gnome stuff, and I think some non-Gnome stuff will pull this in as well.

If you don't want pulseaudio mucking things up, turning off the option to treat recommends as dependencies and removing pulseaudio and pulseaudio-* packages is enough. 

If you are currently stuck at the command line:

[http://blogs.koolwal.net/2009/01/07/howto-tell-apt-get-not-to-install-recommends-packages-in-debian-linux/](http://blogs.koolwal.net/2009/01/07/howto-tell-apt-get-not-to-install-recommends-packages-in-debian-linux/)

Normally when I am updating if I run into updates that want to pull in pulseaudio, I install everything but those things, then in Synpatic turn off the option to treat recommends as dependencies, install the things that want to pull in pulse audio, then turn the option to treat recommends as dependencies back on until the next time. 

Later, Seeker

---

### Post by Zoot7 on 2009-11-26
AFAIK Debian is avoiding Pulseaudio until the issues are avoided. So one option would be to grab the source for Gnome-Applets and Gnome-Media from the Debian Unstable repos (which too uses Gnome 2.28.1) and re-compile it under Ubuntu.
```
apt-get source gnome-applets && sudo apt-get build-dep gnome-applets
```
and then
```
dpkg-buildpackage -b -j4 -D
```
to compile and build the package.

---

### Post by Wilbefast on 2009-11-26
What about Kubuntu? Does KDE use pulseaudio? I'm not very familiar with Xfce but I'm think to changing to *something* else - 9.10 has been giving me all sorts of problems, especially with Flash.

edit: removing Pulseaudio won't fix the problem with Skype because the problem with Skype IS the removal of Pulseaudio - perhaps an older version of Skype?

---

### Post by Zoot7 on 2009-11-26
Kubuntu or Xubuntu don't use Pulseaudio, I think they're just using no-frills ALSA.

Skype 2.0 uses Alsa and works perfectly without Pulseaudio installed, the trouble if finding the installation package. They've taken it off their website to my knowledge.

---

### Post by yakshbuntu on 2009-11-26
> **slumbergod said:**
> Yeah, I totally agree - PulseAudio was never anything but a headache for me. It crackled and popped all the time. The first thing I did was replace it after any new installation.

Imagine my delight to find Xubuntu 9.10 didn't have Pulse!!!!
Thanks

---

### Post by robert-e on 2009-11-27
Thanks to all that posted suggestions wrt removing PA in 9.10.  I will try this, and then if successful, will install OSSv4.  I have used OSSv4 in place of PulseAudio/Alsa in Fedora and it worked quite well.  However, Fedora is moving towards making it exceedingly difficult to do such tweaks, and I am exploring other distros.  I shall also look into Mint 8, to see if it is also is less arbitrary in allowing the user to easily manage the OS.
Regards,
Bob

---

### Post by mgol on 2009-11-27
> **Wilbefast said:**
> 
edit: removing Pulseaudio won't fix the problem with Skype because the problem with Skype IS the removal of Pulseaudio - perhaps an older version of Skype?
I don't get it - I use Skype 2.1 without PA and it works. What is the problem?

---

### Post by Wilbefast on 2009-11-27
The problem is:

> **Wilbefast said:**
> I can hear but can't be heard - there's this weird thing that happens: I try to test the mike on sound-recorder when Skype is running and it doesn't work, then I close Skype and it does: somehow running Skype stops the microphone from working across the board.

---

### Post by mgol on 2009-11-27
@Wilbefast - I run a test call (to echo123) and I heard myself.

---

### Post by JC Cheloven on 2009-11-27
> **Zoot7 said:**
> One useful command for apps that don't like Pulseaudio like Musescore is **pasuspender**. The best thing to do is change your launchers to include "pasuspender" before the command to launch the app.
That way Pulse is suspended once you start that app and is brought back to life once you quit it.
I use it for Tuxguitar, Wine apps and Musescore at the moment.

As a matter of fact, I made the menu icons to execute simple scripts, with commands similar to these (example for musescore):
[INDENT]pulseaudio -k
mscore
pulseaudio -D [/INDENT]
It worked nicely as well. Thanks anyway ;-)

Related to my post #42, I can confirm that the removal of pulseaudio following the instructions in this thread, has been succesful: my Hammerfall DSP 9632 which wasn't recognized due to pulse-alsa issues (didn't even appeared in aplay -l), works flawlessly now.

**_For those of you who use skype._** Perhaps the community, as a bunch of new members come in, is forgeting (in average) the risks of proprietary software, and thus the ideas underpinning this whole thing called "free software". I don't use e-phones anyway, but I'd consider free-libre replacements. Be adviced about some possible issues with skype (some in spanish or frech, sorry):

- [Skype accused]("http://www.abc.es/20081003/internacional-internacional/empresa-telecomunicaciones-skype-aucusada-200810030046.html") of allowing chinesse authorities to spy the users.
- Occidentals are not safe either: It seems that [a function to extract]("http://blog.philpep.org/post/Skype-:-un-logiciel-qui-vous-veut-du-bien") your favourites/bookmarks and your downloads could be built-in.
- When turned off, it seems that it could be still "alive" (doing what?). [The suspects of a backdoor]("http://www.h-online.com/security/news/item/Speculation-over-back-door-in-Skype-736607.html") have been around for long.

--> Software is not only a set of tools. It manages your whole info (personal docs, habbits, friends lists ...) You've the right of knowing what exactly your software does with that. Formats are not only dumb containers. They are the key to access the info inside. You should have the right to access the information (be in flash or ??movie format, or whatever). Hence the need to fight for open formats, not closed protocols.

Just a reminder. Well... what about Ekiga ?
___________________________

---

### Post by robert-e on 2009-11-27
J C,
I am pretty green at this PA stuff, but I seem to recall that executing:

pulseaudio -k   is largely ineffective, as it very quickly restarts again.  I remember something about editing a conf file containing something about "autospawn  blah blah"??? 

On a more general note; it seems to me that more and more services are being moved into the kernel, and are becoming more and more difficult to erradicate; including sound, video, and wireless.  Modular linux is becoming less so.
Regards,
Bob

---

### Post by Zoot7 on 2009-11-27
> **JC Cheloven said:**
> Just a reminder. Well... what about Ekiga ?
I've been wondering about Ekiga for a while now, but I've never got around to getting anyone else to try it out with me yet.
But If I can get an open source alternative to skype I'm all for it! :)

---

### Post by Wilbefast on 2009-11-28
> **JC Cheloven said:**
> Just a reminder. Well... what about Ekiga ?

My mum's a bit of a noob when it comes to computers, which is why we've stuck to Skype so far (bit of background: I'm doing uni in France, she lives in Australia). I agree with everything you said though, perhaps it's time she learned ;)

---

### Post by PC_load_letter on 2009-11-29
> **nullrend said:**
> The above procedure works. I'll just repeat it for extra points, marked up properly.

Here is what I did to remove pulse audio in Karmic:

```
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
$ sudo apt-get autoremove
``````
$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
``````
$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
```restart your computer!



I just installed Karmic 64bit on my desktop with M-Audio 2496 sound card and guess what? No sound at all!
I followed the the steps in the quote above and restarted, and was greeted by Ubuntu's login sound:guitar:=D>=D>=D>. 

Regarding the volume control, which disappeared from the panel, I replaced it with envy24 control applet which is part of the alsa-utils package that I installed from the repos.

Many many thanks to all you guys. 

Best.

---

### Post by guillemsola on 2009-11-30
COOL!!! :popcorn:

Useful post

After remove pulseaudio I can hear music again! With pulse rhytmbox stopped, spotify crashed and freezed... even MOCP blocked!!!

Unfortunately the volume icon is not the same, Is there any applet that allow mouse wheel to change headphones level in alsa?

---

### Post by VertexPusher on 2009-11-30
> **Hugo Alvarado said:**
> Here is what I did to remove pulse audio in Karmic:

sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove

sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui

sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer

restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)
-remove gstreamer0.10-pulseaudio to get sound in totem
-gnome-alsamixer is for changing the volume, not an applet but better that nothing

Enjoy!
Some suggestions:

Purging pulseaudio will remove ubuntu-desktop as well. That's not a problem per se, but if you run autoremove afterwards, it may remove the entire desktop (which has been installed as a dependency of ubuntu-desktop). The outcome depends on the state of the other packages, so you should never recommend autoremove and expect the same results for everyone.

Before removing shared dependencies, you should make sure that the alternatives are installed. For example, Totem and Rhythmbox depend on gstreamer0.10-pulseaudio _or_ gstreamer0.10-alsa. If you remove the former before installing the latter, both applications will be gone. If you reverse the order, they will stay.

Installing esound and related packages in Karmic is pointless. No application uses them, and Gnome will not even start up esd any more. Those packages will just sit on your disk and do nothing.

Anyone using VLC may want to remove vlc-plugin-pulse as well.

---

### Post by JC Cheloven on 2009-12-01
Thanks Vertex for your pointings.

> **robert-e said:**
> J C,
I am pretty green at this PA stuff, but I seem to recall that executing:
pulseaudio -k   is largely ineffective, as it very quickly restarts again.  (...)
Bob

Hey, that's why one has to do that I suggested in #42. To sum up again:

1) Do create (once in life) the file ~/.pulse/client.conf contaning the single line:
      autospawn = no
2) When you want pulse not bothering, run ~$ pulseaudio -k
3) When you want pulse around again, run  ~$ pulseaudio -D

It's easy, no root privileges are required, and works.

---

### Post by JC Cheloven on 2009-12-01
> **PC_load_letter said:**
>  (...)Regarding the volume control, which disappeared from the panel, I replaced it with envy24 control applet which is part of the alsa-utils package that I installed from the repos. (...)


Just for other people seeing that: the envy24 bit only applies if you actually have a ICE1712 card in your system.

---

### Post by Wilbefast on 2009-12-01
I installed Kubuntu-desktop and now I can use the hardware volume control again :D

Also flash seems to be working as well ;)

This is fantastic, think I'm going to start again with a fresh Kubuntu!

---

### Post by Zoot7 on 2009-12-01
Yeah neither Kubuntu or Xubuntu have Pulse.

---

### Post by PC_load_letter on 2009-12-05
> **JC Cheloven said:**
> Just for other people seeing that: the envy24 bit only applies if you actually have a ICE1712 card in your system.


You're right, but then anyone can still use Gnome-alsamixer (it's in the repos), right?

---

### Post by PC_load_letter on 2009-12-05
A follow-up to my earlier post. Although I was successful in removing PA and everything is fine, I'm having trouble with "Sound" preferences. I select it from the menu, and I get a "Waiting for sound system to respond" then it disappears. The "system testing" utility (from the Administration menu) recognizes my card and correctly plays the beep sound.

My question is: Is there a way to recover the sound preference menu? Or at least be able to change the preferences from a file?

Thanks.

---

### Post by Wilbefast on 2009-12-06
I've downgraded to 9.04 (but kept the 64 bit) - after 2 weeks of absolute hell I've got a working computer again :KS

Don't know what 9.04 uses but whatever it is it works. Phew!

---

### Post by Zoot7 on 2009-12-06
> **PC_load_letter said:**
> You're right, but then anyone can still use Gnome-alsamixer (it's in the repos), right?
There's no reason why you wouldn't be able to.

---

### Post by Zoot7 on 2009-12-06
> **PC_load_letter said:**
> My question is: Is there a way to recover the sound preference menu? Or at least be able to change the preferences from a file?
Not sure about configuring from a file, but there's no way to get the menu's back without pulseaudio.

---

### Post by tommcd on 2009-12-06
> **PC_load_letter said:**
> ... I'm having trouble with "Sound" preferences. I select it from the menu, and I get a "Waiting for sound system to respond" then it disappears. The "system testing" utility (from the Administration menu) recognizes my card and correctly plays the beep sound.

I had the same thing happen to me. I don't miss the sound-preferences though. I just set MPlayer to use alsa and forget about it.
I pretty much use MPLayer for all audio and video. I run MPlayer right off the terminal. No need even for a GUI.

---

### Post by CylnZ on 2009-12-06
What is Ubuntu's commitment to Pulse? It seems to cause more problems than benefits. Ever since I installed Ubuntu 8.10 I'v e had a miserable time with Intel HDA. Made the system mostly worthless, choppy video (due to PA high cpu usage spikes) off/on audio whenever it bloody well felt like it, on boot muted sound until I unmuted it all it shell alsamixer, etc. I followed your guide here to just dump it, and YIPPEE! I finally have a decent multimedia system that works all the time, even on startup.

Thanks so much :)

I reiterate, what's the passion for pulse if it drives new users back to windows?

---

### Post by Roger Allott on 2009-12-06
> **nullrend said:**
> The above procedure works. I'll just repeat it for extra points, marked up properly.

Here is what I did to remove pulse audio in Karmic:

```
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
$ sudo apt-get autoremove
``````
$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
``````
$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
```restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)[INDENT]This means:
```
$ gstreamer-properties
```[/INDENT]-remove gstreamer0.10-pulseaudio to get sound in totem.[INDENT]The above commands should have taken care of that, but it never hurts to be sure when talking about the hydra that is PulseAudio.
[/INDENT]-gnome-alsamixer is for changing the volume, not an applet but better that nothing[INDENT]This means you are left without a panel applet to control volume across the board, thanks to the thoughtful efforts of Canonical to shove PulseAudio down our throats. So you need to have something to control audio with:
```
$ sudo apt-get install gnome-alsamixer
```And something to keep gnome-alsamixer within easy reach, provided by AllTray:
```
$ sudo apt-get install alltray
```[/INDENT]Now, one last word of advice. Usually the best solution is to use aptitude or synaptic to do these moves, but you'll run headfirst into their dependency resolution efforts, which command them to put PulseAudio back in your system when reinstalling gnome-alsamixer. So either you use apt-get or you reconfigure aptitude/synaptic dependency resolution to work the way you want.

I've just tried doing this but aborted when the first command produced:
```
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
[sudo] password for stuart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gstreamer0.10-pulseaudio* libcanberra-pulse* padevchooser* paprefs*
  pulseaudio* pulseaudio-esound-compat* pulseaudio-module-bluetooth*
  pulseaudio-module-gconf* pulseaudio-module-udev* pulseaudio-module-x11*
  pulseaudio-module-zeroconf* ubuntu-desktop*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
After this operation, 6,443kB disk space will be freed.
Do you want to continue [Y/n]?
```

I can live with all of those packages being removed, but removing ubuntu-desktop??????

---

### Post by tommcd on 2009-12-07
> **CylnZ said:**
> What is Ubuntu's commitment to Pulse? It seems to cause more problems than benefits....
I reiterate, what's the passion for pulse if it drives new users back to windows?
From what I have read, pulse audio seems to be the future sound standard in linux. See this article:
[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it](http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it)
Fedora is using pulse audio also:
[http://fedoraproject.org/wiki/Interviews/LennartPoettering](http://fedoraproject.org/wiki/Interviews/LennartPoettering)
> PulseAudio is a next generation sound server for Linux, making all sorts of "ear-candy" possible ...
To my ears, pulse audio does not sound any better than alsa. 
From a quick google search, it seems that Fedora users are having just as many problems with pulse audio as us Ubuntu users.

And for Ubuntu specifically:
[http://ossguy.com/?p=347](http://ossguy.com/?p=347)
[https://wiki.ubuntu.com/DesktopTeam/Specs/CleanupAudioJumble](https://wiki.ubuntu.com/DesktopTeam/Specs/CleanupAudioJumble)
I suspect that all the difficulties with pulse audio will be fixed as it matures. This will have to wait for future Ubuntu releases unfortunately. In the meantime will will just have to work around it.
The biggest problem I have with pulse audio is that it is a resource hog compared to alsa. I really hope this is fixed in future releases.

---

### Post by Zoot7 on 2009-12-07
> **tommcd said:**
> From what I have read, pulse audio seems to be the future sound standard in linux. See this article:
[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it](http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it)
Fedora is using pulse audio also:
[http://fedoraproject.org/wiki/Interviews/LennartPoettering](http://fedoraproject.org/wiki/Interviews/LennartPoettering)

To my ears, pulse audio does not sound any better than alsa. 
From a quick google search, it seems that Fedora users are having just as many problems with pulse audio as us Ubuntu users.

And for Ubuntu specifically:
[http://ossguy.com/?p=347](http://ossguy.com/?p=347)
[https://wiki.ubuntu.com/DesktopTeam/Specs/CleanupAudioJumble](https://wiki.ubuntu.com/DesktopTeam/Specs/CleanupAudioJumble)
I suspect that all the difficulties with pulse audio will be fixed as it matures. This will have to wait for future Ubuntu releases unfortunately. In the meantime will will just have to work around it.
The biggest problem I have with pulse audio is that it is a resource hog compared to alsa. I really hope this is fixed in future releases.
The main feature I'm interested in that Pulse touts is a system wide equalizer.

---

### Post by seeker5528 on 2009-12-07
> **tommcd said:**
> From what I have read, pulse audio seems to be the future sound standard in linux. See this article:
[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it](http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it)
Fedora is using pulse audio also:
[http://fedoraproject.org/wiki/Interviews/LennartPoettering](http://fedoraproject.org/wiki/Interviews/LennartPoettering)

To my mind, you have to question an article that claims:

> And that's the point: some apps are written to use the userspace ALSA API, some aRts, some JACK, some handle the audio internally. If you can reroute all of the audio through one handler, you get more control, fewer conflicts, and fewer surprises.

Pulseaudio does give you some options you don't have if you don't use it, but overall you have less control with it than without.

Confusion doesn't go away either. Apps will still be programed to use gstreamer, OpenAL, Phonon, JACK, etc... each with their own potential set of issues as it relates to Pulseaudio. 

In particular with the insistence on the developer side that Pulseaudio needs exlusive access the the audio hardware, just when were getting rid of Artsd and things were looking up.

Does it seem less confusing that with Pulseaudio the list applications that you might not be able to have sound in at the same time doesn't seem any shorter, just different?

Or the situations when audio isn't working out of the box doesn't seem any less, just different?

Or that times that things work fine using alsa directly but are screwy with Pulseaudio still seem way too common but it gets used as the default anyway with Gnome? 

Is it less confusing when you pay extra for more capable hardware with more options, and those extra sliders/controls are shown by the alsa mixers but with only pulseaudio stuff, your hardware control is just as limited as with the more basic hardware?

And if, for example, you record from line 1 and need to mute the output from line 1 in one applications so it doesn't create a feedback loop and unmute it in another so you can hear what is going on, does Pulseaudio provide the necessary control?

Later, Seeker

---

### Post by sieve on 2009-12-10
I was able to successfully remove Pulseaudio using the procedures listed by nullrend in post #4.  However, after doing so, I could not get the system to recognize my Creative Soundblaster X-Fi Notebook external soundcardcard. Which was odd, because supposedly the X-Fi driver is part of Alsa in 9.10/Karmic. 

Maybe it is possible to get the system to recognize the X-Fi, but I don't know enough about it to know how. If anyone else does, I'd appreciate their input.

---

### Post by Zoot7 on 2009-12-10
You could give upgrading to Alsa 1.0.21 a shot, the stable, tried and tested X-Fi driver is included in that. There's a nice upgrade script posted here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by sieve on 2009-12-10
> **Zoot7 said:**
> You could give upgrading to Alsa 1.0.21 a shot, the stable, tried and tested X-Fi driver is included in that. There's a nice upgrade script posted here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

I should recheck, but I just did a fresh install of Karmic the other day and updated Alsa and I think I already have the most current version.

---

### Post by Zoot7 on 2009-12-10
> **sieve said:**
> I should recheck, but I just did a fresh install of Karmic the other day and updated Alsa and I think I already have the most current version.
Well yeah if you updated Alsa to the latest version as you say, then you're running 1.0.21.
Forgot to suggest this to you:
Install the Gnome-Alsamixer and investigate if there's a channel muted by default.
```
sudo apt-get install gnome-alsamixer
```

or just use 
```
alsamixer
```
from the command line.

People have been reporting their Volume being muted in Karmic by default.

---

### Post by sieve on 2009-12-11
> **Zoot7 said:**
> Forgot to suggest this to you:
Install the Gnome-Alsamixer and investigate if there's a channel muted by default.

People have been reporting their Volume being muted in Karmic by default.

There were channels muted, but they were for microphones and other inputs. I unmuted them all, but still no luck.

I wish there was some way in Alsa to toggle between sound cards like in Pulseaudio. Actually, it's surprising that the external soundcard doesn't just automatically override and take precedence to the internal card.

---

### Post by Sammaye on 2009-12-13
I found the command:- padsp to be very useful. Run this on a shortcut (at the beginning of the command) and it will disable Pulse from running on that App. Works perfect for Wine.

---

### Post by sieve on 2009-12-16
> **sieve said:**
> I wish there was some way in Alsa to toggle between sound cards like in Pulseaudio. Actually, it's surprising that the external soundcard doesn't just automatically override and take precedence to the internal card.

I was able to solve the problem, as discussed in this post:
[http://ubuntuforums.org/showpost.php?p=8501268&postcount=24](http://ubuntuforums.org/showpost.php?p=8501268&postcount=24)

---

### Post by sieve on 2009-12-16
> **Sammaye said:**
> I found the command:- padsp to be very useful. Run this on a shortcut (at the beginning of the command) and it will disable Pulse from running on that App. Works perfect for Wine.

That sounds useful, as I do use Wine for various applications.
Thanks!

---

### Post by Zoot7 on 2009-12-16
> **sieve said:**
> I was able to solve the problem, as discussed in this post:
[http://ubuntuforums.org/showpost.php?p=8501268&postcount=24](http://ubuntuforums.org/showpost.php?p=8501268&postcount=24)
What that does is disable the power saving features that automatically turn on and off the Audio chip thus producing snaps or crackles at times.

---

### Post by sieve on 2009-12-16
Zoot7, did you mean what Sammaye posted above?

> **Sammaye said:**
> I found the command:- padsp to be very useful. Run this on a shortcut (at the beginning of the command) and it will disable Pulse from running on that App. Works perfect for Wine.

For me, the problem was more than the snap crackle and pop. The sound quality itself was bad. The high frequencies sounded tinny and midranges sounded echoey and slightly garbled.

---

### Post by Zoot7 on 2009-12-17
Opps, my bad.
I'd the same problem with crackles upon startup and startup alone thanks to that power saving feature.

---

### Post by User3k on 2009-12-17
> **slumbergod said:**
> yeah, i totally agree - pulseaudio was never anything but a headache for me. It crackled and popped all the time. The first thing i did was replace it after any new installation.

Imagine my delight to find xubuntu 9.10 didn't have pulse!!!!

+1

---

### Post by GodLikeCreature on 2009-12-18
Hey, 

I am using Ubuntu Studio 9.04, which by default comes with network manager applet disabled.  I would like to keep it that way, so here´s my question:

Can I remove pulse audio without having to install anything else?  As far as I know, Ubuntu Studio already has the ALSA packages on board?

Thanks

---

### Post by garyedwardjohnston on 2009-12-30
Very nice...if fixed my problems in Karmic

---

### Post by Tulth on 2010-01-01
I constantly have sound problems as well in Karmic_amd64 9.10.  I wish someone would just bury pulseaudio once and for all.  It simply does not work.

---

### Post by Zoot7 on 2010-01-01
> **GodLikeCreature said:**
> Can I remove pulse audio without having to install anything else?  As far as I know, Ubuntu Studio already has the ALSA packages on board?
If you're using Jaunty you should be able to.

> **Tulth said:**
> I constantly have sound problems as well in Karmic_amd64 9.10.  I wish someone would just bury pulseaudio once and for all.  It simply does not work.
Sadly Pulseaudio is here to stay, if you wanted something Ubuntu-like that does not use Pulseaudio, then just regular Debian is a good candidate.

---

### Post by User-007 on 2010-01-02
Hi all,

Thanks for your guide.

I followed that and just got ALSA working for system sounds and various programs. My problem is Totem - I got no sound when trying to open anything with that. I have removed gstreamer0.10-pulse and installed gstreamer0.10-alsa, set ALSA for a default in gstreamer-properties etc etc. Any suggestions? Totem would be very handy for watching DVD's and for a browser plugin.

I'm using Karmic.

Thanks in advance
User JB

---

### Post by woodmaster on 2010-01-02
thanks very much...works great!!!

---

### Post by Alex_W on 2010-01-06
Hi all,

Great guide, thank you!

I understand our troubles with PulseAudio are slightly different from case to case... so, here is mine:

HW: Laptop HP Pavillion DV42** series, Intel ICH6-type card onboard.

On Jaunty, sound worked out-of-the-box, no tinkering required.

With Karmic, I had several issues:[INDENT]crackling/stuttering sound on login (apps worked more-less tolerably);

inability to store volume settings: after PA restart (logout-login, for example), the volume levels would return to some pre-specified (somewhere... I couldn't find where) levels, including **100% on the headphones channel** (the most annoying thing).

[/INDENT]What I have tried before removing PA (obviously, all this didn't work for me):
[INDENT]updating the system as outlined in the "Comprehensive MultiMedia Guide" on this forum;

installing "the rest of" PA (like pavchooser, etc.)

upgrading ALSA to 1.0.21

numerous edits to config files (changing "merge" to "ignore", etc.)

[/INDENT]Instructions in this thread worked perfectly well.
What works:
[INDENT]the sound (system; audio via Rhythmbox, MPlayer, VLC; DVD/video via VLC, GXine, Movie Player, flash/YouTube).

[/INDENT]What stopped working:
[INDENT]volume control via mediabuttons (only volume-up, down, and mute were lost)
[/INDENT]Workaround (that did the trick for me): in the System/Preferences/Keyboard Shortcuts, I had to create _new_ associations for Vol Up, Down, Mute with amixer command, like this:

```
amixer -c 0 set Master 3dB+
``````
amixer -c 0 set Master 3dB-
``````
amixer -c 0 set Master 0%
```[INDENT]volume applet -- not a huge deal for now ;)

[/INDENT]Cheers!

---

### Post by brocktice on 2010-01-13
The instructions here worked great for me on Karmic x86_64, on a Mac Pro. Thanks everyone, particularly for the pointer on the volume buttons.

---

### Post by voxman69 on 2010-01-15
Thank you so much for this! I applied this to Mint 8 and the only thing out of the ordinary that happened was that Gnome-Do was removed, but I just re-installed it and now everything is fine.

I followed the guide on making new keyboard shortcuts for volume up/down which was the way I changed volume earlier anyhow.

Spotify is now smoothly playing music and I also have more free memory by some 7-8 percent according to Sysinfo.

---

### Post by The-NightPhoenix on 2010-01-18
I made a script to control alsa for the media keys and to provide notifications.

i could't do the notifications well, it became a bit crappy so i disabled it **so if u please check it out and modify it **

Also If any one can do something for the mute thing . to unmute and not to increase the volume up again

to use it : 
Extract The File.
put it in the "/usr/bin" folder
```
sudo cp AlsaControler /usr/bin
```

give it executable permissions 
```
sudo chmod +x /usr/bin/AlsaControler
```

and change the shortcut keys to : 
Volum UP :
```
 AlsaControler up 
```
Volum Down :
```
 AlsaControler down 
```
Volum Mute :
```
 AlsaControler mute 
```

---

### Post by mgol on 2010-01-18
> **The-NightPhoenix said:**
> I made a script to control alsa for the media keys and to provide notifications.
Sorry to say this but You just wasted Your time. Such scripts have already been done:
[http://ubuntuforums.org/showpost.php?p=8130297&postcount=25](http://ubuntuforums.org/showpost.php?p=8130297&postcount=25)
They support nice Jaunty notifications and a sound icon in system tray, I'd advise to use these ones - I do and they do their job.

---

### Post by The-NightPhoenix on 2010-01-19
Thnax alot that is really good .

---

### Post by head2head on 2010-01-19
Quick question. I've got problems with pulseaudio in ubuntu (gnome) and would like to give KDE a try.

Would running 'sudo apt-get install kubuntu-desktop' be all that's needed to get rid of pulseaudio, or would I have to uninstall via terminal?

---

### Post by jack.herbert on 2010-01-19
Hi everybody,
Disclaimer: I know Ubuntu is free and canonical doesn't owe me anything whatsoever but oh boy, I just had one hell of an annoying afternoon.
Never had any problems with pulse audio for general use, but as soon as you want to do some more involved ardour / jack recording, the headache begins.

I ended up opening synaptic, removed pulse-audio (I only saw this thread afterwards) and installed k-mix. Probably not recommended but so far so good. At least the the line-in signal comes through. I've only lost sound playback with gnome-player, but i use vlc anyway.

What really really pissed me off is not being able to use the gnome-panel volume control for anything else BUT pulse. Who came up with THAT idea? Red flag indeed.

Anyway, cheers for this thread, very helpful.

---

### Post by farna on 2010-01-20
Maybe I should start a new thread, but my troubles are related. I'm running Mint 8 (Ubuntu 9.10 based) AMD x64 version on a PC with a quad core AMD processor and 4GB of ram -- plenty power.  I bought a Turtle Beach Riviera sound card because I needed one with optical (or coaxial) digital output and reviews indicated it worked fine with Ubuntu. That was before Pulse Audio, apparently. I have every indication that the card will work with ALSA, so I followed the instructions in this thread and removed PA and installed ALSA. Still no sound!

This is an HTPC, so right now it's useless. When I try to set properties for the card (computer sees it just fine!) it tells me the card is in use, but nothing is running that would need it! Here's the output I get:

swygert@Living-Room ~ $ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. Device is being used by another application. [gstalsasink.c(685): gst_alsasink_open (): /GstPipeline /pipeline0/GstAlsaSink:alsasink3:
Device 'default' is busy]


lspci:
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

So why no sound?  Are the "unavailable plugins" the problem? 

I have the computer connected to my 52" flat screen through a Sony AV receiver. Video is fine (HDMI cords), and I made sure I have the optical cable in the correct position. I'm using the computer right now, just no sound!! I need something that will send a surround sound signal to the receiver, it won't work over the HDMI cable (a disappointment, but I understand HDMI doesn't have the bandwidth). 

If there is a sound card with optical and/or coaxial digital output known to work with 9.10 I will return the card and try another. Otherwise I may have to install Windows XP and just forget Linux. It's not quite as mature as I thought, and I'm getting tired of fighting with it. A friend called me "Don Quioxte" when I described some of the problems, and it's starting to fit.... (he uses an Apple).

I was looking at teh upgrade ALSA script post, thinking that might be the problem, abd I get this:

swygert@Living-Room ~ $ speaker-test -Dplughw:0,0 -c2 

speaker-test 1.0.20

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
(continuous loop -- have to close terminal to stop)

So something is "using" the card, but I have no idea what it could be. Noting in System Monitor/Processes that could be using sound. The only apps open as I type this are Firefox, Terminal, and System Monitor. I cut the computer completely off after removing PA.

---

### Post by farna on 2010-01-20
I'm working through the forums on this! While the computer recognizes the sound card, maybe I don't have the proper drivers installed. Got that tip from [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=205449&highlight=optical+sound](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=205449&highlight=optical+sound). I went through the instructions and downloaded the latest ALSA files after going to the ALSA site and finding drivers. Everyting compiled fine, then I got this:

make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
utils/link-modules /home/swygert/alsa-driver-1.0.22.1

ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/swygert/alsa-driver-1.0.22.1/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
rm: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
rm: cannot remove `/usr/include/sound/hdsp.h': Permission denied
rm: cannot remove `/usr/include/sound/hdspm.h': Permission denied
rm: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
rm: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
rm: cannot remove `/usr/include/sound/asequencer.h': Permission denied
rm: cannot remove `/usr/include/sound/sscape_ioctl.h': Permission denied
rm: cannot remove `/usr/include/sound/asound.h': Permission denied
rm: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
install: cannot create regular file `/usr/include/sound/ac97_codec.h': Permission denied
install: cannot create regular file `/usr/include/sound/aci.h': Permission denied
install: cannot create regular file `/usr/include/sound/ad1816a.h': Permission denied
install: cannot create regular file `/usr/include/sound/ad1843.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4113.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4114.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4117.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4531_codec.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4xxx-adda.h': Permission denied
install: cannot remove `/usr/include/sound/asequencer.h': Permission denied
install: cannot remove `/usr/include/sound/asound.h': Permission denied
install: cannot remove `/usr/include/sound/asound_fm.h': Permission denied
install: cannot create regular file `/usr/include/sound/asoundef.h': Permission denied
install: cannot create regular file `/usr/include/sound/atmel-abdac.h': Permission denied
install: cannot create regular file `/usr/include/sound/atmel-ac97c.h': Permission denied
install: cannot create regular file `/usr/include/sound/control.h': Permission denied
install: cannot create regular file `/usr/include/sound/core.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs4231-regs.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs8403.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs8427.h': Permission denied
install: cannot remove `/usr/include/sound/emu10k1.h': Permission denied
install: cannot create regular file `/usr/include/sound/emu10k1_synth.h': Permission denied
install: cannot create regular file `/usr/include/sound/emu8000.h': Permission denied
install: cannot create regular file `/usr/include/sound/emu8000_reg.h': Permission denied
install: cannot create regular file `/usr/include/sound/emux_legacy.h': Permission denied
install: cannot create regular file `/usr/include/sound/emux_synth.h': Permission denied
install: cannot create regular file `/usr/include/sound/es1688.h': Permission denied
install: cannot create regular file `/usr/include/sound/gus.h': Permission denied
install: cannot create regular file `/usr/include/sound/hda_hwdep.h': Permission denied
install: cannot remove `/usr/include/sound/hdsp.h': Permission denied
install: cannot remove `/usr/include/sound/hdspm.h': Permission denied
install: cannot create regular file `/usr/include/sound/hwdep.h': Permission denied
install: cannot create regular file `/usr/include/sound/i2c.h': Permission denied
install: cannot create regular file `/usr/include/sound/info.h': Permission denied
install: cannot create regular file `/usr/include/sound/initval.h': Permission denied
install: cannot create regular file `/usr/include/sound/jack.h': Permission denied
install: cannot create regular file `/usr/include/sound/l3.h': Permission denied
install: cannot create regular file `/usr/include/sound/memalloc.h': Permission denied
install: cannot create regular file `/usr/include/sound/minors.h': Permission denied
install: cannot create regular file `/usr/include/sound/mixer_oss.h': Permission denied
install: cannot create regular file `/usr/include/sound/mpu401.h': Permission denied
install: cannot create regular file `/usr/include/sound/opl3.h': Permission denied
install: cannot create regular file `/usr/include/sound/opl4.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm-indirect.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm_oss.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm_params.h': Permission denied
install: cannot create regular file `/usr/include/sound/pt2258.h': Permission denied
install: cannot create regular file `/usr/include/sound/pxa2xx-lib.h': Permission denied
install: cannot create regular file `/usr/include/sound/rawmidi.h': Permission denied
install: cannot create regular file `/usr/include/sound/s3c24xx_uda134x.h': Permission denied
install: cannot create regular file `/usr/include/sound/sb.h': Permission denied
install: cannot remove `/usr/include/sound/sb16_csp.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_device.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_kernel.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_midi_emul.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_midi_event.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_oss.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_oss_legacy.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_virmidi.h': Permission denied
install: cannot remove `/usr/include/sound/sfnt_info.h': Permission denied
install: cannot create regular file `/usr/include/sound/sh_dac_audio.h': Permission denied
install: cannot create regular file `/usr/include/sound/sh_fsi.h': Permission denied
install: cannot create regular file `/usr/include/sound/snd_wavefront.h': Permission denied
install: cannot create regular file `/usr/include/sound/soc-dai.h': Permission denied
install: cannot create regular file `/usr/include/sound/soc-dapm.h': Permission denied
install: cannot create regular file `/usr/include/sound/soc-of-simple.h': Permission denied
install: cannot create regular file `/usr/include/sound/soc.h': Permission denied
install: cannot create regular file `/usr/include/sound/soundfont.h': Permission denied
install: cannot create regular file `/usr/include/sound/tea575x-tuner.h': Permission denied
install: cannot create regular file `/usr/include/sound/tea6330t.h': Permission denied
install: cannot create regular file `/usr/include/sound/timer.h': Permission denied
install: cannot create regular file `/usr/include/sound/tlv.h': Permission denied
install: cannot create regular file `/usr/include/sound/tlv320dac33-plat.h': Permission denied
install: cannot create regular file `/usr/include/sound/tpa6130a2-plat.h': Permission denied
install: cannot create regular file `/usr/include/sound/trident.h': Permission denied
install: cannot create regular file `/usr/include/sound/uda134x.h': Permission denied
install: cannot create regular file `/usr/include/sound/uda1380.h': Permission denied
install: cannot create regular file `/usr/include/sound/util_mem.h': Permission denied
install: cannot create regular file `/usr/include/sound/version.h': Permission denied
install: cannot create regular file `/usr/include/sound/vx_core.h': Permission denied
install: cannot create regular file `/usr/include/sound/wavefront.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8904.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8955.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8993.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm9081.h': Permission denied
install: cannot create regular file `/usr/include/sound/wss.h': Permission denied
install: cannot create regular file `/usr/include/sound/ymfpci.h': Permission denied
make: *** [install-headers] Error 1
swygert@Living-Room ~/alsa-driver-1.0.22.1 $ 


Does this mean I should use sudo and manually accomplish these tasks, or am i barking up the wrong tree??

---

### Post by mikewhatever on 2010-01-20
You have to run the last command with sudo, ie **sudo make install**, or, in fact, whatever command you tried running in that case.

And just to chip in my 2 cents, removing PA didn't work at all. I had alsa related 'spurious response' errors in the logs, and no sound.

---

### Post by farna on 2010-01-21
Thanks for trying Mike, but that isn't the problem. If i run using sudo the script still starts erroring out after "ALSA modules were successfully compiled". It saved the part between that text and the first error as an executable script file and ran it with sudo. With that I get: 
swygert@Living-Room ~ $ sudo ./sound_card_script.sh
[sudo] password for swygert: 
install: cannot stat `include/sound/*.h': No such file or directory

I think I found the problem. There is a this note in the script: 
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting

It appears that the files which should be in /usr/include/sound are not there, they are in the Alsa upgrade directory from where the script was run (alsa-driver-1.0.22.1/include/sound. 

I'm relatively new to Linux, and I can't simply copy the files to /usr/include/sound due to permissions without going to the command line, and I don't know the commands. In some ways Linux is as bad or worse than Windows. I know the intent is to keep someone from messing the system up, but it's frustrating to not be able to use the GUI tools to do what would be simple tasks. I really despise being locked out of my computer. Now I have to go back and look up how to log on as super user, log out, and log back in so I can screw it up more, since Ubuntu screwing up the sound system to begin with wasn't bad enough. Yeah, blowing off some steam... been called "Don Quioxte" for trying to make Ubuntu (Linux Mint 8x64) work instead of installling Windows, and it's beginning to feel that way. Sound should be easy to get.

---

### Post by farna on 2010-01-21
Got the sound problem fixed. i removed PulseAudio, and got the latest Alsa drivers installed. Copying the files did the trick. Still had no sound. Found a blog site describing installing the card ([http://mymythtv.blogspot.com/2005_06_01_archive.html](http://mymythtv.blogspot.com/2005_06_01_archive.html)). 

Alsamixer turned out to be the clincher. May have worked from the start if I'd known the settings! Of the 7 IEC958 controls, only "output" should be activated, the others muted or turned off. The others have no noticeable effect except "loop", which kills sound output. 

I knew it had to be something simple I just couldn't see 9forest for trees?). I'd tried several different settings in Alsamixer, but didn't think to turn all settings off and try one at a time -- what seems to be the logical approach now! Not sure if PulseAudio needed to be removed or the latest Alsa drivers installed or not. Anyone reading this should try Alsamixer first, with ONLY "IEC958 Output" selected of the IEC958 attributes. The other settings shouldn't effect digital sound, but I'd turn all that off to begin with too, then turn on and try once you get digital sound.

---

### Post by mikewhatever on 2010-01-21
So, it looks like you went the long way just to find out about the setting that needed to be activated. As for permissions, it can be frustrating at times, but once you know how to start the file browser as root, it's easy. Use <gksudo nautilus> to do that.

---

### Post by Skerit on 2010-02-02
Removing pulseaudio worked.

However, while I do have sound in totem and such, I hear NOTHING from the start-up sounds or in programs like ultrastardx. What's wrong?

---

### Post by mgol on 2010-02-03
> **Skerit said:**
> However, while I do have sound in totem and such, I hear NOTHING from the start-up sounds or in programs like ultrastardx.
Did You try this:
[http://ubuntuforums.org/showpost.php?p=8373458&postcount=13](http://ubuntuforums.org/showpost.php?p=8373458&postcount=13)
? If You follow all the steps and it still fails, please write again.

---

### Post by Lorso on 2010-02-08
Hello,

I've recently bought a mini 311 HP netbook and installed UNR 9.10 on it. It was all ok but audio out when playing streams and mp3s was someway confused and popping/glitching all the time. 

So I decided to remove pulseaudio: I followed instuctions as reported on post #3 & 4#, but done that both Rhyhtmbox and Audacious2 gave me error messages and played no sound at all. System sounds were ok, mp3 preview from nautilus worked flawlessly.

I solved with Rhythmbox uninstalling and reinstalling it via Synaptic. For Audacious2, I modified the config file located in ~/.config/audacious/ changing the output plugin line to ALSA.so

```
output_plugin=/usr/lib/audacious/Output/ALSA.so (#0)
```

Now all works correctly, including Skype 2.10 (is it possible!?)

I have solved the issue with volume control via keyboard following post #36 instructions: I've lost OSD notifications, but I'm happy anyway.

The only pity is I have lost the speaker tray icon and I don't know how to replace it: can you help me?

Thanks a lot,

L.

---

### Post by nerdy_kid on 2010-02-23
ya know....why not just do
```

sudo chmod -x /usr/bin/pulseaudio
killall pulseaudio

```

i have this one game that doesnt like pulseaudio and i do that every time i play it, and everythings pretty ;)

---

### Post by ublintu on 2010-02-23
Hi,
I didn't read all of the post, so if someone posted it sorry.

Volume controller buttons are working for me!!

post #3 [http://ubuntuforums.org/showthread.php?t=1377667](http://ubuntuforums.org/showthread.php?t=1377667)

there you will find this link: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

Good luck.

---

### Post by woodmaster on 2010-02-23
> **nerdy_kid said:**
> ya know....why not just do
```

sudo chmod -x /usr/bin/pulseaudio
killall pulseaudio

```i have this one game that doesnt like pulseaudio and i do that every time i play it, and everythings pretty ;)

For me, that would've been necessary everytime I started as pulseaudio errors were pretty much constant and ate up my Memory after a while causing freezing

---

### Post by nerdy_kid on 2010-02-23
> **woodmaster said:**
> For me, that would've been necessary everytime I started as pulseaudio errors were pretty much constant and ate up my Memory after a while causing freezing

it is consistent from boot to boot, so you would only have to do it once.

---

### Post by Oceola on 2010-02-25
I tried to leave pulse on the system and it did work for a while but the interactivity with something else had it making large files (64MB) in the /dev/shm/folder. I think it was more my hardware than the program as it's probably tailored for newer equipment, I'm running an antique here. One thing I found was you can't just delete all the packages through the repositories without losing the entire gnome setup and even the login screen. Tried this once and had to reinstall Karmic.
What I did was to remove the packages I could using Synaptic and then going inside the system and doing and search for every related "pulse" I could find including the libasound related to pulse and the canberra. I tried to remove the pulse cookie from the home/name/ folder but no go, each time it would create a new tmp file under /tmp/pulse. I tried to remove the pulse files also from the /dev/shm folder and the /etc/pulse folder to no avail until I did a complete cold reboot. The login had some isses, I think due to being tied into the system loggin sound but when I came back on the remainder of the pulse files could be removed from the various directories which kept regenerating including the /dev/shm; the /tmp/pulse; the /home/name/pulse cookie and the /etc/pulse files.
This left me without sound but an install of the following gave me control of the sound again without the replicating files large 64 MB files.
esound
alsaplayer-common (0.99.80-3.1ubuntu2)
alsaplayer-esd (0.99.80-3.1ubuntu2)
alsaplayer-gtk (0.99.80-3.1ubuntu2)
libid3tag0 (0.15.1b-10build1)
libmad0 (0.15.1b-4)
libmikmod2 (3.1.11-a-6ubuntu4)
esound (0.2.41-5)
gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2)
gnome-audio (2.22.1-1)
Some of the problems I had was a consistent staccato sound like a bad repeater at boot, no playing of sound in some minor games.
I had similar sound problems with pulse in Hardy and this was handled in a similar fashion.

---

### Post by ElectricJake on 2010-03-10
Thanks to Hugo Alvarado, that was a quick and simple way of going about it. 

As for the volume control I use a custom keyboard shortcut as roughly outlined here: 

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1308980](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1308980)

except I substitute PCM in place of Master (my Fast Track USB only has PCM and Mic)

---

### Post by danflash on 2010-03-10
Hold the front page - I've successfully left Pulse...
I'm unsure as to HOW exactly I did it, but I'll bring you up to speed and maybe a more advanced penguin here could put 2+2 together... (see attached pics for proof)

Tried to remove PA a while ago, unsuccessfully, using these guides.  After epic failure, I put PA back on but forgot to remove some ALSA related things first (like alsa-mixer, alsa-utils, the applet(s), etc).
Then did the usual update routine through update manager, and voila - all of a sudden my volume notifier (Fn + Up/Down) was the old ALSA gem, not the one that pops up in the up right like when you change screen brightness.
SO - then I just went into synaptic, unchecked Pulseaudio (note - I didn't do a Purge with apt-get or a 'Mark for COMPLETE removal', I just did the normal standard remove) and for some reason it didnt list 'Ubuntu-desktop' as a dependency or anything.
Since then - I have my tray applet, volume notifier, Skype actually works properly, boot up sounds remain, AND flash works (see attached screen shots for some proof).

So, escape from pulse can be done

Hope that info is of some use to someone, let me know if you need more info + i'll try my best to help.  
Peace

---

### Post by Stosskraft on 2010-03-21
> **nullrend said:**
> The above procedure works. I'll just repeat it for extra points, marked up properly.

Here is what I did to remove pulse audio in Karmic:

```
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
$ sudo apt-get autoremove
``````
$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
``````
$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
```restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)[INDENT]This means:
```
$ gstreamer-properties
```[/INDENT]-remove gstreamer0.10-pulseaudio to get sound in totem.[INDENT]The above commands should have taken care of that, but it never hurts to be sure when talking about the hydra that is PulseAudio.
[/INDENT]-gnome-alsamixer is for changing the volume, not an applet but better that nothing[INDENT]This means you are left without a panel applet to control volume across the board, thanks to the thoughtful efforts of Canonical to shove PulseAudio down our throats. So you need to have something to control audio with:
```
$ sudo apt-get install gnome-alsamixer
```And something to keep gnome-alsamixer within easy reach, provided by AllTray:
```
$ sudo apt-get install alltray
```[/INDENT]Now, one last word of advice. Usually the best solution is to use aptitude or synaptic to do these moves, but you'll run headfirst into their dependency resolution efforts, which command them to put PulseAudio back in your system when reinstalling gnome-alsamixer. So either you use apt-get or you reconfigure aptitude/synaptic dependency resolution to work the way you want.


I have followed these instructions and everything worked great until a re-start.

Now I have NO SOUND and even the log in screen with the ubuntu-drum? is not working. Here is what I get if I type gstreamer-properties in the terminal:

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

```

Also the media selector is using ALSA but no sound when testing.

Any ideas?

Everything worked fine before the restart, not sure what happend.

Thanks

---

### Post by kaligus on 2010-03-22
> **danflash said:**
> Hold the front page - I've successfully left Pulse...
I'm unsure as to HOW exactly I did it, but I'll bring you up to speed and maybe a more advanced penguin here could put 2+2 together... (see attached pics for proof)

Tried to remove PA a while ago, unsuccessfully, using these guides.  After epic failure, I put PA back on but forgot to remove some ALSA related things first (like alsa-mixer, alsa-utils, the applet(s), etc).
Then did the usual update routine through update manager, and voila - all of a sudden my volume notifier (Fn + Up/Down) was the old ALSA gem, not the one that pops up in the up right like when you change screen brightness.
SO - then I just went into synaptic, unchecked Pulseaudio (note - I didn't do a Purge with apt-get or a 'Mark for COMPLETE removal', I just did the normal standard remove) and for some reason it didnt list 'Ubuntu-desktop' as a dependency or anything.
Since then - I have my tray applet, volume notifier, Skype actually works properly, boot up sounds remain, AND flash works (see attached screen shots for some proof).

So, escape from pulse can be done

Hope that info is of some use to someone, let me know if you need more info + i'll try my best to help.  
Peace

I am very interested in knowing how this came to be just so I can have a sound that tells me when my headless machine has completed its bootup!

---

### Post by ahso4271 on 2010-03-22
yea left pulse as well as it crashed flightgear and more. pulseaudio is simply not ready for prime time sorry.

---

### Post by sieve on 2010-03-23
> **Stosskraft said:**
> Now I have NO SOUND and even the log in screen with the ubuntu-drum? 
Also the media selector is using ALSA but no sound when testing.

Any ideas?

Everything worked fine before the restart, not sure what happend.

Thanks

A similar thing happened to me a few days ago.  All of a sudden, no sound.  I think it must be a result of an update that was pushed down.

I was able to fix it.  Offhand, I don't recall how, but if I check some threads here, I should be able to figure it out.  So stay tuned.

---

### Post by Stosskraft on 2010-04-04
I am still having trouble with this. I needed to re-start 5-6 times before I hear the drum on the boot up screen and then the audio works.

Does anyone have any idea what this could be?

Thanks

---

### Post by Z06Gal on 2010-04-18
> **Stosskraft said:**
> I am still having trouble with this. I needed to re-start 5-6 times before I hear the drum on the boot up screen and then the audio works.

Does anyone have any idea what this could be?

Thanks


I do not know what it is but I was having the very same problem having to restart.  Someone on the forum suggested that I disable system sounds in the sound module and I have not had a problem since.  What that does I have no idea but it worked.  :)

---

### Post by zampes on 2010-04-26
All my thanks to Hugo Alvarado; thanks so much for this, solved all my Pulse Audio related problems in 9.10, even 3 days before going 10.04 :)
I described my issues here:
[http://ubuntuforums.org/showthread.php?t=1452145](http://ubuntuforums.org/showthread.php?t=1452145)

---

### Post by sieve on 2010-04-30
For those who have removed Pulseaudio as described in this thread, and upgraded to 10.04, did this cause problems regarding sound?  I don't want to do the upgrade and then find out after the fact that it undid all my efforts to get my sound working acceptably.

---

### Post by tommcd on 2010-04-30
> **sieve said:**
> For those who have removed Pulseaudio as described in this thread, and upgraded to 10.04, did this cause problems regarding sound?  I don't want to do the upgrade and then find out after the fact that it undid all my efforts to get my sound working acceptably.
I just did a clean install of Ubutnu 10.04. I then removed pulseaudio and  gstreamer0.10-pulseaudio using:
```
sudo apt-get remove pulseaudio gstreamer0.10-pulseaudio
```
APT then removed a bunch of other pulseaudio related packages. It also removed the ubuntu-desktop metapackage.
With some trepidation, I let APT do it's thing. I have since logged out and rebooted with no ill effects. Sound works fine with alsa; and the ubuntu desktop is intact with all my settings preserved.
Pulse Audio is less of a resource hog in 10.04 than it was in 9.10. However, it still was using more of my CPU (around 3-4% with one sound app running, and up to 12-14% with 2 sound apps running) than alsa, so I removed it! I have no need for pulse audio.

Hope this helps.

---

### Post by mgol on 2010-04-30
I did an upgrade and then invoke the following:
```

sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol 

sudo apt-get install gnome-alsamixer alsa-oss python-alsaaudio 

```

Now it works OK.

---

### Post by Rockin Robbins on 2010-05-05
> **tommcd said:**
> I just did a clean install of Ubutnu 10.04. I then removed pulseaudio and  gstreamer0.10-pulseaudio using:
```
sudo apt-get remove pulseaudio gstreamer0.10-pulseaudio
```
APT then removed a bunch of other pulseaudio related packages. It also removed the ubuntu-desktop metapackage.
With some trepidation, I let APT do it's thing. I have since logged out and rebooted with no ill effects. Sound works fine with alsa; and the ubuntu desktop is intact with all my settings preserved.
Pulse Audio is less of a resource hog in 10.04 than it was in 9.10. However, it still was using more of my CPU (around 3-4% with one sound app running, and up to 12-14% with 2 sound apps running) than alsa, so I removed it! I have no need for pulse audio.

Hope this helps.

Just did it. I was pretty desperate, with the flaky sound totally ruining my computing experience with Ubuntu 10.04. Had blamed it on my relatively ancient Turtle Beach Santa Cruz sound card, which is marvelous under Windows XP. I had already burned a Kubuntu install disk to start again from scratch when I tried your fix. Rock solid audio now. It's great!

---

### Post by tommcd on 2010-05-06
> **Rockin Robbins said:**
>  I had already burned a Kubuntu install disk to start again from scratch when I tried your fix. 
Kubuntu and now even Xubuntu also use pulse audio, so using Kubuntu would not be a solution. If you want a *buntu that does not use pulse audio, you would have to go to the new lighweight Lubuntu. There is also Crunchbang, but Crunchbang is still at version 9.04. Crunchbang 10 is currently at alpha stage.
Other distros, like Fedora and Mandriva also use pulse audio. 
> **Rockin Robbins said:**
> 
Rock solid audio now. It's great!
Glad to help. So was pulse audio a resource hog on your computer also? It is on mine. But at least it was less of a resource hog on 10.04 than it was on 9.10.
Some pulse audio tidbits:
[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it](http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it)
[http://www.tuxmachines.org/node/42129](http://www.tuxmachines.org/node/42129)
[http://www.unixlads.com/?p=179](http://www.unixlads.com/?p=179)
We are not the only users who are frustrated by this!

---

### Post by teet on 2010-05-06
I did the steps outlined in this post:  [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4) 
and everything is working like I want it now.  

My major issue with pulse audio is that I have a mythtv frontend running all the time as a seperate x-screen via a tv-out.  The frontend grabs all the audio and consequently I have no sound on my main x-screen.

I made a link to gnome-alsamixer and put it where the old volume mixer applet used to go.  I chose a medium-volume icon and now everything at least LOOKS like it should (although the icon doesn't change based on the volume level, but I can live with that).

Maybe all this pulse audio nonsense will be sorted out by 12.04 :)

-teet

---

### Post by Quake on 2010-05-06
But now, another problem arise... how to make the keyboard volume work because it seems pulseaudio is MUCH MORE integrated than 9.04. In Jaunty, I didn't have that problem.

---

### Post by teet on 2010-05-06
> **Quake said:**
> But now, another problem arise... how to make the keyboard volume work because it seems pulseaudio is MUCH MORE integrated than 9.04. In Jaunty, I didn't have that problem.

Can you just redefine the shortcut key in System --> preferences --> keyboard shortcuts?

-teet

---

### Post by feistybill on 2010-05-07
tommcd, mgol,

THANK YOU!

I followed your instructions and now that piece of junk called PulseAudio is not infesting my machine anymore :)

---

### Post by Quake on 2010-05-07
> **teet said:**
> Can you just redefine the shortcut key in System --> preferences --> keyboard shortcuts?

-teet
No, the shortcut is fine, but when you remove pulseaudio, it also removes the audio applet that takes command from the keyboard shortcut.

---

### Post by mgol on 2010-05-07
> **Quake said:**
> No, the shortcut is fine, but when you remove pulseaudio, it also removes the audio applet that takes command from the keyboard shortcut.

Try this:
[https://launchpad.net/~dtl131/+archive/ppa/](https://launchpad.net/~dtl131/+archive/ppa/)

---

### Post by Quake on 2010-05-07
Thank you very much for that link! I will try it when I get home

---

### Post by Quake on 2010-05-07
[mgol]("http://ubuntuforums.org/member.php?u=486086"), I THANK YOU!!!!!!!!!!!!!!!!!!!! I finally removed the Pulseaudio virus! It could hit up to 35% in CPU usage.

I think I should blog about this!

---

### Post by tyk on 2010-05-09
Thank you Hugo Alvarado

---

### Post by teamanx on 2010-05-14
Here is the full command sequence to get rid of pulse with Lucid, that worked for me, based on the posts above. Just copy and paste onto the terminal:

```

sudo cp /usr/share/alsa/alsa.conf /usr/share/alsa/alsa.conf.bak
sudo sed /usr/share/alsa/alsa.conf.bak -e 's/\"\/usr\/share\/alsa\/pulse.conf\"/#\"\/usr\/share\/alsa\/pulse.conf\"/g' > /usr/share/alsa/alsa.conf
sudo apt-add-repository ppa:dtl131/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install esound esound-clients esound-common libesd-alsa0 alsa-base alsa-tools alsa-utils alsa-oss linux-sound-base python-alsaaudio gnome-media libsdl1.2debian-alsa
sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol

```

Now reboot, log in, and add to the panel the "Volume Control" applet, by right-clicking on the panel and selecting "Add to the panel...". By clicking on the new applet and selecting "Volume Control", you can have access to all sound properties.

---

### Post by mgol on 2010-05-14
Why to install esound? ALSA is enough with its mixing capabilities, I guess.

I would also move the line:
```
sudo apt-add-repository ppa:dtl131/ppa

```
to the beginning. Otherwise some packages are installed twice - from standard repository and then upgraded, it's a waste of bandwidth.

---

### Post by tommcd on 2010-05-15
> **mgol said:**
> Why to install esound? ALSA is enough with its mixing capabilities, I guess.
I have never found it necessary to install any of the esound stuff either. I also have not installed any extra alsa stuff beyond what is included in a default Ubuntu 10.04 install.
 Just removing pulseaudio and gstreamer0.10-pulseaudio will disable pulse audio and take almost all of the pulseaudio related packages away too.
Just run **gstreamer-properties** in the terminal after removing pulseaudio and set everything to alsa. I can control all the sound levels just fine with alsamixer in the terminal. Some of those alsa packages (e.g., alsa-base and alsa-utils) are already part of a default Ubuntu 10.04 install.
Installing the extra alsa packages will not hurt anything though; and it does give some extra GUI control over sound properties.
> **mgol said:**
> 
I would also move the line:
```
sudo apt-add-repository ppa:dtl131/ppa

```
to the beginning. Otherwise some packages are installed twice - from standard repository and then upgraded, it's a waste of bandwidth.
I don't bother with that ppa repo either.

---

### Post by teamanx on 2010-05-15
> **mgol said:**
> Why to install esound? ALSA is enough with its mixing capabilities, I guess.


That's OK, as long as your sound card supports hardware mixing. If it doesn't, then you must set up ALSA to use DMix, which needs extra config, and has worst performance than esound. That's  my experience, but maybe I'm wrong and it is a better choice to stick with ALSA.

---

### Post by yadayada2 on 2010-05-16
Well, I have followed your instructions, but now I cannot open Sound Recorder. I attached the error message as a screenshot.

Edit: I have to add that there are no "Sound Preferences" in the Preferences menu anymore.

---

### Post by mgol on 2010-05-16
> **yadayada2 said:**
> Well, I have followed your instructions, but now I cannot open Sound Recorder. I attached the error message as a screenshot.

Edit: I have to add that there are no "Sound Preferences" in the Preferences menu anymore.

Did You add the dtl31 ppa repository, followed by update, upgrade and reboot?

---

### Post by yadayada2 on 2010-05-16
I did. But it didn't change anything. Now I have done all steps again and rebooted. And still the error message appears.

---

### Post by mgol on 2010-05-16
Go to System->Preferences->Sound and check if You have an audio device set.

---

### Post by yadayada2 on 2010-05-16
As you can see in the attached screenshot, there is no such option. :(

Edit: When I run the item "Default Sound Card" it seems nothing happens. When I run this link in a terminal, this will be the output> /usr/bin/asoundconf-gtk                                       < ~

(process:2537): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!


---

### Post by mgol on 2010-05-16
> **yadayada2 said:**
> As you can see in the attached screenshot, there is no such option. :(

It is probably hidden. Right click and choose "Edit menu" and then turn it on. If it's still not there, You can invoke it manually:
```
gnome-volume-control
```
Try also this:
```
gstreamer-properties
```

---

### Post by yadayada2 on 2010-05-16
Thanks, now I can open this dialog from the command line. However, the Sound Recorder still gives the same error message.

Then I have tried your second command, which will give me another windows, as to be seen in the next attached screenshot. ALSA is selected as default input plugin, and as device, there is a default option.

When I click on "Test", I get ALSA - Advanced Linux Sound Architecture: Could not open audio device for recording.

There are also two options, both labeled ALC1200 Analog. Selecting one and then testing, a new dialogue appears. "Testing pipeline". A small block runs from the left to the right and back again, but nothing more happens.

---

### Post by yadayada2 on 2010-05-16
Sorry, little update. Now I can open the Sound Recorder. I don't know, why this works now. Thanks anyway.

The only problem remaining is that the front mic still doesn't work. Seems that taking away pulseaudio didn't solve that problem.

---

### Post by mgol on 2010-05-16
Invoke
```
alsamixer
```
in the terminal and upload the screenshot.

---

### Post by yadayada2 on 2010-05-16
Somehow this still calls for pulse.

---

### Post by mgol on 2010-05-16
Check if You really removed these packages (sometimes some error may prevent it, leave conf. files etc.)...
```
sudo dpkg --purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol 
```

Do You have ~/.asoundrc file? If so, remove it.

You can also check what You have in /etc/:
```

find /etc/ -name "*alsa*" 2>/dev/null
find /etc/ -name "*pulse*" 2>/dev/null

```
and check if any of found *alsa* files doesn't invoke PulseAudio in any way.

I'm running out of ideas - didn't You change a lot of stuff before upgrade to 10.04? I'm convinced it should work just OK after performing steps supplied by teamanx on a clean 10.04 install...

---

### Post by yadayada2 on 2010-05-16
> sudo dpkg --purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol
dpkg: warning: ignoring request to remove libcanberra-pulse which isn't installed.
dpkg: warning: ignoring request to remove pulseaudio which isn't installed.
dpkg: warning: ignoring request to remove pulseaudio-esound-compat which isn't installed.
dpkg: warning: ignoring request to remove pulseaudio-module-bluetooth which isn't installed.
dpkg: warning: ignoring request to remove pulseaudio-module-gconf which isn't installed.
dpkg: warning: ignoring request to remove pulseaudi[QUOTE]o-module-udev which isn't installed.
dpkg: warning: ignoring request to remove pulseaudio-module-x11 which isn't installed.
dpkg: warning: ignoring request to remove gstreamer0.10-pulseaudio which isn't installed.
dpkg: warning: ignoring request to remove pulseaudio-utils which isn't installed.
dpkg: warning: ignoring request to remove pavucontrol which isn't installed.
[/QUOTE]

asoundrc is there, but it includes only the position of .asoundrc.asoundconf. This file reads like this:

> pcm.!default { type pulse }
ctl.!default { type pulse }


---

### Post by yadayada2 on 2010-05-16
> martin@acer > find /etc/ -name "*alsa*" 2>/dev/null                                                 < ~
/etc/apm/scripts.d/alsa
/etc/apm/resume.d/20alsa
/etc/apm/suspend.d/80alsa
/etc/default/alsa
/etc/init/alsa-mixer-save.conf
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/alsa-base.conf.dpkg-dist
/etc/init.d/alsa-mixer-save


and 

> martin@acer (1) > find /etc/ -name "*pulse*" 2>/dev/null                                            < ~
/etc/pulse


---

### Post by yadayada2 on 2010-05-16
> **mgol said:**
> 
and check if any of found *alsa* files doesn't invoke PulseAudio in any way.


What do you mean by this?

---

### Post by mgol on 2010-05-16
> **yadayada2 said:**
> asoundrc is there, but it includes only the position of .asoundrc.asoundconf. This file reads like this:

OK, it seems to be the source of the problem, they obviously refer to PA. Is this a file in Your home directory? Then delete both .asoundrc and .asoundrc.asoundconf (You can move them to the backup directory if You don't want to risk). After a reboot it should work.

---

### Post by yadayada2 on 2010-05-16
I am sorry to say, but it still doesn' work. For now I will call it a night and try again tomorrow. Thanks again for all your help.

---

### Post by mgol on 2010-05-16
I'm out of ideas. Thos .asoundrc files suggest non-standard configuration (by default those files are not created). I believe with default installation everything should work properly. Maybe try to remember what You edited in the past and look into those files - I believe You have pulse entries written there.

---

### Post by teamanx on 2010-05-17
Actually, there is no sound properties in the "System" menu. What you have to do is adding the volume control applet to the panel, right-click on it, and selecting "Open volume control". Here is the sound properties dialog. Now, try to change the switches and sliders, specially those in the "Recording" tab, and see if you can record from the microphone. Some cards have also a switch called "Mic record" on the "Switches" tab.

---

### Post by mgol on 2010-05-17
> **teamanx said:**
> Atry to change the switches and sliders, specially those in the "Recording" tab, and see if you can record from the microphone.
I doubt it'll help as he still has some PulseAudio junk in his OS...

---

### Post by yadayada2 on 2010-05-17
@teamanx: Unfortunately, it's not as simple as that... :(

---

### Post by yadayada2 on 2010-05-17
Do you have more hints how to narrow down what's causing the problem?

---

### Post by seeker5528 on 2010-05-17
> **yadayada2 said:**
> Well, I have followed your instructions, but now I cannot open Sound Recorder. I attached the error message as a screenshot.

Edit: I have to add that there are no "Sound Preferences" in the Preferences menu anymore.

If you don't find it in the menu, then you can always go to the command prompt and type 'gstreamer-properties'.

EDIT: saw this was answered already. Try uninstalling gstreamerXXX-pulseaudio package, currently showing in Synaptic as gstreamer0.10-pulseaudio on my system.

Later, Seeker

---

### Post by teamanx on 2010-05-19
I have added libsdl1.2debian-alsa for installing, so KDE apps (e.g. kdenlive) work with alsa.

---

### Post by lqdc on 2010-06-06
Thanks a lot to nullrend for the informative post on the first page.
I did everything according to this post:
[http://art.ubuntuforums.org/showpost.php?p=8284273&postcount=4](http://art.ubuntuforums.org/showpost.php?p=8284273&postcount=4)

Linux sounds now work (such as the boot sound), but with some cracking at the beginning of each sound.

However, when I play music or use any application that requires sound, the sound doesn't work - just cracks at the beginning.  
Are the applications trying to use pulseaudio? How would I go about solving that?

---

### Post by wasabishot on 2010-06-07
Hello
so this thread worked perfect for me on my Hp pavilion 9730us, working on Lucid 10.04.

But.....
today I got in the mail a 3D sound usb device i bought on eBay, because my internal sound card makes a distortioned sound when connected to an external amplifier, and I can't make it work with the alsa.

It appears in lsusb as
JMTek, LLC.

it also appears in alsamixer as one of the sound cards but still no sound out nor in.

Does anybody have any idea?

---

### Post by sieve on 2010-06-08
Not sure if this is the same issue, but you could try the procedure as described in post #24 of this thread:

[http://ubuntuforums.org/showthread.php?t=1313831](http://ubuntuforums.org/showthread.php?t=1313831)

---

### Post by wasabishot on 2010-06-08
thanks sieve... I already thanked you in the other thread... but just for ppl to know it works just great!!!

---

### Post by cliang on 2010-06-11
> **mgol said:**
> Try this:
[https://launchpad.net/~dtl131/+archive/ppa/](https://launchpad.net/~dtl131/+archive/ppa/)

I've removed pulseaudio and installed these packages but I'm having a problem where using the volume up/down shortcut keys causes the speaker popup to display but the volume doesn't change. It just shows the speakers as muted. I can control the volume just fine with the applet. Any clues why the key events aren't being handled properly?

---

### Post by mgol on 2010-06-11
> **cliang said:**
> Any clues why the key events aren't being handled properly?

Go to System -> Preferences -> Keyboard shortcuts and check if You have the proper keys assigned to Volume mute, down and up.

---

### Post by cliang on 2010-06-11
> **mgol said:**
> Go to System -> Preferences -> Keyboard shortcuts and check if You have the proper keys assigned to Volume mute, down and up.

The mute shortcut key works ok. The volume up and down keys don't do anything besides set the volume to the max and display the volume level with a bar that seems to break through the right side. :confused:

---

### Post by stoppage on 2010-07-11
Hi I have two questions on removing pulse-audio from Hardy 8.04.

Q1: I've heard there's a PPA Repo that re-installs „System-Preferences-Sound“ applet without Pulse. Has anybody any further information?

Q2: By purging Pulse do I lose „asoundconf-gtk“ (I need ability to select onboard sound or „SBLive“) sound card. Would appreciate any help here.

---

### Post by mgol on 2010-07-11
> **stoppage said:**
> Q1: I've heard there's a PPA Repo that re-installs „System-Preferences-Sound“ applet without Pulse. Has anybody any further information?

It was already mentioned many times...
```
sudo apt-add-repository ppa:dtl131/ppa
```

> **stoppage said:**
> Q2: By purging Pulse do I lose „asoundconf-gtk“ (I need ability to select onboard sound or „SBLive“) sound card. Would appreciate any help here.

I don't know:
```
$ asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!
```

However, I'm on 10.04. BTW, why don't You upgrade to 10.04? 8.04->10.04 path is supported and 10.04 is the newest LTS. 8.04 has only 9 months of life left.

---

### Post by tommcd on 2010-07-12
> **stoppage said:**
> Hi I have two questions on removing pulse-audio from Hardy 8.04.
Q2: By purging Pulse do I lose &#8222;asoundconf-gtk&#8220; (I need ability to select onboard sound or &#8222;SBLive&#8220;) sound card. Would appreciate any help here.
I can answer the second question: No, you will not loose asoundconf-gtk. The asoundconf-gtk package does not depend on pulseaudio. Pulseaudio is just a suggested package for asoundconf-gtk:
[http://packages.ubuntu.com/hardy/asoundconf-gtk](http://packages.ubuntu.com/hardy/asoundconf-gtk)
It is the same on Lucid 10.04 btw.
You can confirm this on your own system by running:
```
aptitude show asoundconf-gtk
```
It should not list pulseaudio as a dependency.

In the event that you ever want pulseaudio back just reinstall it:
```
sudo apt-get install pulseaudio
```
And then the pulseaudio beast will be back on your system!

---

### Post by Mattevt on 2010-07-24
> **teamanx said:**
> Here is the full command sequence to get rid of pulse with Lucid, that worked for me, based on the posts above. Just copy and paste onto the terminal:

```

sudo cp /usr/share/alsa/alsa.conf /usr/share/alsa/alsa.conf.bak
sudo sed /usr/share/alsa/alsa.conf.bak -e 's/\"\/usr\/share\/alsa\/pulse.conf\"/#\"\/usr\/share\/alsa\/pulse.conf\"/g' > /usr/share/alsa/alsa.conf
sudo apt-add-repository ppa:dtl131/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install esound esound-clients esound-common libesd-alsa0 alsa-base alsa-tools alsa-utils alsa-oss linux-sound-base python-alsaaudio gnome-media libsdl1.2debian-alsa
sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol

```

Now reboot, log in, and add to the panel the "Volume Control" applet, by right-clicking on the panel and selecting "Add to the panel...". By clicking on the new applet and selecting "Volume Control", you can have access to all sound properties.

THANK YOU! A Million times! I was messing around with my Steelseries Siberia usb soundcard. I don't even know what I did but suddenly I had zero sound, everything was so wacky I can't even explain it. I completely removed PA, installed Alsa then I followed these instructions up to (but not including, no offense) the esound stuff, and everything is just golden. Thanks again, you have no idea.

---

### Post by ZBlue on 2010-07-24
Need help with this after removing pulseaudio : 

[HTML]http://art.ubuntuforums.org/showthread.php?t=1537824[/HTML]

---

### Post by adkmom on 2010-07-25
Hi all~

Not meaning to hijack- but this thread makes me believe part of my issue is PA. I'm running Mint 9/64. Logitech x-530 5.1 speakers, Realtek 889 sound.

There's just sooooo much bass coming from my sub that you can't listen to music. I've tried any equalizers in all music players installed (M, RhyBx, MovieP, VLC)- all the same. I've adjusted Pulse bass settings via slide bar- but it does nothing. I opened alsa mixer to make sure the correct sound was chosen- it was. I have XP running in Virtualbox- it has the same issue (though the speakers function properly in Windows). I'm d/l'ing PCLinuxOS right now to see if the issue exists in their livecd.

Is this a matter of program control mis-management? Are two programs trying to control sound? As a very n00b Linux user, I am hesitant to bork what I have so far. I've managed to d/l & install/tweak a lot of stuff- but the sound has me baffled, and I use my PC as my stereo, so it hurts!

Lastly- is there supposed to be a start-up sound in Mint? If so, I've never heard it...

T

---

### Post by tommcd on 2010-07-29
Here is a good article on controlling pulseaudio. It shows you how to control pulseaudio so you can turn it on or off when you want, without removing it:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)
I have not tried this, since I have already removed pulseaudio, and I do not want it back. It looks like an effective option instead of removing pulseaudio in case anyone wants to try it.

---

### Post by dentaquet on 2010-09-14
HELP!!
 
hi everyone! im on ubuntu 10.04, and i removed pulseaudio yesterday because i tought it was the reason why i had no sound in jack...and it also removed ubuntu-desktop! now i cant log on anymore...can i get it back from a console at startup? if so, how do i proceed?! 
 
im panicking!

---

### Post by mgol on 2010-09-14
ubuntu-desktop is a meta-package, so removing it shouldn't screw anything up. However, You can always reinstall it in one of terminals:
```
sudo apt-get install ubuntu-desktop
```
I assume You can log in the text console? (You can get there by pressing Ctrl+Alt+Fx, where x is between 1 and 6).

---

### Post by brooklynzoo81 on 2010-09-14
Hello all.  I hope i am posting in the right area.  I had to completely remove Pulseaudio due to a hissing and static sound while playing any audio.  Once i did that my sound icon on the upper right is gone.  How would i go about getting this back?  When i go to preferences and sound i get a pop up windows saying "Waiting for sound system to respond"  also when i go to sound&video and click on gnome ALSA mixer, i get a error stating that some of your configurations will not work. I am running 10.04 64bit.  

This week is the most i have used linux ever! so i am still a newbie in training with all of this.  Too much Windows brain washing for me.

---

### Post by riverfr0zen on 2010-09-14
@brooklynzoo81, after removing pulseaudio did you install the alsa packages? 

This post in this same thread should help you out if you haven't:
[http://ubuntuforums.org/showthread.php?t=1313253&page=14#134](http://ubuntuforums.org/showthread.php?t=1313253&page=14#134)

Otherwise, the following troubleshooting guide may also help:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by brooklynzoo81 on 2010-09-14
> **riverfr0zen said:**
> @brooklynzoo81, after removing pulseaudio did you install the alsa packages? 

This post in this same thread should help you out if you haven't:
[http://ubuntuforums.org/showthread.php?t=1313253&page=14#134](http://ubuntuforums.org/showthread.php?t=1313253&page=14#134)

Otherwise, the following troubleshooting guide may also help:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Thanks for the reply back.  I am not sure if i did.  I remember typing in ALSA in the update manager and installing some stuff i saw from there but not sure if that was the right thing or not.  What packages exactly are you referring to and or how can i found out? thanks.

---

### Post by riverfr0zen on 2010-09-14
They're listed in the comment at that first link I gave you:

```
sudo apt-get install gnome-alsamixer alsa-oss python-alsaaudio
```

---

### Post by victorkruger on 2010-09-23
Thank you all for this information to remove pulseaudio from the computer and just use alsa for sound.  The problem that i had was that pulseaudio kept insisting to unmute my mic everytime i rebooted or woke up my laptop.  

Now I have another issue, since i've removed pulse audio, my laptop does not remember or check to see if my headphones are plugged into my laptop and direct the audio to the speakers when i unmute my system or reboot my computer with the headphones plugged in.   Does anyone have any suggestions on how to correct this?


Edit

I should probably put in some hardware info
Lenovo 3000 N200 running ubuntu 10.04

Edit2
I seem to have band-aided the issue for now.

I updated alsa drivers from this post:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

but that still didn't fix my issue.

I added the following to my /etc/modprobe.d/alsa-base.conf

```

options snd-hda-intel model=lenovo
options snd-hda-intel position_fix=1 enable=yes

```
rebooted, but my issue was still there.

I finally went into alsamixer and muted the front speakers and finally it worked.  I can now mute then unmute and the front speakers don't play any sounds.  I can unplug my headphones and the front speakers then play sound.  I also rebooted to make sure the settings stayed the way they were and they did.

---

### Post by Bucky Ball on 2010-10-11
This fix is exactly what I am looking for. One problem: Anyone know how I'd remove Pulse and add ALSA in 8.04 LTS this easily rather than 10.04? I am having a nightmare:

[http://ubuntuforums.org/showthread.php?p=9956634#post9956634](http://ubuntuforums.org/showthread.php?p=9956634#post9956634)
[http://ubuntuforums.org/showthread.php?t=1592896](http://ubuntuforums.org/showthread.php?t=1592896)

---

### Post by grahams on 2010-10-11
Has anyone successfully removed Pulse from 10.10? 

I've used this guide on 9.10 and 10.04 perfectly, but I noticed that libesd-alsa0 is not available is not available on 10.10. Is this needed on 10.10 for PulseFree audio.

---

### Post by tommcd on 2010-10-12
> **grahams said:**
> Has anyone successfully removed Pulse from 10.10? 

The only thing you really need to do to remove pulseaudio is to remove *pulseaudio* and *gstreamer0.10-pulseaudio*. This will disable pulseaudio. All the other stuff in the guide on post #4 of this thread is optional.

---

### Post by nh7o_hi on 2010-10-13
After I removed pulse from my 10.04, I needed to restore the volume/mute keys. I found a small app called "volti" which does the trick.

[http://code.google.com/p/volti/](http://code.google.com/p/volti/)

However, it needs to be reloaded after a suspend/resume cycle. Probably because the intel-hda module gets removed and reloaded on resume. Otherwise a good solution.

---

### Post by grahams on 2010-10-14
I can confirm that it is safe to remove pulse in 10.10 and you just need to remove pulseaudio and gstreamer0.10-pulseaudio. Thanks Tommcd

For volume control and multimedia these steps works on 10.10 (and 9.10, 10.04)

[http://forums.slimdevices.com/showthread.php?t=70556&page=2](http://forums.slimdevices.com/showthread.php?t=70556&page=2)



Btw. I tired volti, it looks nicer and simpler to install, but the multimedia keys didn't work and it has to be reloaded on reboot or resume.

---

### Post by tommcd on 2010-10-14
> **nh7o_hi said:**
> After I removed pulse from my 10.04, I needed to restore the volume/mute keys. I found a small app called "volti" which does the trick.

You can always just use **alsamixer** in the terminal. It works just as well as anything else. That is what I use.
If you want a GUI app you can install **alsamixergui** or **gnome-alsamixer**.

---

### Post by nh7o_hi on 2010-10-17
> **tommcd said:**
> You can always just use **alsamixer** in the terminal. It works just as well as anything else. That is what I use.
If you want a GUI app you can install **alsamixergui** or **gnome-alsamixer**.

Yes, but Volti also enables the volume up-down-mute keys on this laptop, with the on-screen display. I use those constantly.

---

### Post by Harrychillboy on 2010-10-18
> **nullrend said:**
> The above procedure works. I'll just repeat it for extra points, marked up properly.

Here is what I did to remove pulse audio in Karmic:

```
$ sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
``````
$ sudo apt-get autoremove
``````
$ sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
``````
$ sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
```restart your computer!

Notes:
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)[INDENT]This means:
```
$ gstreamer-properties
```[/INDENT]-remove gstreamer0.10-pulseaudio to get sound in totem.[INDENT]The above commands should have taken care of that, but it never hurts to be sure when talking about the hydra that is PulseAudio.
[/INDENT]-gnome-alsamixer is for changing the volume, not an applet but better that nothing[INDENT]This means you are left without a panel applet to control volume across the board, thanks to the thoughtful efforts of Canonical to shove PulseAudio down our throats. So you need to have something to control audio with:
```
$ sudo apt-get install gnome-alsamixer
```And something to keep gnome-alsamixer within easy reach, provided by AllTray:
```
$ sudo apt-get install alltray
```[/INDENT]Now, one last word of advice. Usually the best solution is to use aptitude or synaptic to do these moves, but you'll run headfirst into their dependency resolution efforts, which command them to put PulseAudio back in your system when reinstalling gnome-alsamixer. So either you use apt-get or you reconfigure aptitude/synaptic dependency resolution to work the way you want.

Thanks a lot nullrend!! 
It worked and finally I could trash pulseaudio, it never worked well and consumed to much cpu too.

---

### Post by tommcd on 2010-10-18
> **Harrychillboy said:**
>  
 pulseaudio ...  consumed to much cpu too.
This is the main problem with pulseaudio imo. Surely, the Ubuntu devs must be aware that pulseaudio is a *huge* resource hog. Does anyone know if the Ubuntu devs are planning to do anything at all about this? I realize that pulseaudio is an upstream package that the Ubuntu devs are not responsible for; but gee whiz, is anyone addressing this at all???

Perhaps pulseaudio could be offered as an option when you install Ubuntu. Or perhaps there could be a simple GUI app for turning pulseaudio on and off.

Here is an informative article that shows you how to turn pulseaudio on or off at will as an alternative to removing it (I posted a link to this previously in this thread):
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)

---

### Post by loxaheart on 2010-11-21
Thank you soo much!! I was having the worst time with Pulse =( It actually got to the point where if I opened my browser, my mic would fail.

So, once again, thank you!

Signed,
<3 Grateful <3

---

### Post by riverfr0zen on 2010-11-29
I would not mind Pulseaudio if Ubuntu engineers were able to deliver the package without completely disrupting my computer's entire sound system, including the direct connection to the soundcard and/or PS3. 

There are a lot of benefits to enabling the package--simultaneous visualizations of applications that are using up all of the sound system resources, graphic identification of audio cards and even *porno*graphic audio-channel capabilities.

I'm not saying I'm ungrateful to the people at Canonical -- you guys do a great job, it's just I wish you would do a *better job* with pulseaudio.

---

### Post by snuffy47 on 2011-01-21
I removed pulse audio and it appears to have fixed some of my sound issues.

But now when I try to run alsamixer I get

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

cannot open mixer: Connection refused

Any help?

---

### Post by mgol on 2011-01-21
> **snuffy47 said:**
> But now when I try to run alsamixer I get

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

This is very little information. Did you try to google it? If so, what steps did you perform, what did you check?

It's a bit impolite of you to ask for help without even trying to find the answer by yourself. For example, first link obtained by googling your error message is:
[http://forums.debian.net/viewtopic.php?f=6&t=45884](http://forums.debian.net/viewtopic.php?f=6&t=45884)
Did you check that?

Show some initiative! After all, we are not paid for trying to help here.

---

### Post by snuffy47 on 2011-01-21
Funny you posted that post

I did try that post and there really is not that much on google regarding that error.

Not sure that I am being needy here I have been struggling with my audio on my htpc since installing 10.04.

I am not a linux expert and appreciate any help I ever recieve from this site.

I didnt figure I would be the only one to see this error

One more note I have spent most of the day tring to get this stuff to work.

---

### Post by mgol on 2011-01-21
> **snuffy47 said:**
> I did try that post and there really is not that much on google regarding that error.

[http://tinyurl.com/alsapulse](http://tinyurl.com/alsapulse)

> **snuffy47 said:**
> I am not a linux expert and appreciate any help I ever recieve from this site.

You don't have to be. It would just be nice if you google about this problem first and wrote here what you tried, then we would could actually exclude some possible problems. Your error is too generic.

BTW: you still didn't answer my question: what exactly did you try to do to fix this problem (like, did you try this link I provided? If it didn't help, why? Was the file they're talking about missing or was there any other problem connected to this proposed solution?)

Nobody here is a magician, we need some feedback from you to help you!

---

### Post by tommcd on 2011-01-22
> **snuffy47 said:**
> I removed pulse audio and it appears to have fixed some of my sound issues.
How did you remove pulseaudio?
Make sure you that *pulseaudio* and *gstreamer0.10-pulseaudio* are uninstalled.
> **snuffy47 said:**
> 
But now when I try to run alsamixer I get
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused
cannot open mixer: Connection refused

Be sure to run *gstreamer-properties* from the terminal and set everything to alsa. Also be sure you have the *alsa-utils* package installed.
As per the link that Mgol provided, try renaming *~/.asoundrc* (if you have this file) to *~/.asoundrc.bak*. Then reboot and see if you can run alsamixer.
Please write back with *what you have tried* to fix this.

---

### Post by snuffy47 on 2011-01-22
I was following post #4 in this thread.

I actually removed that file already following one of the google posts that I was also using.

I did save a copy and will put it back with the different name but not sure that makes sense to me :(

Going to go through post #4 again.

How would I ensure that gstream and all of pulseaudio is removed?

@mgol I tried the dkg line in terminal and the file was present I removed it.  The difference with my problem was I did not see the first error.

As for google the 4 search finds after the debian first one have no information that seem use full.

[http://pastebin.com/SeqVajvC](http://pastebin.com/SeqVajvC) I tried to start from the begining but damn error is still there.  plus a small melt down when I lost my desktop lol

Finished the other post also again

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

cannot open mixer: Connection refused

[http://forums.debian.net/viewtopic.php?f=6&t=45884](http://forums.debian.net/viewtopic.php?f=6&t=45884)

sudo dpkg-reconfigure alsa-utils

no work still error

sudo apt-get install libasound2-plugins (already installed)

No fix :(

~/.asoundrc renamed to asoundrc.bak using gksudo nautilus

That file did reappear after all the terminal work.

Same error :(

---

### Post by tommcd on 2011-01-23
> **snuffy47 said:**
> I was following post #4 in this thread.
As per your pastebin link:
You really did not need to go through all of that. All I have ever done to remove pulseaudio was to remove **pulseaudio** and **gstreamer0.10-pulseaudio**. Then I run **gstreamer-properties** and set everything to alsa. However, everything worked fine for me before I ever even bothered to run gstreamer-properties.
Make sure **alsa-base** and **alsa-utils** and **gstreamer0.10-alsa** are installed. On my Xubuntu install these are the only alsa packages I have installed. (I also have **libsdl1.2debian-alsa**; but I don't think you even need that).
> **snuffy47 said:**
> 
How would I ensure that gstream and all of pulseaudio is removed?
You could look in Synaptic Package Manager, or (what I do), install **aptitude** and run from the terminal:
```
aptitude search pulseaudio
``` A "p" before a package means the package is purged (i.e., not installed). A "i" before a package means it is installed.
Just install aptitude and post the output of:```
aptitude search pulseaudio
``` and ```
aptitude search alsa
```
(Use code tags to post these outputs please. This is the # icon at the top of the post window).
 This will tell us exactly what you have and don't have.
> **snuffy47 said:**
> 
~/.asoundrc renamed to asoundrc.bak using gksudo nautilus
There is no need to use gksudo with configuration files in your home directory. These files are owned by you and can thus be edited or removed from your regular user account without using sudo.

---

### Post by kovo1533 on 2011-01-29
Hey guys it looks like I have a final solution for this problem. My both ubuntu computers are working without this **** called pulseaudio also icon in notification area works and volume bar too.
Also my friend help me resolve volume keys problem. SO :
My ubuntu is 9.10 on big computer and 10.04 on notebook.

**Zoot7** wrote a great article in this formum how to recompile panel applets to include volume applet, just one o two improvements, so step by step:

**At first say goodbye to pulseaudio:**
```
sudo apt-get purge pulseaudio
```
... now reboot the computer to let changes take effect and after reboot we can continue with game.

... ALSA should take control over the soundsystem after this reboot, my experiences are that sound works (also sound from multiple sources at one time) you do not need to install anything and can continue to next steps ... if no, lot of posts are i this thread describing how to get sound working using ALSA, after that you can come back and continue  

**Open console:**

**satisfi depencies:**
```
sudo apt-get install devscripts build-essential fakeroot
```
```
sudo apt-get build-dep gnome-applets
```

**CD to your home directory:**
```
cd ~
```

**Make directory** called for example "build":
```
mkdir build
```

**CD to this directory:**
```
cd build
```

**get source code**
```
apt-get source gnome-applets
```

Then you're going to have to **specify the configure options** to enable the mixer applet. To do that:
```
gedit debian/rules
```
... Look for the line that starts with 
```
DEB_CONFIGURE_EXTRA_FLAGS +=
```
(in my case there were two lines with this, but I edited only the first and it was enough) and add another option to this line: 
```
--enable-mixer-applet
```

**OK** now trick from me... When you klick sound icon in tray (!! I mean notification area NOT indicator applet, maybe icon will appear in indicator applet too but I haven't tried it ...) the widnow with volume bar will appear. Also there is button called **"Volume control"** and here is the point of joke.
By clicking this button your system want to open "gnome-volume-control" ("system >> preferences >> sound" for better imagine) which is **not working** because you purged pulseaudio. 
But it is possible to **resolve this by editing this source file:**
```
gedit mixer/applet.c
```
search for:
```
gnome-volume-control
```
(it is only expression in file like this, in my case line number 707) and rewrite it to any command you like, I used:
```
gnome-alsamixer
``` 
which is program - mixer from repos and can be installed by:
```
sudo apt-get install gnome-alsamixer
```
... now save and close and follow to next steps ...

now we are going to **build .deb packages**
first install this (i get error first time, something about gstreamer inproper version i dont remember)
```
sudo apt-get install libgstreamer-plugins-base0.10-dev

```
**now build debs**
```
dpkg-buildpackage -b -j4 -D
```
compiling takes me about 10 minutes, after that finish **CD one directory up**
```
cd ..
```

leave console (terminal) opened and just for sure open file browser (nautilus) in your build directory and **check if there are three .deb packases named gnome-applets-"something"**, but no reason why shouldnt ... so continue ... 

Now we can go for beer, we are close to finish ...**instal this debs by**
```
sudo dpkg -i *.deb
```

...restart GDM after this (logout/login will be enough to do it)

...now FINALLY right click on panel >> add to panel >> you should see volume control somewhere ... that's it 

... oops I forgot ... It's good to not allow update-manager or something another to overwrite this packages so go to system >> administration >> synaptic and search for this packages:

[B]gnome-applets
gnome-applets-data
gnome-applets-dbg [/B] 

... and lock them (mark package, from upper menu: package >> lock version, apply for all three packages)

[IMG]http://kovo.webovka.eu/linux/alsa-vol-control/3.png[/IMG]

[IMG]http://kovo.webovka.eu/linux/alsa-vol-control/1.png[/IMG]

[IMG]http://kovo.webovka.eu/linux/alsa-vol-control/2.png[/IMG]

**In next post I want to explain using multimedia keys / function keys and notifications**

---

