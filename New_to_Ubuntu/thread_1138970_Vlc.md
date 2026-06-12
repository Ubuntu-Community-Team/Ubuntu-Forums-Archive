---
title: "Vlc"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-04-26
I got the latest VLC from their website after installing 9.04 and it's very different from the old one. the controls open in their own window, it's slow to open, and some files just stop playing. is there a setting to embed the controls in the video window like the old one, or can i get and older version of VLC anywhere?

---

### Post by jmmL on 2009-04-26
It's fixed in Kow's PPA: [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

That version also has support for VDPAU, if you have a nVidia card and are interested.

---

### Post by doas777 on 2009-04-26
vlc has always behaved in the way you describe for me, by default.

---

### Post by joey-elijah on 2009-04-26
> **doas777 said:**
> vlc has always behaved in the way you describe for me, by default.

It never for me - on either Linux, OS X or Windows. There was always one window and the video always played inside it. 

The version i have atm has to separate windows, one control's and one video. When you enter video into fullscreen you can't get any 'hover' controls up meaning you have to exit fullscreen to access controls.

---

### Post by benerivo on 2009-04-26
Older versions can are kept inside older repositories. The current repository is jaunty, but see [here]("http://packages.ubuntu.com/search?keywords=vlc&searchon=names&suite=all&section=all") for access to other .deb files. Comaptibility of these packages might be a problem.

---

### Post by doas777 on 2009-04-26
i'm sorry i need to clarify. I havn't had any of the serious problems the op mentions (at least not regularly, though it did crash twice playing dvds last night). it has always opened a control window separately from the video window, by default. on numerous versions of windows and ubuntu. 

vlc is a pretty good viewer so i hope you get it worked out.
you may wanna try 'sudo apt-get install vlc --reinstall' to see if that helps.

---

### Post by MrWES on 2009-04-26
> **jmmL said:**
> It's fixed in Kow's PPA: [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

That version also has support for VDPAU, if you have a nVidia card and are interested.

Thanks for the link - worked perfectly!

Bill

---

### Post by llamabr on 2009-04-26
It sounds like something you can resolve by messing with your config file.

But why install from the website.  Any reason not to install from repositories?  You always minimize future problems and inconsistencies when using the native package manager.

---

### Post by Messyhair42 on 2009-04-27
> **jmmL said:**
> It's fixed in Kow's PPA: [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)


I looked at the site and it didn't make much sense to me. what will enabling a PPA do for me?

---

### Post by Messyhair42 on 2009-04-27
I went through the walkthrough here [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683") and set VLC as my default DVD player, but is there a way to set it as the default player for files like .avi, .mkv, .mp3 and so on?
also i couldn't get the version from intrepid through the method benerivo suggested, is there another way to get video and controller in one window so i can have hover controls in fullscreen? i even tried changing the skin and it looks exactly the same.

---

### Post by oldos2er on 2009-04-27
Right-click on a file (avi, mp3, whichever you want to open with vlc), Properties, Open with.

---

### Post by jmmL on 2009-04-27
> **Messyhair42 said:**
> I looked at the site and it didn't make much sense to me. what will enabling a PPA do for me?

PPA stands for Personal Package Archive. It's basically a very small repository with only a few files in it, chosen by whoever maintains that PPA (Kow, in this case). They rely on a certain degree of trust - I don't know the maintainer personally. What I'm trying to say is don't go installing files from any old source, but I found out about this from the jaunty-testing sub-forum, so that's trustworthy enough for me.

Back on track: once you've enabled the PPA, you can then run:
```

sudo apt-get update
sudo apt-get upgrade
```It should then prompt you to upgrade VLC and probably a package called x264, or something like that. You can of course do this through any package manager you like.

To actually enable the PPA you'll want to go to System > Admin > Software Sources and add the line ```
deb [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
```The version currently packaged by Kow is much more up-to-date than available in the main repos. It also fixes the compile-time error that means that the player and controls are in separate windows.

Anything else?

---

### Post by Messyhair42 on 2009-04-27
it worked, had to run update a couple of time b/c i got errors the first time, thanks all. stuff like this is why i use Ubuntu and love the forums

---

### Post by Messyhair42 on 2009-07-08
bringing this back up again because i reinstalled jaunty on a new HD. enabled the Kow repositories and updated, now VLC wont launch at all.

---

### Post by mc4man on 2009-07-08
While i don't use jaunty nor a ppa for vlc maybe try starting up with this from a terminal and see
```
vlc --reset-config --reset-plugins-cache
```

(also note that the 1.0 version released, I'd expect that ppa to update shortly from the rc4 version

---

### Post by Arup on 2009-07-08
The right ppa for vlc is C.Korn's at [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc) 

The VlC package there was updated within hours of announcement of VLC final by Video LAN.

---

### Post by Messyhair42 on 2009-07-08
changed the PPA source and still doesnt work. I went through the multimedia steps to set vlc as default player. when i do get it working i'm aiming for one window with hovering controls rather than two separate windows.

---

### Post by mc4man on 2009-07-08
Don't know if you tried command i suggested or not, would also suggest you open synaptic, search vlc and make sure that the 5 main vlc packages are **all the same version**

vlc, libvlc2, vlc-data, vlc-nox and most importantly libvlccore2 (if there is a libvlccore0 remove it (or remove all vlc packages/plugins and then reinstall. (and do a first run start w/ sugg. command or add -vv for add. info
ex.
 vlc --reset-config --reset-plugins-cache -vv

---

### Post by Messyhair42 on 2009-07-08
worked like a charm, was a mix of 1.0.0.0 and .9.9 packages because of the PPA. reinstallation worked great, except now my packages do not include libvlccore2. do i have to worry about new updates and keeping C.Korn's PPA?

---

### Post by mc4man on 2009-07-08
> do i have to worry about new updates and keeping C.Korn's PPA?No real issue one way or the other, you could uncheck the ppa's source in 3rd party apps or just leave. (any upgades from the same ppa will install cleanly.

(if you ever change repo's, ppa's or versions the usually best to remove completely first and then clear the config  and cache on first start

any update would be a positive (the majority of times

There are still improvements and possibly some fixes of small bugs, regressions

(( The command I gave you is always a good first step in case vlc starts misbehaving


Edit
> now my packages do not include libvlccore2

That would seem very odd if you are running jaunty and installed vlc 1.0

This is the list of the 5 main packages from that ppa for 9.04 (jaunty i386

```
libvlc2_1.0.0-1~ppa3_i386.deb      vlc-data_1.0.0-1~ppa3_all.deb
libvlccore2_1.0.0-1~ppa3_i386.deb  vlc-nox_1.0.0-1~ppa3_i386.deb
vlc_1.0.0-1~ppa3_i386.deb
```

---

### Post by Messyhair42 on 2009-07-10
i upgraded to 1.0 as a part of my migration. but now when i watch in fullscreen, whenever i move the mouse, causing the cursor to appear (or disappear after it times out) the screen flickers for a moment (one frame? more?) anybody else have this problem?

edit: i've discovered that moving the mouse causes the screen to go transparent for a moment, so i see my desktop, even if other windows are open behind VLC.

---

### Post by Messyhair42 on 2009-07-17
is there a fix for this? or is this instance unique?

---

### Post by mc4man on 2009-07-17
> is this instance unique? 

Absolutely not

I had jaunty for a short time and while it wasn't the one of the more significant issues /reasons while i dumped it, it was annoying, (nvidia adapter on a laptop

I can't remember if I resolved it other than the unacceptable method which will work (disable compiz

(I do think there may have been a solution involving something in compiz settings
Maybe I'll boot up a jaunty live cd later, enable the restricted drivers and see.

What's your video adapter? ( sudo lshw -C display and or glxinfo | grep render

Edit:
from the jaunty live cd, the restricted nvidia 180 drivers enabled, the flashing in vlc's fullscreen mode was solved by opening CompizConfig Settings Manager and under General options unchecking the  "Unredirect Fullscreen Windows"

If you don't have System -> Preferences -> CompizConfig Settings Manager then search compiz in synaptic and you'll find it there to install

---

### Post by Messyhair42 on 2009-07-17
```
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

```

also within CCSM i didn't find "Unredirect Fullscreen Windows," maybe it's my version but it might be called something else.

---

### Post by mc4man on 2009-07-17
ck. screens, opened from System -> Admin... -> Preferences -> CompizConfig Settings Manager

For those commands 
```
sudo lshw -C display
```
```
glxinfo | grep render

```

---

### Post by Messyhair42 on 2009-07-18
> **mc4man said:**
> Absolutely not

I had jaunty for a short time and while it wasn't the one of the more significant issues /reasons while i dumped it, it was annoying, (nvidia adapter on a laptop

I can't remember if I resolved it other than the unacceptable method which will work (disable compiz

(I do think there may have been a solution involving something in compiz settings
Maybe I'll boot up a jaunty live cd later, enable the restricted drivers and see.

What's your video adapter? ( sudo lshw -C display and or glxinfo | grep render

Edit:
from the jaunty live cd, the restricted nvidia 180 drivers enabled, the flashing in vlc's fullscreen mode was solved by opening CompizConfig Settings Manager and under General options unchecking the  "Unredirect Fullscreen Windows"

If you don't have System -> Preferences -> CompizConfig Settings Manager then search compiz in synaptic and you'll find it there to install

solved!

---

### Post by swong on 2009-07-19
> **jmmL said:**
> It's fixed in Kow's PPA: [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

That version also has support for VDPAU, if you have a nVidia card and are interested.

If the card does not support VDPAU (like mine which is a Geforce 7600GT), does it mean the video decoding is offloaded to the cpu?

---

### Post by swong on 2009-07-19
Never mind, I guess it does offload the work to the cpu.  Just tried running a H.264 1080p trailer, and the cpu usage did go up.

Seems I was misinformed previously, it seems hardware acceleration and video acceleration are two different things, I guess I'll upgrade to a better gpu next time.

---

### Post by Messyhair42 on 2009-08-14
my VLC has gotten glitchy, nothing big, but i get a line than moves up the screen every so often, its like the top part and bottom part of the screen are playing different frames because i notice a difference in the position of a moving shot (this happens with DVD as well as video files). also i get subtitles overlapping, sometimes the subtitles stay onscreen longer than they're supposed to and the next line is displayed on top of it. anyone else experiencing this? hardware problem or should an update fix it soon?

---

