---
title: "vlc"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-28
There was this wonderful tutorial in this forum for installing non-gui mplayer. Is there a similar tutorial for vlc on Karmic Koala? I have tried installing it through Synaptic, Adept and Ubuntu Software Center. I also ensured that I selected proper files in  Adept besides vlc itself. But nothing worked. VLC opens but does not play audio or video.

---

### Post by wojox on 2009-11-28
Install Medibuntu:

```
sudo wget http://www.medibuntu.org/sources.list.d/karmic.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Install:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by confused_user on 2009-11-28
```
sudo apt-get update && sudo apt-get install vlc
```

and then

```
vlc -I dummy nameofvideo.avi
```

that launches vlc with no gui, just the video screen

you can put that in a script and give it an icon if you want.

---

### Post by iRounak on 2009-11-28
> **confused_user said:**
> [code]

you can put that in a script and give it an icon if you want.
Can someone elaborate this part and give me the script? I am assuming that this is a way to make non-gui vlc to open videos like gui vlc.

---

### Post by iRounak on 2009-11-28
> **wojox said:**
> Install Medibuntu:

```
sudo wget http://www.medibuntu.org/sources.list.d/karmic.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```Install:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```
I may have installed these already but I will try again

---

### Post by oldos2er on 2009-11-28
Here's some info on installing codecs: [https://help.ubuntu.com/9.10/musicvideophotos/C/index.html](https://help.ubuntu.com/9.10/musicvideophotos/C/index.html)

---

### Post by confused_user on 2009-11-28
> **iRounak said:**
> Can someone elaborate this part and give me the script? I am assuming that this is a way to make non-gui vlc to open videos like gui vlc.

yes of course.  Basically just install VLC as described.  It has the ability to be launched without a GUI built in.


Lets say you want to watch last nights Stargate Universe and that file is on your desktop

From a command line (terminal) you just type 

***vlc -I dummy ~/Desktop/stargate.universe.avi***

And a VLC window will open wth no gui, just the video.

I just played with a script and it didnt work as i expected but here is an even easier way to do it.

Right click on your video file

Choose ***Open With***

Choose ***Other Application***

At the bottom of the pop up that appears click on ***Use a custom command***

In the box that appears type ***vlc -I dummy***

Click ***Open***

VLC with no GUI will launch the video. :o

You dont have to do that every time, if you choose ***open with*** it will be in the list as ***vlc*** from now on.

You can also make it the default media player by

***Right click*** on the file

Click on the ***Open With*** tab

Click ***Add***

At the bottom of the pop up that appears click on ***Use a custom command***

In the box that appears type ***vlc -I dummy***

Click ***Add***

Then you will see an app called vlc in the main window which you just click on the little white circle to make it your default.

Easy peasy.

Wanna know how to play rar files in vlc without having to unpack them?

---

### Post by andrew.46 on 2009-11-28
Hi iRounak,

> **iRounak said:**
> There was this wonderful tutorial in this forum for installing non-gui mplayer. Is there a similar tutorial for vlc on Karmic Koala? 

vlc is a slightly different proposition to compile than MPlayer and as far as I know there is no guide for compiling it under Karmic on these forums. In part this is also because Karmic offers a reasonable version in the repository and there are also a couple of decent versions available in PPAs.

> I have tried installing it through Synaptic, Adept and Ubuntu Software Center. I also ensured that I selected proper files in  Adept besides vlc itself. But nothing worked. VLC opens but does not play audio or video.

The best way to test for errors and problems is to run vlc from the commandline with a reasonable level of verbosity selected:

```
cvlc -v **[COLOR="Red"]*myfile.mp4*[/COLOR]**
```

and any problems will then be easily revealed.

All the best,

Andrew

---

### Post by confused_user on 2009-11-28
just do a 

```
sudo apt-get remove vlc
```

To remove your previous efforts

then 

```
sudo apt-get update && sudo apt-get install vlc
```

thats really all you need to do to install vlc

You dont need to install any other codecs since vlc uses it's own.

Perform those steps and let us know what happens

edit: are you able to play videos with audio with movieplayer?  or any other player?  i'm just wondering if you have a more serious problem and not actually one with vlc.

---

### Post by iRounak on 2009-11-28
Thank you everyone for your replies. I will follow your instructions and post back the results.
> edit: are you able to play videos with audio with movieplayer? or any other player? i'm just wondering if you have a more serious problem and not actually one with vlc.

I can play everything with mplayer/smplayer. 
> 

Wanna know how to play rar files in vlc without having to unpack them?
Ofcourse, yes :)

---

### Post by iRounak on 2009-11-29
removed vlc with
```
sudo apt-get remove vlc
```But running the command ```
which vlc
```gave
/usr/bin/vlc

So I went to synaptic and removed everything related to vlc.

Then "which vlc" gave nothing.

Installed vlc with
```
sudo apt-get update && sudo apt-get install vlc
```Though during installation it was mentioned that 33 Mb will be downloaded. Nothing was downloaded.  Probably because it was downloaded earlier. This is the installation log:

> Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US      
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [65.9kB]                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [87.5kB]
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources [495B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [28.5kB]        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]     
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [54.1kB]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [12.2kB]   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [1,606B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [1,223B] 
Fetched 296kB in 8s (35.4kB/s)                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libggi2 libgii1 libgii1-target-x libggi-target-x
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtar libvlc2 libvlccore2 vlc-data vlc-nox vlc-plugin-pulse
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libtar libvlc2 libvlccore2 vlc vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 7 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/11.5MB of archives.
After this operation, 33.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libtar.
(Reading database ... 167576 files and directories currently installed.)
Unpacking libtar (from .../libtar_1.2.11-6_amd64.deb) ...
Selecting previously deselected package vlc-data.
Unpacking vlc-data (from .../vlc-data_1.0.2-1ubuntu2_all.deb) ...
Selecting previously deselected package libvlccore2.
Unpacking libvlccore2 (from .../libvlccore2_1.0.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libvlc2.
Unpacking libvlc2 (from .../libvlc2_1.0.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_1.0.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_1.0.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package vlc-plugin-pulse.
Unpacking vlc-plugin-pulse (from .../vlc-plugin-pulse_1.0.2-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libtar (1.2.11-6) ...

Setting up vlc-data (1.0.2-1ubuntu2) ...
Setting up libvlccore2 (1.0.2-1ubuntu2) ...

Setting up libvlc2 (1.0.2-1ubuntu2) ...

Setting up vlc-nox (1.0.2-1ubuntu2) ...
Setting up vlc (1.0.2-1ubuntu2) ...

Setting up vlc-plugin-pulse (1.0.2-1ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Then I opened a media file with vlc by right-clicking it and "Open with vlc".
VLC opened but it played neither audio nor video. No CPU usage in System Monitor. Then I did:
```
cvlc -v avifile
```> VLC media player 1.0.2 Goldeneye
[0x9200e8] main demux warning: no access_demux module matching "file" could be loaded
[0x942968] main interface error: no interface module matched "globalhotkeys,none"
[0x942968] main interface error: no suitable interface module
[0x82e888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x942968] dummy interface: using the dummy interface module...

But the video/audio does not play.

Also, tried 
> Code:
 	sudo wget [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list) --output-document=/etc/apt/sources.list.d/medibuntu.list 
Install:

 	Code:
 	sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

But they were installed already before running the above commands, so nothing changed.

---

### Post by confused_user on 2009-11-29
How to play rar files in vlc without uncompressing them first

```
 sudo apt-get update && sudo apt-get install unrar
```

```
unrar p -inul $1 | vlc - stargate.universe.avi
```

follow the steps i detailed in my other post to make it easier

or

past this is into a text file

```
#! /bin/sh
unrar p -inul $1 | vlc -
```

rename the text file ***rarvideo.sh***

```
sudo cp rarvideo.sh /usr/bin/
```

then from a terminal you can run it from anyway like so

```
rarvideo stargate.universe.avi
```

an viola

you can use Mplayer instead of vlc if you want, just change i from VLC to Mplayer

```
unrar p -inul $1 | mplayer -
```

:D

---

### Post by iRounak on 2009-11-29
to confused_user
Thanks for the help. Please see the post above you. I have failed to run vlc gui or non-gui.

---

### Post by confused_user on 2009-11-29
I think you need to start by removing all traces of vlc from your system.

you seem to have at least two different installations , one that the package manager installed and i dont know where the other one came from.

go back into synaptic and uninstall all traces of vlc.

then do a ```
sudo find / -name *vlc*
```

see what comes up and if i is vlc related delete it.

once your sure that all traces of vlc have gone try this again

```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by iRounak on 2009-11-29
first uninstalled vlc from terminal with the command:
sudo apt-get remove vlc
then removed everything related to vlc from Synaptic and Adept.
Then I ran you find command and found these. Should I remove these. If yes, how to remove these?
/usr/share/app-install/desktop/vlc.desktop
/var/cache/apt/archives/mozilla-plugin-vlc_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/libvlccore-dev_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/vlc-plugin-pulse_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/vlc-plugin-jack_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/vlc-plugin-sdl_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/vlc-plugin-ggi_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/libvlccore2_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/vlc-data_1.0.2-1ubuntu2_all.deb
/var/cache/apt/archives/vlc-plugin-svgalib_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/libvlc2_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/libvlc-dev_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/vlc_1.0.2-1ubuntu2_amd64.deb
/var/cache/apt/archives/vlc-nox_1.0.2-1ubuntu2_amd64.deb
/var/lib/dpkg/info/vlc.list
/var/lib/dpkg/info/libvlc2.list
/var/lib/dpkg/info/libvlccore2.list
/var/lib/dpkg/info/vlc.postrm
/var/lib/dpkg/info/vlc-data.list
/var/lib/dpkg/info/libvlccore2.postrm
/var/lib/dpkg/info/libvlc2.postrm
/home/tux/.config/vlc
/home/tux/.config/vlc/vlc-qt-interface.conf
/home/tux/.config/vlc/vlcrc
/home/tux/.cache/vlc
/home/tux/.local/share/mime/application/vlc.xml
/home/tux/.local/share/mime/application/x-google-vlc-plugin.xml
/home/tux/.local/share/mime/application/x-vlc-plugin.xml
/home/tux/.local/share/mime/video/x-google-vlc-plugin.xml
/home/tux/.local/share/mime/packages/application-x-google-vlc-plugin.xml
/home/tux/.local/share/mime/packages/application-vlc.xml
/home/tux/.local/share/mime/packages/video-x-google-vlc-plugin.xml
/home/tux/.local/share/mime/packages/application-x-vlc-plugin.xml
/home/tux/.local/share/vlc

---

### Post by confused_user on 2009-11-29
yes remove them, when you install it agian from apt it will reinstall it all, or just the bits you actually need.

I suspect that this is the problem.

Lets see.

type this to remove them all.

```
sudo find / -name "*vlc*"-exec rm -rf {} \;
```

this command will delete all of the files that resulted from your earlier 

find query. So rather than just print the results to the screen it will delete them as well.

---

### Post by iRounak on 2009-11-29
sudo find / -name "*vlc*"-exec rm -rf {} \;
find: paths must precede expression: rm
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

---

### Post by confused_user on 2009-11-29
ok i cant test it without wiping my own vlc from my computer, i was trying to save you having to delete them all one by one.

you can delete them by typing 

rm /usr/share/app-install/desktop/vlc.desktop

and so on and so on

you could try sudo find / -name *vlc* | rm -rf but maybe not a good idea if your not comfortable  with it (you could potentially do a lot of damage if you make a typo.

just delete them by hand using the rm command

edit: i wonder if it will work without the quotes

sudo find / -name *vlc*-exec rm -rf {} \;

---

### Post by mc4man on 2009-11-29
run this and then try vlc (obviously with vlc installed
```
vlc --reset-config --reset-plugins-cache
```

If no good then start vlc like this and try your file.
```
vlc -vv
```

 Post output from below this line
> [0x9a49140] [COLOR="Blue"]main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.[/COLOR]


---

### Post by iRounak on 2009-11-29
To mc4man, 
sorry, i have already removed it.

> **confused_user said:**
> 

edit: i wonder if it will work without the quotes

sudo find / -name *vlc*-exec rm -rf {} \;
yes, except that you missed the "space" before -exec.

I am trying to install it again, but see this
> 
Fetched 198B in 1s (101B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libvcdinfo0 libvlc2 libvlccore2 vlc-data vlc-nox vlc-plugin-pulse
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libvcdinfo0 libvlc2 libvlccore2 vlc vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 7 newly installed, 0 to remove and 1 not upgraded.
Need to get 11.5MB/11.6MB of archives.
After this operation, 33.6MB of additional disk space will be used.
Do you want to continue [Y/n]? 

Notice the line 
> Need to get 11.5MB/11.6MB of archives.
and
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Virtual Liberty on 2009-11-29
> **confused_user said:**
> 
type this to remove them all.

```
sudo find / -name "*vlc*"-exec **[COLOR="Red"]rm -rf[/COLOR]** {} \;
```


You shouldn't use -rf if you don't know what will be the target. One small mistake ( eg., regular expression ) and he's out of the game.

---

### Post by confused_user on 2009-11-29
yeah i know, but we do know what the target will be since we did a dry run before hand (read further up) and i did warn him.

dont worry about this

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

it just means that you dont have the key to use the medibuntu repository, you dont need it for this anyway

so its now downloading the vlc packages from scratch, what was the result?

---

### Post by iRounak on 2009-11-29
> **mc4man said:**
> 
```
vlc -vv
``` Post output from below this line

[0xc63888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xd77b58] main interface debug: looking for interface module: 4 candidates
[0xd71098] main interface debug: thread started
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
[0xd77b58] qt4 interface debug: Error while initializing qt-specific localization
[0xd77b58] main interface debug: using interface module "qt4"
[0xd77b58] main interface debug: TIMER module_need() : 206.234 ms - Total 206.234 ms / 1 intvls (Avg 206.234 ms)
[0xd77b58] main interface debug: thread started
[0xd77b58] main interface debug: thread ended
[0xd77b58] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0xd58d38] main playlist debug: rebuilding array of current - root Playlist
[0xd58d38] main playlist debug: rebuild done - 1 items, index -1
[0xd58d38] main playlist debug: processing request item null node Playlist skip 0
[0xd58d38] main playlist debug: starting new item
[0xd58d38] main playlist debug: creating new input thread
[0xd79738] main input debug: Creating an input for 'avifile'
[0xd79738] main input debug: thread started
[0xd79738] main input debug: using timeshift granularity of 50 MBytes
[0xd79738] main input debug: using timeshift path '/tmp'
[0xd79738] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0xd79738] main input debug: `avifile' gives access `' demux `' path `avifile'
[0xd79738] main input debug: creating demux: access='' demux='' path='avifile'
[0xd79d98] main demux debug: looking for access_demux module: 7 candidates
[0xd79d98] main demux debug: TIMER module_need() : 1.282 ms - Total 1.282 ms / 1 intvls (Avg 1.282 ms)
[0xd79738] main input debug: creating access '' path='avifile'
[0xd79d58] main access debug: looking for access module: 7 candidates
[0xd79d58] vcd access debug: trying .cue file: avifile.cue
[0xd79d58] vcd access debug: could not find .cue file
[0xd79d58] main access debug: using access module "access_directory"
[0xd79d58] main access debug: TIMER module_need() : 0.363 ms - Total 0.363 ms / 1 intvls (Avg 0.363 ms)
[0x109fcf8] main stream debug: Using AStream*Block
[0x109fcf8] main stream debug: pre buffering
[0x109fcf8] main stream debug: received first data after 0 ms
[0x109fcf8] main stream debug: prebuffering done 160 bytes in 0s - 5787 kbytes/s
[0x10a2bd8] main stream debug: looking for stream_filter module: 4 candidates
[0x10a2bd8] main stream debug: TIMER module_need() : 0.062 ms - Total 0.062 ms / 1 intvls (Avg 0.062 ms)
[0x10a28e8] main stream debug: looking for stream_filter module: 1 candidate
[0x10a28e8] main stream debug: using stream_filter module "stream_filter_record"
[0x10a28e8] main stream debug: TIMER module_need() : 0.059 ms - Total 0.059 ms / 1 intvls (Avg 0.059 ms)
[0xd79738] main input debug: creating demux: access='' demux='xspf-open' path='avifile'
[0x10a38b8] main demux debug: looking for demux module: 1 candidate
[0x10a38b8] playlist demux debug: using XSPF playlist reader
[0x10a38b8] main demux debug: using demux module "playlist"
[0x10a38b8] main demux debug: TIMER module_need() : 0.080 ms - Total 0.080 ms / 1 intvls (Avg 0.080 ms)
[0xd79738] main input debug: looking for a subtitle file in /media/8/Multimedia 8/
[0xd79738] main input debug: `avifile' successfully opened
[0x10a3a98] main xml debug: looking for xml module: 2 candidates
[0x10a3a98] main xml debug: using xml module "xtag"
[0x10a3a98] main xml debug: TIMER module_need() : 0.064 ms - Total 0.064 ms / 1 intvls (Avg 0.064 ms)
[0x10a38b8] playlist demux debug: parsed 0 tracks successfully
[0x10a3a98] main xml debug: removing module "xtag"
[0xd79738] main input debug: EOF reached
[0x10a38b8] main demux debug: removing module "playlist"
[0x10a28e8] main stream debug: removing module "stream_filter_record"
[0xd79d58] main access debug: removing module "access_directory"
[0xd79738] main input debug: thread ended
[0xd58d38] main playlist debug: dead input
[0xd79738] main input debug: TIMER input launching for 'avifile' : 5.364 ms - Total 5.364 ms / 1 intvls (Avg 5.364 ms)
[0xd58d38] main playlist debug: changing item without a request (current 0/1)
[0xd58d38] main playlist debug: nothing to play

---

### Post by iRounak on 2009-11-29
> so its now downloading the vlc packages from scratch, what was the result?
I did not save that log. But it was normal. No errors.

---

### Post by iRounak on 2009-11-29
cvlc -v avifile.avi 
> VLC media player 1.0.2 Goldeneye
[0x26f10e8] main demux warning: no access_demux module matching "file" could be loaded
[0x2713968] main interface error: no interface module matched "globalhotkeys,none"
[0x2713968] main interface error: no suitable interface module
[0x25ff888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x2713968] dummy interface: using the dummy interface module...

no audio, no video

---

### Post by Onesimus on 2009-11-29
> **iRounak said:**
> cvlc -v avifile.avi 


no audio, no video

I had a similar problem with vlc not playing vidio (audio did play).  You could try this:

[http://ubuntuforums.org/showthread.php?p=8407427#post8407427]("http://ubuntuforums.org/showthread.php?p=8407427#post8407427")

---

### Post by iRounak on 2009-11-29
> **Onesimus said:**
> I had a similar problem with vlc not playing vidio (audio did play).  You could try this:

[http://ubuntuforums.org/showthread.php?p=8407427#post8407427](http://ubuntuforums.org/showthread.php?p=8407427#post8407427)
Thanks Onesimus, that was really helpful. Now can anyone enlighten me on advantages/disadvantages of using XVideo extension output for video instead of the default one.

---

### Post by iRounak on 2009-11-29
actually, now it plays with default video output. I don't know why.

---

### Post by andrew.46 on 2009-11-30
Hi confused,

> **confused_user said:**
> you can use Mplayer instead of vlc if you want, just change i from VLC to Mplayer

```
unrar p -inul $1 | mplayer -
```

Mind you newer versions of MPLayer need some cache as well and will fail without it:

```
unrar p -inul myarchive.rar | mplayer *[COLOR="Red"]-cache 2048[/COLOR]* -
```


Andrew

---

### Post by confused_user on 2009-11-30
Whatever works for you :p

i don't need to add the cache bit to my mplayer.

In fact caching is disabled on mine.  Not sure what version i have actually since when i go to help > about all i get is a list if names.

edit: oh ok i've got 2:1.0~rc3+svn20090426

phew, i got that from the default karmic repo's as well :)

I suspect that maybe you have caching enabled on yours? and that's why you have to add it as an argument ?

---

### Post by andrew.46 on 2009-11-30
Hi confused,

> **confused_user said:**
> I suspect that maybe you have caching enabled on yours? and that's why you have to add it as an argument ?

I am running the svn MPlayer:

```
andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r29971-4.3.3 (C) 2000-2009 MPlayer Team
```

and somewhere over the last few months, I can't pin it down exactly, the MPlayer developers shifted the goalposts and from then on playing from rar archives required a cache. Obviously not for the Karmic repository version though :).

Andrew

---

### Post by confused_user on 2009-11-30
The difference in the method i suggest is that mplayer / vlc are not playing the rar file directly. Unrar is piping it's output into mplayer / vlc.

In any case, it **does** work without caching enabled and without specifying the cache argument.  

Actually it works exactly as a described in my original post.

Try it, you may be pleasantly described.

---

