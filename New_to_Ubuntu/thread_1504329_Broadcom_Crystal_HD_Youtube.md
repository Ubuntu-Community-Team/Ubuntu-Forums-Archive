---
title: "Broadcom Crystal HD Youtube"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by DarkEternity on 2010-06-07
Hi, I just recently purchased an asus 1005pr with the Broadcom Crystal HD card and installed ubuntu netbook remix 10.04.  I installed the driver via the broadcom site, but I can't seem to get a good 720p youtube stream.  I have also installed adobe flash 10 beta.  Has anyone had any success getting a good hd stream?

Thanks!

---

### Post by Directive 4 on 2010-06-07
if you have firefox you could try

[I][https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) 
 
maybe this will fix it
 [/I]

---

### Post by joshruehlig on 2010-06-08
I don't think flash in linux supports crystal decoding. Yeah I basicly use the broadcom crystal for movies in xbmc in linux(ask me if you need help compiling), movies in media player classic in windows, and flash in windows (need at least 10.1 beta3).

XBMC- linux: plays 1080p for .mkv's really well, but cant do well with mp4's, or some mkv's(a bluray avator file)

Flash - windows: plays 720p pritty well, I only have a GMA 950 so it still struggles a little.

Media Player Classic - windows : 1080p really well for most files (.mkv, mp4) but again had trouble with avatar bluray file

---

### Post by robbiebravo on 2010-07-03
Hi, I have a broadcom crystal hd card on a intel d510mo board with ubuntu 10.04 installed and xbmc. I could use some help with the compilation. I have the linux drivers downloaded, the other forums state such complicated ways. I could use some help... it would be very much appreciated.

thanks.

---

### Post by joshruehlig on 2010-07-03
sorry but you have to delete xbmc as well ur driver... Start fresh. Then check out the xbmc.org forum and search for compiling crystalhd on karmic. I'll post a link later ( I'm on my phone). Page 3 has instructions from waterhead, make sure to use the updated instructions.

I take no credit for this work, I just read alot of that forum.

```
sudo apt-get install linux-source subversion linux-headers-`uname -r` build-essential tofrodos autoconf git-core
svn checkout http://crystalhd-for-osx.googlecode.com/svn/tags/crystalhd-for-osx-1.0.3 crystalhd-for-osx-1.0.3
cd crystalhd-for-osx-1.0.3/crystalhd/driver/linux
autoconf                    #may not be necessary
./configure
make
sudo make install
sudo modprobe crystalhd
cd ~/crystalhd-for-osx-1.0.3/crystalhd/linux_lib/libcrystalhd
make
sudo make install
_______________________________________________________

#Add to /etc/apt/sources.list            #may not be necessary
    deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main

sudo add-apt-repository ppa:team-xbmc/ppa    #may not be necessary
sudo apt-get update
sudo apt-get install libasound2-dev
sudo apt-get build-dep xbmc             #may not be necessary

sudo aptitude install subversion make g++ gcc gawk pmount libtool nasm automake cmake gperf unzip bison libsdl-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev libfribidi-dev liblzo2-dev libfreetype6-dev libsqlite3-dev libogg-dev libasound-dev python-sqlite libglew-dev libcurl3 libcurl4-openssl-dev x11proto-xinerama-dev libxinerama-dev libxrandr-dev libxrender-dev libmad0-dev libogg-dev libvorbisenc2 libsmbclient-dev libmysqlclient-dev libpcre3-dev libdbus-1-dev libhal-dev libhal-storage-dev libjasper-dev libfontconfig-dev libbz2-dev libboost-dev libfaac-dev libenca-dev libxt-dev libxtst-dev libxmu-dev libpng-dev libjpeg-dev libpulse-dev mesa-utils libcdio-dev libsamplerate-dev libmms-dev libmpeg3-dev libfaad-dev libflac-dev libiso9660-dev libass-dev libssl-dev fp-compiler gdc libwavpack-dev libmpeg2-4-dev libmicrohttpd-dev libmodplug-dev libssh-dev gettext cvs

cd ~
svn co https://xbmc.svn.sourceforge.net/svnroot/xbmc/trunk/ XBMC
cd XBMC
./bootstrap
./configure
make clean
make -j2              
sudo make install
```

---

### Post by robbiebravo on 2010-07-04
thanks for the post. It was very clear. i was able to follow/execute everything in the code without errors. i rebooted, started xbmc. when i press ' o ' mkv/mov files still show h-264 and ff-h264 where i've read othter people see somethingh like crystal-hd. also in system, video, playback menu i don't have the choice of crystal hd as a render method. in movieplayback CPU is at 50-90% and dropping frames. how can i check if it's properly installed now?
Thanks so much for your effort already.

---

### Post by joshruehlig on 2010-07-04
> **robbiebravo said:**
> thanks for the post. It was very clear. i was able to follow/execute everything in the code without errors. i rebooted, started xbmc. when i press ' o ' mkv/mov files still show h-264 and ff-h264 where i've read othter people see somethingh like crystal-hd. also in system, video, playback menu i don't have the choice of crystal hd as a render method. in movieplayback CPU is at 50-90% and dropping frames. how can i check if it's properly installed now?
Thanks so much for your effort already.

Did you get rid of your old xbmc install first? make sure your xbmc is the just built revision. Check synaptics under xbmc for the rev. number. 
Also the key check is in the ./configure step, at the end it outputs a few thing including if it found broadcom crystal support. [B]rerun that step and check your output, 
run lsmod and search if crystalhd is there.[/B]

also run lspci and just put what your computer sees as the crystal

---

### Post by robbiebravo on 2010-07-05
hey there,

succes! at least partly. my lsmod gives: crystalhd in the list, but used by 0. Crystalhd now even shows up in the system>administration>hardware drivers. When trying to see the version of xbmc, nothing shows up in synaptic, so no version installed yet it works when i start xbnc up. it also doesn't show up in dpkg --list. Before I tried the above mentioned code I installed a nightly build. I might not have removed that properly. how to get rid of that now, so i can try again? I have tried: sudo apt-get remove xbmc* and it tells me "package xbmc is not installed, so not removed"

---

### Post by joshruehlig on 2010-07-05
> **robbiebravo said:**
> hey there,

succes! at least partly. my lsmod gives: crystalhd in the list, but used by 0. Crystalhd now even shows up in the system>administration>hardware drivers. When trying to see the version of xbmc, nothing shows up in synaptic, so no version installed yet it works when i start xbnc up. it also doesn't show up in dpkg --list. Before I tried the above mentioned code I installed a nightly build. I might not have removed that properly. how to get rid of that now, so i can try again? I have tried: sudo apt-get remove xbmc* and it tells me "package xbmc is not installed, so not removed"

My also says 0 but i think because it doesnt load until called, not sure on that but nothing to worry about.

you are using a build that didnt compile with xbmc support. Not sure how to remove it but if you can run it with "xbmc" then you should be able to remove it with "sudo apt-get remove xbmc". The svn site has revision 31632, I bet if you went into xbmc and checked the build number(I forgot where it is, google) it will be different. MAKE SURE YOU COMPLETELY REMOVE THIS.

There is a better command to remove packages completely (once again google). Then look through your sources (I use ubuntu tweak as it is easier) and delete any XBMC sources, except for the ones I talked about earlier.

And please run
     cd ~/XBMC
     ./configure

and check what it say in the last 50 lines, it will say if it has crystalhd support, if yes then you want to continue to build xbmc AFTER YOU HAVE COMPLETELY REMOVED ANY OTHER XBMC INSTALLS/SOURCES.

You should not have anything happen when you run xbmc, (until you do all of the earlier commands of course.)

---

### Post by robbiebravo on 2010-07-05
It works! I made a clean install of lucid, followed the code you posted to the letter and it works like a charm. in xbmc crystalhd shows up under system>video>playback where it allows to toggle hardware accelleration. indeed when i press 'o ' now during movie playback it says chd-264 with cpu utilization well under 20%.

Thanks so much for your effort. It's nice to know that experienced users like you will help out newbies like me. Thanks!

---

### Post by joshruehlig on 2010-07-06
Lol welcome my experience is reading walkthroughs, googling and trial and error. Haha ur not the first to do a full reinstall of ubuntu to get xbmc working right.

Hopefully they update the crystal libraries/drivers because xbmc in ubuntu still cannot play .mp4 well... while they play great in windows

---

### Post by michaelhenryvogel on 2010-08-04
I was browsing about the same question.  Is there any update on youtube viewing on behalf of either Adobe or Broadcom?  Earlier in the thread someone wrote that crystal decoding is not supported in flash on linux.  Is this still the case?

---

### Post by joshruehlig on 2010-08-04
> **michaelhenryvogel said:**
> I was browsing about the same question.  Is there any update on youtube viewing on behalf of either Adobe or Broadcom?  Earlier in the thread someone wrote that crystal decoding is not supported in flash on linux.  Is this still the case?

As far as I know hardware acceleration of flash 10.1 is only available on Windows. This includes nvidia or broadcom crystal acceleration. This kind of sucks for linux user... hopefully adobe updates flash on linux sometime in the future.

I do know they are working on flash acceleration on android tablets which use tegra 2 processors (nvidia gpu's), but I don't think that will mean anything for desktop linux and especially broadcom crystal acceleration.

____

BTW if you plan on playing flash videos on a netbook I have had better performance playing them on linux under mplayer then "crystal accelerated flash" under windows 7.

With the right settings I can play 720p flash of any site flawlessly on a n270 netbook (the older atom cpu available for most netbooks).

All I do is set my cpu to performance mode, and run the flash file in mplayer (which I wrote a config file for). It runs flawlessly and much better then under windows. I actually wrote a script to do this so it does it by drawing on my screen (using easystroke). You could also easily but a button on your panel.

Tell me if you want to go this route as I can help you.

---

### Post by princedwi on 2010-08-05
> **joshruehlig said:**
> 
BTW if you plan on playing flash videos on a netbook I have had better performance playing them on linux under mplayer then "crystal accelerated flash" under windows 7.

With the right settings I can play 720p flash of any site flawlessly on a n270 netbook (the older atom cpu available for most netbooks).

All I do is set my cpu to performance mode, and run the flash file in mplayer (which I wrote a config file for). It runs flawlessly and much better then under windows. I actually wrote a script to do this so it does it by drawing on my screen (using easystroke). You could also easily but a button on your panel.

Tell me if you want to go this route as I can help you.

I'm particularly interested in this method, solely because I'm fed up of the fact that youtube playback in general is very poor..I get dropped frames et al even on Win7 with the broadcom drivers. As with the OP, I own the 1005PR.

---

### Post by joshruehlig on 2010-08-06
> **princedwi said:**
> I'm particularly interested in this method, solely because I'm fed up of the fact that youtube playback in general is very poor..I get dropped frames et al even on Win7 with the broadcom drivers. As with the OP, I own the 1005PR.


Here's my complete observations for running flash better in ubuntu on a netbook.

I use a Dell mini 9 with atom n270, gma 950 and broadcom crystal 70012. You have stightly better specs in all aspects with atom n450, gma 3150 and broadcom crystal 70015.

First of all I dont know any media players that have hardware decoding for flash files with the gma 3150 or broadcom crystal 70015. (I havent researched this much)

Here are the ways I view hd youtube / other flash sites. 

**1** minitube (a great interface that allows 360, 720 and 1080p youtube) this doesnt work great for 720 for me but with your better processor on performance mode this may work for 720p.

**2** through mplayer

NOTE
This method has you run a flash player in youtube or most any other site, pause it so a file is in your /tmp folder named Flash(something). You then run a command, either in a terminal/ using easystrokes/ by putting a button on your panel/ or double clicking on a file/ or ect...
(it is fairly simple and can run the file in a window or fullscreen with only two steps(pausing->running command).

* This doesnt apply to you but I overclock my GMA950 from 250(which I have it on startup) to 400. I dont think yours can be overclocked yet [http://www.gmabooster.com/download.htm](http://www.gmabooster.com/download.htm)
I noticed this makes no noticeable difference when playing flash files.

*Next you want to make sure your cpu isnt constantly going into a low power cpu mode so you want to get into performance mode.

#echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

eeepc's have Super Hybrid Engine (SHE), I don't know much about this but it may not be enabled on ubuntu 10.04. It allows overclocking of eeepc's. I'll research this...

*Now you want to use mplayer
#sudo apt-get install mplayer w32codecs

Now you want to play the file in mplayer with
#mplayer /tmp/Flash*
(this is probably enough to work but lets make a config file to make this run flawlessly)
#cd .mplayer
#gedit config
Now paste this in the file and save
_________________
vo="xv"	
fs=1    #Full Screen
framedrop="1"	
vfm="ffmpeg"
lavdopts=threads=2:fast=1:skiploopfilter=all:lowres=1
autosync=30
v=1
#cache=65535 #This may not help, its commented out right now
_________________

Note - If you don't always want to run in fullscreen just delete the fs=1 line. If you do want to run fullscreen after deleting that run
#mplayer -fs /tmp/Flash*

PUTTING IT ALL TOGETHER
1. download/make config  for mplayer
2. make a file with this in it
-----
sudo echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
sudo echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
mplayer /tmp/Flash*
sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
sudo echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
-----
make sure to right click the file and make it executeable
3. now just surf/pause/run file either by a command/panel button ect... (You need to run it as root so the command would start with sudo)

**3** gnome-media-player
This is similar to mplayer method but it allows you to play files with the vlc, xine or gstreamer backend. You need to download gnome-media-player and someother stuff(vlc xin gstreamer backends). Mplayer has better performance but sometimes some site's flash crash in mplayer, so this may be needed. You can switch the backend and you get a playlist.

Tell me if you get confused anywhere.

---

### Post by gornokot on 2011-01-12
At Adobe's site, found this recent post: [http://forums.adobe.com/thread/773227](http://forums.adobe.com/thread/773227)
> 
Hi, I'm a linux user.

Now, i'm using version 10,2,151,49 of Adobe Flash Player, but i'm really disappointed because my Broadcom Crystal HD(BCM70015) isn't more supported.

I am little confused because a previous version (SQUARE) has worked fine, but after this update my netbook can't handle hd video provided by web sites.

Unfortunately cant find a changelog. Can anything clear this a bit more?

---

### Post by ray420 on 2011-06-05
i have a inspiron duo 1090 with crystal hd chip and everything is fine and youtube plays 1080p pretty well but if i try to play hulu or the hulu player flash fails and the hulu player closes or chromium says the plugin has crashed this happens on any on2 vp6 codex video i have tried to watch on the internet is there a work around for this maybe get crystal hd chip to play vp6 codex or configure flash to automatically switch off the chip for vp6 codex and back on for everything else if i do sudo rmmod crystalhd they play fine without the crystalhd chip but if i modprobe crystalhd i cant get it to play

---

### Post by wolfen69 on 2011-06-05
@ray420: what version of ubuntu and flash are you using? I also have a crystal hd card, but couldn't get 720 or 1080p with ubuntu 10.10 on my netbook.

---

### Post by ray420 on 2011-06-05
im running 11.04 natty with flash 10.3.XXX i got the drivers from here [http://git.wilsonet.com/crystalhd.git/](http://git.wilsonet.com/crystalhd.git/) i used the readme file from the drivers downloaded from brodcomms website i couldnt get those to compile the only thing is if i want to watch hulu i have to do "sudo rmmod crystalhd" to turn the drivers off then "modpobe crystalhd" to turn them back on also i guess it can handle only one video at a time so if you have a video paused and try to play another it wont use the chip hope that helps also i used the ignore ko.unsigned drivers

---

### Post by wolfen69 on 2011-06-06
> **ray420 said:**
> im running 11.04 natty with flash 10.3.XXX i got the drivers from here [http://git.wilsonet.com/crystalhd.git/](http://git.wilsonet.com/crystalhd.git/) i used the readme file from the drivers downloaded from brodcomms website i couldnt get those to compile the only thing is if i want to watch hulu i have to do "sudo rmmod crystalhd" to turn the drivers off then "modpobe crystalhd" to turn them back on also i guess it can handle only one video at a time so if you have a video paused and try to play another it wont use the chip hope that helps also i used the ignore ko.unsigned drivers

Thanks. I'll give it a go soon.

---

### Post by ray420 on 2011-06-13
any luck getting yours running wolfen and anyone know whats up with my hulu videos

---

### Post by travelinman81 on 2011-08-01
Just found this thread and CrystalHD support is in the new Adobe Flash player 11.. If you build the latest drivers from [http://git.wilsonet.com/crystalhd.git/](http://git.wilsonet.com/crystalhd.git/) then install the latest flash player from adobe [http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html) then you create a file in /etc/adobe/mms.cfg and put inside it.

EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true

It works! It really does.

I lied... I thought it worked last night but alas.. I can watch the ads but when the actual content starts flash crashes... Sorry for any false hope..

---

### Post by EkuquoL on 2011-08-01
Most Adobe flash issues, is from conflicting plugins or having too many Flash plugins installed.

Just go to the Synaptic -- Package Manager -- Then look over how many adobe flash plugins you have installed.

If all else fails you can manually insert adobe flash plugin into your /usr/lib/browser-plugin folder OR
usr/lib/firefox/plugin folder...  To manually insert or remove the flash plugin you will have to be root user.

---

### Post by beew on 2011-08-01
> **EkuquoL said:**
> Most Adobe flash issues, is from conflicting plugins or having too many Flash plugins installed.

Just go to the Synaptic -- Package Manager -- Then look over how many adobe flash plugins you have installed.

If all else fails you can manually insert adobe flash plugin into your /usr/lib/browser-plugin folder OR
usr/lib/firefox/plugin folder...  To manually insert or remove the flash plugin you will have to be root user.

Don't know anything about Crystal HD, but if whatever problem is caused by conflicting or out of dated versions of flash just install the flash-aid addon rom FireFox and run the script, it will install the latest flash, optimize it and remove conflicting versions.

---

