---
title: "Installed Openshot video editor and it broke VLC and Totem playback"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by darkxman on 2009-10-03
I just installed the Openshot video editor ([http://www.openshotvideo.com/](http://www.openshotvideo.com/)) via their PPA and it worked, but now the Totem and VLC won't play any videos anymore. I uninstalled Openshot, but it didn't help. 

Read this ([https://answers.launchpad.net/openshot/+faq/723](https://answers.launchpad.net/openshot/+faq/723)) and found out why. I didn't notice that it replaces a bunch of ffmpeg stuff.

Anybody know what I have to uninstall and reinstall to get Totem and VLC working again?

I'm using Ubuntu 9.04.

VLC says 
"No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this."

console output

VLC probably does not support this sound or video format.
[0xf7ffe8] main decoder error: no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.
[0xf7ffe8] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000


Totem says
an error occurred
internal data stream error

console output

** Message: Error: Internal data stream error.
gstavidemux.c(4163): gst_avi_demux_loop (): /GstPlayBin:play/GstDecodeBin:decodebin1/GstAviDemux:avidemux1:
streaming stopped, reason not-negotiated

---

### Post by mc4man on 2009-10-03
easiest way is first make sure the ppa isn't in your sources anymore.

Then search ffmpeg in synaptic and mark for removal any or all of the libs
(libavcodecXX, libavformatXX, ect. and ffmpeg itself if the ppa version.
(scroll down to ck them all, last one would be libswscale0 ( using X's cause not sure what version #'s you have in jaunty, 52, 51 ect.

You'll lose vlc and some plugins, but they can be re-installed

After removing, then install the "unstripped" versions of the same lib's you just removed, and vlc, plugins ect.

You're the 3rd or 4th person in the last day with same problem - those openshot ppa ffmpeg and  libs are junk if you want to use media players

edit
if vlc gives you any trouble afterwards then start with this to reset
```

vlc --reset-config --reset-plugins-cache
```

---

### Post by the.phantom on 2009-10-03
> You're the 3rd or 4th person in the last day with same problem - those openshot ppa ffmpeg and libs are junk if you want to use media players




just a guess, but this might be why ?

[http://d0od.blogspot.com/2009/09/oepnshot-ppa-video-editor-linux.html](http://d0od.blogspot.com/2009/09/oepnshot-ppa-video-editor-linux.html)

---

### Post by darkxman on 2009-10-03
Thanks! That worked perfectly. I won't be installing Openshot again any time soon. :P


> **mc4man said:**
> easiest way is first make sure the ppa isn't in your sources anymore.

Then search ffmpeg in synaptic and mark for removal any or all of the libs
(libavcodecXX, libavformatXX, ect. and ffmpeg itself if the ppa version.
(scroll down to ck them all, last one would be libswscale0 ( using X's cause not sure what version #'s you have in jaunty, 52, 51 ect.

You'll lose vlc and some plugins, but they can be re-installed

After removing, then install the "unstripped" versions of the same lib's you just removed, and vlc, plugins ect.






Yep, that's where my problems began. :)


> **the.phantom said:**
> just a guess, but this might be why ?

[http://d0od.blogspot.com/2009/09/oepnshot-ppa-video-editor-linux.html](http://d0od.blogspot.com/2009/09/oepnshot-ppa-video-editor-linux.html)

---

### Post by wyrless2002 on 2009-10-03
@Mc4man: How is it everytime I go look for answers to my burning questions, your name is there?:P  Thanks AGAIN. This did work. 

@the.phantom: Yes, I fell for OMG!Ubuntu!'s article too. :(

---

### Post by themusicalduck on 2009-10-03
That article was the reason for my borked VLC too :/

In the end I did a reinstall..

---

### Post by 3rdalbum on 2009-10-03
I realised that this was happening last night and I removed the PPA and Force Versioned all the libav*-unstripped (which only works if you Force Version them in the correct order) and got away without uninstalling anything else.

Freaking ridiculous, now I know why some people are wary of PPAs.

Oh BTW it doesn't interfere with the "ffplay" program; that still works if you need immediate video playback.

---

### Post by mc4man on 2009-10-04
Actually have become very curious about this, looking at their sources the libs should be ok. 
The problem is that while any new 'capabilities' afforded by the libs won't be used by  current repo apps that use them, they should have maintained what was previously 'enabled'. ( mainly thru libavcodecXX

In the case of the openshot ppa ffmeg libs, current installed apps like vlc lose prior 'enables', while probably the libs themselves have them enabled.

Unfortunately I only use a modded hardy that would be unsuitable and karmic.
In the case of karmic the openshot ppa doesn't have a ffmpeg build, only the libs, so direct testing is not possible. (would be in jaunty where there is a ffmpeg

I can say with 100% assuredly that installing a more recent ffmpeg source as a package set should not affect what a current repo app that uses the libs can play. ( do it all the time.

In a quick test on my testing karmic ( where the openshot libs killed playback

Removed ffmpeg, all ffmpeg libs and vlc

Made a local repo and put a current ffmpeg package set from my real karmic install along with some add. dep. packages ( libx264, opencore amr, no different than adding a ppa

Installed  the karmic vlc which also installed the needed ffmpeg libs from the local repo

All previously playable files are still playable including the ones in ? from some of the posters here , wma2 and avc1

So if you really wanted openshot i'd drop that ppa a note and ask them to get it together

( there are other options, but they really should be taking care of this

---

### Post by vjkeito on 2009-10-04
I have this issue.

I don't really understand what you mean by force versioning, so doing so in the correct order seems like an impossible task.

Please help!  What do I need to do to get my system back to normal!?!

---

### Post by rapsodia on 2009-10-17
> **darkxman said:**
> Thanks! That worked perfectly. I won't be installing Openshot again any time soon. :P







Yep, that's where my problems began. :)



Thank you for the update PPA be wary always btw I fell for that link as well Damn you good reviews !!!

---

### Post by jukingeo on 2009-10-19
Wow! When did this problem start happening?  I have Openshot on my system right now and I didn't have any problems with Totem or VLC. So this problem must be fairly recent.

Overall Openshot works but I have a video sync problem. I was going to check back to the Openshot site to see if they have a new version to download, but I came across this thread here.  Now I am glad I DIDN'T check for the latest download.  I need VLC and certainly can't have any trouble with that.

I guess they must be addressing the video sync problem (which is a good thing) because they were talking about problems with ffmpeg.  But this is a new one on me that downloading a newer version now will cause problems with other video software.  I can't have that!

I think I am just going to lay low with Openshot until all the bugs are ironed out.  I am probably going to go back to learning Cinelerra.  Longer, yes...but it works!

Geo

---

### Post by WindPower on 2009-10-27
I have this problem too... But I ran
```
sudo apt-get remove --purge vlc libavcodec-* libavfilter-* libavformat-* ffmpeg vlc-*
```
Then I removed the PPA from sources.list, then I ran sudo apt-get update, then sudo apt-get autoremove, sudo apt-get autoclean, sudo apt-get purge, and finally
```
sudo apt-get install vlc
```
Then I started vlc with --reset-config --reset-plugins-cache, I saw the "Album art policy dialog" thing which confirms that I passed the arguments correctly, then I try to open a video and still can't play it D:

---

### Post by 3rdalbum on 2009-10-28
> **WindPower said:**
> I have this problem too... But I ran
```
sudo apt-get remove --purge vlc libavcodec-* libavfilter-* libavformat-* ffmpeg vlc-*
```

That's an option, but it also removes half my programs that rely on the libav packages :-)

Instead you can do a search in Synaptic for "libav" after you have removed the PPA, and then you need to click on each package and use the "Force Version" option in Synaptic to force it back down to the regular Ubuntu version. It only works if you do it in the correct order - so if you click Force Version and it tells you it's going to delete half your system, then click Cancel and try it with a different libav package.

---

### Post by narcisgarcia on 2009-10-28
Follow strictly these steps to fix the problem with a clean result:

[LIST=1]
[*] Open **Synaptic** package manager
[*] In the **Settings** menu, open the **Repositories** option.
[*] In the **Third-Party Software** tab, remove the "ppa...openshot" lines.
[*] Close the small **Software Sources** window, and use the **Reload** button to update repositories.
[*] Search **libpostproc** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libswscale** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavcodec** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavformat** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] In the **File** menu, use the **Save Markings As** option, and use a name like **synaptic.txt**
[*] _Once the markings are saved_, perform the actions with the **Apply** button.
[*] Open the **synaptic.txt** file with a text editor.
[*] Replace all the words **deinstall** with **install** and save the file.
[*] Return to Synaptic and load **synaptic.txt** with the **Read Markings** option in the **File** menu.
[*] Use the **Apply** button and after the process your software will be as before OpenShot.
[/LIST]

If you want to install OpenShot, don't use the **PPA Instructions** from the Download section; use the **DEB Instructions**. (once downloaded, install first the dependencies and then OpenShot).

---

### Post by WindPower on 2009-10-28
Nope, still have the same problem :(
```
cat /etc/apt/sources.list | grep openshot 
```
does not print any lines, and there's no line with "openshot" in it in Synaptic
Then I follow your instructions, it correctly uninstalls the packages... Then it reinstalls the packages... And I launch VLC with the --reset-config --reset-plugins-cache flags, and no dice.

Perhaps it might be related to the fact that Apt is downloading the libav* from another bad PPA? Here's my sources.list:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse



deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ jaunty main
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ jaunty main

deb http://ppa.launchpad.net/eclipse-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/eclipse-team/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/samrog131/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/samrog131/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/mactel-support/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main
deb http://ppa.launchpad.net/keepassx/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/keepassx/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://ppa.launchpad.net/msn-pecan/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/msn-pecan/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/earcandy-devel/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/earcandy-devel/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main
deb http://deb.playonlinux.com/ jaunty main
deb http://ppa.launchpad.net/sunab/ppa/ubuntu jaunty main
#deb http://ppa.launchpad.net/turl/ppa/ubuntu jaunty main
#deb-src http://ppa.launchpad.net/turl/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/loic-martin3/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/loic-martin3/ppa/ubuntu jaunty main
```
Note that there is indeed "deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main" in there, which lets me use VLC 1.0.2. But it has always worked before I added the Openshot PPA, so I don't see why it would stop working now :-?

---

### Post by narcisgarcia on 2009-10-28
Follow the same procedure but deactivating (not deleting) all the Third-Party repositories.
After all, test VLC/Totem play, and re-enable each Third-Party repository to upgrade others again.

---

### Post by WindPower on 2009-10-28
> **narcisgarcia said:**
> Follow the same procedure but deactivating (not deleting) all the Third-Party repositories.
After all, test VLC/Totem play, and re-enable each Third-Party repository to upgrade others again.
I all the repos starting with ppa, then did the same thing, and now I have VLC 0.9.9a, and here's what happens when I start it...
```
$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
vlc: pthread_mutex_lock.c:87: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.
Aborted
```
So now it's worse because I can't start VLC at all D:

---

### Post by narcisgarcia on 2009-10-29
Ok, you have downgraded the packages to the official provided versions, now it's time do re-enable the other PPA repositories (not openshot) and update+upgrade packages.

---

### Post by jfeole on 2009-10-31
Thanks guys..

I'm running 9.10 x64, just upgraded yesterday.  Right after, .avi, .mpg would only play audio, not video. This is what fixed it for me per this thread:

--
$ sudo apt-get remove smplayer
$ sudo apt-get remove mplayer
$ sudo apt-get remove libx264-67 --purge
$ sudo apt-get install libx264-67
$ sudo apt-get install smplayer
$ sudo apt-get install mplayer
$ sudo apt-get install vlc

--

Regards,
JFeole

---

### Post by narcisgarcia on 2009-11-01
jfeole your solution successess because the upgrade tool already deactivates the third-party repositories for you.

---

### Post by WindPower on 2009-11-01
Still no luck for me... I said screw it, I installed Karmic (fresh install, formatted my Ubuntu partition) and never added the Openshot PPA, yet I still get the same error. So it's probably not due to the Openshot PPA... yet it's the same error message. D:

---

### Post by gazambuja on 2009-11-02
This work fine with me. Thanks!

Contribute:
to replace all deinstall to install, you can run this command:
```
sed 's\deinstall\install\g' synaptic.txt > synaptic_install.txt
```
and use this file: synaptic_install.txt


> **narcisgarcia said:**
> Follow strictly these steps to fix the problem with a clean result:

[LIST=1]
[*] Open **Synaptic** package manager
[*] In the **Settings** menu, open the **Repositories** option.
[*] In the **Third-Party Software** tab, remove the "ppa...openshot" lines.
[*] Close the small **Software Sources** window, and use the **Reload** button to update repositories.
[*] Search **libpostproc** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libswscale** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavcodec** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavformat** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] In the **File** menu, use the **Save Markings As** option, and use a name like **synaptic.txt**
[*] _Once the markings are saved_, perform the actions with the **Apply** button.
[*] Open the **synaptic.txt** file with a text editor.
[*] Replace all the words **deinstall** with **install** and save the file.
[*] Return to Synaptic and load **synaptic.txt** with the **Read Markings** option in the **File** menu.
[*] Use the **Apply** button and after the process your software will be as before OpenShot.
[/LIST]

If you want to install OpenShot, don't use the **PPA Instructions** from the Download section; use the **DEB Instructions**. (once downloaded, install first the dependencies and then OpenShot).

---

### Post by wessel_k on 2009-11-13
Thanx!. Saved me a lot of work.

Regards,

Wessel

---

### Post by ElSlunko on 2009-11-25
Uninstalling the PPA, removing the proper libs & clearing the cache worked for me. Too bad it doesn't work via PPA, going to try through Debs and see how that works out.

Debs seem to work. Have Openshot installed and it hasn't affected my ability to play movie files.

---

### Post by quinnten83 on 2009-11-25
I tried sometime back again installing through the ppa and got the same issue. Fortunately, it was a recent install, so a clean reinstall was not a problem.
The debs do work without issue. It 's a shame, because I really like openshot. I daresay it is the best video editor on Linux, perhaps save for cinelerra. This is ruining the developers hard and excellent work.

---

### Post by rinoshea on 2009-11-26
> **mc4man said:**
> easiest way is first make sure the ppa isn't in your sources anymore.

Then search ffmpeg in synaptic and mark for removal any or all of the libs
(libavcodecXX, libavformatXX, ect. and ffmpeg itself if the ppa version.
(scroll down to ck them all, last one would be libswscale0 ( using X's cause not sure what version #'s you have in jaunty, 52, 51 ect.

You'll lose vlc and some plugins, but they can be re-installed

After removing, then install the "unstripped" versions of the same lib's you just removed, and vlc, plugins ect.

You're the 3rd or 4th person in the last day with same problem - those openshot ppa ffmpeg and  libs are junk if you want to use media players

edit
if vlc gives you any trouble afterwards then start with this to reset
```

vlc --reset-config --reset-plugins-cache
```

Thank you so much!! This worked perfectly. The only extra step is to reinstall mplayer, mencoder, vlc, and any other frontends you use (miro, mplayer, etc.)

---

### Post by korsairtuga on 2009-12-11
> **narcisgarcia said:**
> Follow strictly these steps to fix the problem with a clean result:

[LIST=1]
[*] Open **Synaptic** package manager
[*] In the **Settings** menu, open the **Repositories** option.
[*] In the **Third-Party Software** tab, remove the "ppa...openshot" lines.
[*] Close the small **Software Sources** window, and use the **Reload** button to update repositories.
[*] Search **libpostproc** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libswscale** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavcodec** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavformat** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] In the **File** menu, use the **Save Markings As** option, and use a name like **synaptic.txt**
[*] _Once the markings are saved_, perform the actions with the **Apply** button.
[*] Open the **synaptic.txt** file with a text editor.
[*] Replace all the words **deinstall** with **install** and save the file.
[*] Return to Synaptic and load **synaptic.txt** with the **Read Markings** option in the **File** menu.
[*] Use the **Apply** button and after the process your software will be as before OpenShot.
[/LIST]

If you want to install OpenShot, don't use the **PPA Instructions** from the Download section; use the **DEB Instructions**. (once downloaded, install first the dependencies and then OpenShot).

This worked for me! Thanks!!

---

### Post by tolmun on 2009-12-20
> **WindPower said:**
> I have this problem too... But I ran
```
sudo apt-get remove --purge vlc libavcodec-* libavfilter-* libavformat-* ffmpeg vlc-*
```
Then I removed the PPA from sources.list, then I ran sudo apt-get update, then sudo apt-get autoremove, sudo apt-get autoclean, sudo apt-get purge, and finally
```
sudo apt-get install vlc
```
Then I started vlc with --reset-config --reset-plugins-cache, I saw the "Album art policy dialog" thing which confirms that I passed the arguments correctly, then I try to open a video and still can't play it D:

Great solution

Thank you

---

### Post by ionoff on 2010-01-01
> **mc4man said:**
> easiest way is first make sure the ppa isn't in your sources anymore.

Then search ffmpeg in synaptic and mark for removal any or all of the libs
(libavcodecXX, libavformatXX, ect. and ffmpeg itself if the ppa version.
(scroll down to ck them all, last one would be libswscale0 ( using X's cause not sure what version #'s you have in jaunty, 52, 51 ect.

You'll lose vlc and some plugins, but they can be re-installed

After removing, then install the "unstripped" versions of the same lib's you just removed, and vlc, plugins ect.

You're the 3rd or 4th person in the last day with same problem - those openshot ppa ffmpeg and  libs are junk if you want to use media players

edit
if vlc gives you any trouble afterwards then start with this to reset
```

vlc --reset-config --reset-plugins-cache
```

this solved my problem, thanks.

---

### Post by netahoy on 2010-03-09
OK the trick worked for me too.... and saved me a lot of hardwork.
I tried doing the same for my other issues where installing Mandvd was earlier promting to remove all existing applications like vlc mplayer etc.

---

### Post by syncdram on 2010-03-21
> **jukingeo said:**
> Wow! When did this problem start happening?  I have Openshot on my system right now and I didn't have any problems with Totem or VLC. So this problem must be fairly recent.

Overall Openshot works but I have a video sync problem. I was going to check back to the Openshot site to see if they have a new version to download, but I came across this thread here.  Now I am glad I DIDN'T check for the latest download.  I need VLC and certainly can't have any trouble with that.

I guess they must be addressing the video sync problem (which is a good thing) because they were talking about problems with ffmpeg.  But this is a new one on me that downloading a newer version now will cause problems with other video software.  I can't have that!

I think I am just going to lay low with Openshot until all the bugs are ironed out.  I am probably going to go back to learning Cinelerra.  Longer, yes...but it works!

GeoI had the same problem with the new version of open shot. here is the solution i found. download oggconverter, load your raw video in then hit advanced change from ogg to matroska. make sure the sliders are at both the highest quality convert your video and then slide her into openshot. works everytime. i disscoverd this when the only video files that acturally synced were oog files. hope this helps

---

### Post by syncdram on 2010-03-21
For those who are having problems with the new version of openshot audio and video sync here is what i found to work. first download and install oggconvert. before doing anything in openshot load your video into oggconvert go to advanced and change from ogg to matroska. then make sure both quality sliders are at high quality. once this is done then slip your video into openshot. works for me every time. hope this helps. I found this out by accident when i discovered the only files that were in sync were my .ogg files.

---

### Post by inspired on 2010-04-13
> **narcisgarcia said:**
> Follow strictly these steps to fix the problem with a clean result:

[LIST=1]
[*] Open **Synaptic** package manager
[*] In the **Settings** menu, open the **Repositories** option.
[*] In the **Third-Party Software** tab, remove the "ppa...openshot" lines.
[*] Close the small **Software Sources** window, and use the **Reload** button to update repositories.
[*] Search **libpostproc** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libswscale** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavcodec** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] Search **libavformat** and mark any installed package for removal; no problem marking other dependent software to be removed.
[*] In the **File** menu, use the **Save Markings As** option, and use a name like **synaptic.txt**
[*] _Once the markings are saved_, perform the actions with the **Apply** button.
[*] Open the **synaptic.txt** file with a text editor.
[*] Replace all the words **deinstall** with **install** and save the file.
[*] Return to Synaptic and load **synaptic.txt** with the **Read Markings** option in the **File** menu.
[*] Use the **Apply** button and after the process your software will be as before OpenShot.
[/LIST]

If you want to install OpenShot, don't use the **PPA Instructions** from the Download section; use the **DEB Instructions**. (once downloaded, install first the dependencies and then OpenShot).

This solution worked for me.
I was NOT able to identify which repository/ppa entry was the openshot one, as there were none with the word "openshot". So I used Ubuntu Tweak to remove the repository, as it lists them by the application name.

Then I also took the step of removing the lines in the saved synaptic markings file for:
[LIST=2]
[*]  **libpostproc**
[*]  **libswscale** 
[*]  **libavcodec** 
[*]  **libavformat**
[/LIST]
Because the ones listed were the unstripped ones, and I wanted to make sure it didn't try to install those again.

All works now, as far as I can tell.
Thanks for this info.

---

