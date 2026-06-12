---
title: "How to install Rosegarden?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by SNR99 on 2010-02-04
I am an absolute newbie to Ubuntu but am loving a bit of version 9.10 which I have just managed to successfully install on my laptop.  I plan to use this as a computer to talk to my digital piano which has a USB midi interface.

I have had a search around and Rosegarden looks like it ticks all the boxes I need.  However, being an absolute newbie, the installation is baffling.  Looking through the notes, the list of things I need are:

**"Runtime requirements**

     In order to be fully functional and provide the optimal user experience, Rosegarden requires the following external applications.  
 
[LIST]
[*] bash
[*] available, functioning ALSA General MIDI soft synth (QSynth, TiMidity++, etc.) with soundfont (Fluid-Soundfont, Freepats, etc.)
[*] lilypond
[*] ocular OR acroread OR evince
[*] gtklp OR lpr OR lp
[*] jackd
[*] flac
[*] wavpack/wvunpack
[*] qjackctl
[*] DSSI plugins (any available)
[*] LADSPA plugins (any available)"
[/LIST]
However, I am now lost!  Can anyone help me to work out  

1) Whether I already have any of this list installed
2) How I can go about installing the above components
3) If there is then a sequence of items I need to go through to then get Rosegarden to work.

Many thanks

---

### Post by howefield on 2010-02-04
Rosegarden is in the repository, so install with Synaptic Package Manager, it should pull in whatever dependancies it needs, if you haven't got them already.

---

### Post by SNR99 on 2010-02-04
THanks for the quick reply - I tried installing as you suggested which seemed to work OK.  When I came to run Rosegarden however, I got the message  "Failed to connect to the JACK server".

I then had a look around and found something called JACK Control which I opened.  Im not sure what JACK is exactly but looks like an essential component.  Anyway, after opening, I get a JACK Audio Connection Kit and then select START.  I then get  "Error - JACK Audio Connection Kit, could not connect to JACK server as client" and the Message window lists the following:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]19:42:50.903 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:42:50.929 Statistics reset.[/COLOR]
 [COLOR=#66CC99]19:42:50.997 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]19:42:51.195 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:43:04.452 Startup script...[/COLOR]
 [COLOR=#990099]19:43:04.452 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]19:43:04.854 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:43:04.854 JACK is starting...[/COLOR]
 [COLOR=#990099]19:43:04.855 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]19:43:04.866 JACK was started with PID=7845.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1216076096, from thread -1216076096] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]19:43:04.878 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]19:43:04.878 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:43:04.879 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]19:43:05.285 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]19:43:07.023 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

This is where my knowledge gets stuck.  Can anyone help me?

---

### Post by ChrisB111 on 2010-02-04
Have a look at these pages:
[LIST]
[*][http://ubuntustudio.org/](http://ubuntustudio.org/)
[*][https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[*][https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
[/LIST]
The problem I think you have is, your trying to run jack in realtime mode without the realtime kernal installed. The relevant info to fix this is in the 2nd link under *Real Time Kernel & Xruns*. I am not an expert at this, hence why I am avoiding telling you what to do, however looking at these pages should get you started.

Chris

---

### Post by SNR99 on 2010-02-04
Thanks.  I have installed a load of things as recommended in the seconds link which seems to be successful.  However, in the Real Time Support section of the Ubuntu Studio Preperation notes it details the need to reboot into a low latency kernel.  This has lost me - how do I do this?!

---

### Post by oldos2er on 2010-02-04
Once you install the real time kernel, you will have an option in your grub menu to boot it.

---

### Post by mikechant on 2010-02-05
The alternative if you have the disc space is to install Ubuntu Studio alongside regular Ubuntu. This uses the realtime kernel and has loads of relevant applications pre-installed. 

It's safer than using your normal Ubuntu install with the realtime kernel because the rt kernel is fairly crash-prone (in my experience) which gives a risk of filesystem corruption (although if you're using ext3/4 the journalling should allow recovery of the filesystem to a consistent state). 

If you have a seperate Studio install and it gets messed up you can still use your regular install for non-Rosegarden stuff.

---

### Post by SNR99 on 2010-02-23
Ok after much time and searching for answers, I finally got Ubuntu Studio installed and the dual boot menus working.

I installed Rosegarden from the repository and all works great so thanks for all your help.

However, when I looked at their website, I see there is a new version just released (10.02).  I cant find this in the repository nor does there appear to be a simple way to install this new version.  I tried downloading a compressed file which then decompressed and gave me a list of files.  My Linux knowledge stopped there unfortunately.  Anyone know of a simple way of installing this new version?:D

---

### Post by mikechant on 2010-02-24
I'd suggest trying the following before attempting to install from source:
Go to this download page:
[https://launchpad.net/ubuntu/+archive/primary/+sourcepub/971086/+listing-archive-extra](https://launchpad.net/ubuntu/+archive/primary/+sourcepub/971086/+listing-archive-extra)

And download
rosegarden-data_10.02-0ubuntu2_all.deb

if you're running 64 bit ubuntu studio also download
rosegarden_10.02-0ubuntu2_amd64.deb

or if you're running 32 bit ubuntu studio also download
rosegarden_10.02-0ubuntu2_i386.deb

Then install the two .deb files you have downloaded just by double-clicking them. You may need to install the 'data' .deb first, I'm not sure; if you get it the wrong way round you may get a 'missing dependancies' error, in that case try installing the two packages in reverse order to what you tried first time.

---

### Post by SNR99 on 2010-03-21
Thanks for your help.  I managed to download the .deb files below and installed the 'data' first.  This worked fine but once I then tried to install the second 32 bit deb file, the peckage installer says 

"Error: Dependency is not satisfiable: libasound2 (>> 1.0.22)".

This is where I am now stuck!  Unfortunatley now Rosegarden doesnt work at all!  Can anyone please help??
;)


"I'd suggest trying the following before attempting to install from source:
Go to this download page:
[https://launchpad.net/ubuntu/+archiv...-archive-extra]("https://launchpad.net/ubuntu/+archive/primary/+sourcepub/971086/+listing-archive-extra")

And download
rosegarden-data_10.02-0ubuntu2_all.deb

if you're running 64 bit ubuntu studio also download
rosegarden_10.02-0ubuntu2_amd64.deb

or if you're running 32 bit ubuntu studio also download
rosegarden_10.02-0ubuntu2_i386.deb

Then install the two .deb files you have downloaded just by double-clicking them. You may need to install the 'data' .deb first, I'm not sure; if you get it the wrong way round you may get a 'missing dependancies' error, in that case try installing the two packages in reverse order to what you tried first time."

---

### Post by mikechant on 2010-03-26
Sorry I haven't followed this up until now but I've been working hard at my 'real job' :)

OK, so you're running 9.10 and as far as I can see that supplies v1.0.18 of libasound2, so you need to upgrade this package to v1.0.22 as per the error message. v1.0.22 is the default version in Ubuntu 10.04 (which I'm running the beta version of at present).

So if you go to
[http://packages.ubuntu.com/lucid/libs/libasound2](http://packages.ubuntu.com/lucid/libs/libasound2)
and use the download links at the bottom left of the page you can get the relevant .deb file from the 10.4 repository, install this and try installing the failed package again.
Of course, you may get further dependency errors but you should be able to work your way through them in the same way.
Because you want the latest version you're having to do manually some of the work that the repository system usually does for you.


Incidentally, if you wanted to go back to the working release you should be able to just use synaptic to uninstall the 10.02 data package and then reinstall the older version; or uninstall all rosegarden packages and reinstall the older versions.

---

