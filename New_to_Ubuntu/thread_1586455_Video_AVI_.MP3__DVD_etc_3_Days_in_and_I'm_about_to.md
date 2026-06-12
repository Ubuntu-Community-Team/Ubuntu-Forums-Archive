---
title: "Video AVI .MP3  DVD etc 3 Days in and I'm about to"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by QuietOne on 2010-10-02
This is my 2nd attempt at a Linux version.  3 years apart ... 

I'm not a geek I don't want to be geek. I want to use the computer. 

10.04.01 everything seems to work but no video player I've loaded works correctly. Totem if I tried to resize or move or advance or pause or ... would black out. 

No other video player plays at all. 

Someone please walk me through how to find out what is wrong and how to fix it.

How do I identify my graphics card on board HP P4 and know if it is running correctly? 

Is there not a easy way to search these forums? 

I know now why Linux isn't catching up, it shouldn't take 3 days to get farther behind.

---

### Post by jtarin on 2010-10-02
This your first post to the forums....if you would have posted three days ago you would be that much further ahead. Video player....try starting the player from the termianl by entering the name of the playe and hit enter...example ```
totem
```post your results from the terminsl here.

---

### Post by QuietOne on 2010-10-02
dwade@dwade-desktop:~$ totem
dwade@dwade-desktop:~$ 

The player opens, I can start to play an avi but if I go to full screen, or try to reposition it the player screen goes black. I have to start again and on it goes.

---

### Post by QuietOne on 2010-10-02
mplayer in terminal window

desktop:~$ mplayer
mplayer: relocation error: mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

---

### Post by fly-by-night on 2010-10-02
The best video player in my opinion is VLC.  It plays just about everything.

To search this site with google ```
site:ubuntuforums.org vlc
```Leave a space between the site URL and the words you want to search.

---

### Post by QuietOne on 2010-10-02
vlc has the same issue as totem plays video, avi/mpg etc but If i grab the window and move it, resize it, or touch it in anyway the view goes BLACK.

from terminal the program opens but....

-desktop:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x86b267c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb757d0d4, 0xb757d048)
Warning: call to signal(13, 0x1)
Warning: call to srand(1286328548)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3190): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()

CVLC gives

-desktop:~$ cvlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x91dc304] dummy interface: using the dummy interface module...

Above does not bring up the program

---

### Post by jtarin on 2010-10-02
Disable Compiz (special effects) and try.

---

### Post by NightwishFan on 2010-10-02
If that does not work do one of the following (for the player you want):
[LIST]
[*]**For Totem**: Press Alt+F2 and type: ```
gstreamer-properties
``` A window should come up that says Audio/Video. Go to Video -> Default Output and choose Plugin: X Window System (No X). This will improve reliability at the expense of some performance. On good hardware it will not matter.
[*]**For Mplayer**: Chose X11 Video as output under Video Preferences.
[*]**For VLC**: Choose X11 Video as output under Tools -> Preferences -> Video.
[/LIST]

If this does not help, change anything back to the default. (usually xv/xvideo)

---

### Post by QuietOne on 2010-10-02
Disable compiz?

---

### Post by QuietOne on 2010-10-02
changing properties with 

gstreamer-properties 
didn't do anything, still goes black on resize, move, minimize and expand etc

---

### Post by jtarin on 2010-10-02
> **QuietOne said:**
> Disable compiz?
Disable compiz window manager - Go to System -> Preferences -> Appearance, click on the Visual Effects tab and select None.

---

### Post by QuietOne on 2010-10-02
Turned off compiz

Totem, I was able to play an mpg and the screen didn't go black while resizing it, was able to advance etc. but does not play any other format at all

Open with terminal window  via command 
-desktop:~$ totem
Segmentation fault

Mplayer not working at all
-desktop:~$ mplayer
mplayer: relocation error: mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

VLC but it will play avi and mpg does have issues seems like slow motion and jerky at times

-desktop:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x9d3e67c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb74ce0d4, 0xb74ce048)
Warning: call to signal(13, 0x1)
Warning: call to srand(1286389181)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:1859): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()

---

### Post by jtarin on 2010-10-02
Is this installation of Ubuntu a WUBI install?

---

### Post by jtarin on 2010-10-02
> VLC media player 1.1.4 The Luggage (revision exported)
That's not a stable build it still has bugs. I would advice an uninstall and use the version from the repositories.
vlc-1.0.6-1ubuntu1.2 it works where the other doesn't.
[Installation documentation]("http://www.videolan.org/vlc/download-ubuntu.html")

---

### Post by QuietOne on 2010-10-02
WUBI???

I downloaded the ISO from Ubuntu, burned it and installed it. Other than this issue of playing video I'm amazed at how easy it has been, but if it won't play video I'll drop it.

---

### Post by QuietOne on 2010-10-02
> **jtarin said:**
>  ....   vlc-1.0.6-1ubuntu1.2 it works where the other doesn't.
[Installation documentation]("http://www.videolan.org/vlc/download-ubuntu.html")

I can't seem to find that version with synaptic package manager

is there a specific repository I have to add, never having added one this could be interesting.

---

### Post by jtarin on 2010-10-02
> **QuietOne said:**
> I can't seem to find that version with synaptic package manager

is there a specific repository I have to add, never having added one this could be interesting.The link I gave you has this information....your right...this could be interesting.

---

### Post by QuietOne on 2010-10-02
nothing I do brings up anything other than the 1 version

I've read and re-read the instructions at [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) but it never says what to add to the existing list...    or am I really missing something basic

---

### Post by jtarin on 2010-10-02
Software Sources....checked
Synaptic.....ver-1.06 installed

---

### Post by jtarin on 2010-10-02
> **QuietOne said:**
> nothing I do brings up anything other than the 1 version
You need to uninstall your old version completely.

---

### Post by QuietOne on 2010-10-02
not knowing how to insert a picture from my desktop it is an attachment

only the 1 version of vlc shows up

---

### Post by migs73 on 2010-10-02
> **QuietOne said:**
> 

I know now why Linux isn't catching up, it shouldn't take 3 days to get farther behind.

99% or so of people who buy a computer, do so with windows already installed by the manufacturer. If you bought a PC with Ubuntu already installed you wouldn't have any problems either. 
The people on this forum are one of the most powerful facets of Ubuntu, and will bend over backwards to help you out.

Now, get a PC with no OS and no driver disks and try putting windows on it. 3 days? Good luck.

---

### Post by migs73 on 2010-10-02
> **jtarin said:**
> Is this installation of Ubuntu a WUBI install?

By this jtarin wants to know if this is a standard install or if it was done from within windows (WUBI). If you were running windows, put the disk in then followed the instructions it will probably be WUBI. If you had the disk in, rebooted from the CD and then selected install, then it will be a true Ubuntu install.

---

### Post by andrew.46 on 2010-10-02
Hi Quiet,

> **QuietOne said:**
> only the 1 version of vlc shows up

You have added in a PPA at some stage which is giving you this version of vlc and perhaps other software as well. Which PPA is this?

Andrew

---

### Post by jtarin on 2010-10-02
As andrew.46 has reported looking at you attachment it shows your installed version of VLC coming from a source you have added...a ppa repository. You will have to remove that to be able to downgrade.

---

### Post by QuietOne on 2010-10-02
> **migs73 said:**
> 99% or so of people who buy a computer, do so with windows already installed by the manufacturer. If you bought a PC with Ubuntu already installed you wouldn't have any problems either. 
The people on this forum are one of the most powerful facets of Ubuntu, and will bend over backwards to help you out.

Now, get a PC with no OS and no driver disks and try putting windows on it. 3 days? Good luck.

I can install XP Pro on a WIDE variety of machines but it takes about 6-8 hours, maybe more depending on the machine. That's a bare machine with nothing, no hard drive, no memory, this is from a XP Pro Full Enterprise setup. The worst installations I've hit are for Dell. 

It may require basic video and network cards to get going but once it hits the net Windows goes. 

Don't get me wrong I'm very impressed with Ubuntu 10.04 from an install point. I've put it on 3 different machines from legacy 5 year old to bought last week, just to see what it will do. In 45 minutes Ubuntu was on the net and the only glitch I have is with video so yes it is impressive but without video.. avi, mpg, dvd and so on it is not going to be my every day machine. 

I don't want to use Windows I personally can not afford multiple licenses.  So if I can get this working I have 30 HP boxes I can install Ubuntu on and donate to the schools or individual students. 

Ubuntu is getting closer to being a prime system I'd say not just yet though.

---

### Post by QuietOne on 2010-10-02
I didn't install any PPA (personal package archives, yes I had to look it up to know what the heck it is) I don't have clue still what it is or what it does where it came from or if I need it. I can't even identify it from the listing I have so .....

I'm a total novice with Linux and more so with Ubuntu so everything I'm advised of I have to look up and investigate.

---

### Post by NightwishFan on 2010-10-02
It sounds like something is not installed right. Totem should not just seg-fault trying to play a video. Did you install 3rd party ppas or anything?

---

### Post by jtarin on 2010-10-02
Synaptic>settings>repositories>other software(tab) will show ppa's

---

### Post by QuietOne on 2010-10-03
vlc terminal plays mpg files apparently just fine


gives the following on exit
desktop:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x89f9668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
swScaler: pal8 is not supported as output pixel format
[0x8eebbe8] swscale scale error: could not init SwScaler and/or allocate memory
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
QPainter::begin: Paint device returned engine == 0, type: 1
[0x8ed2c60] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8ed2c60] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

vlc and avi....

desktop:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x8fe0668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Segmentation fault

---

### Post by diablo75 on 2010-10-03
I just noticed you started this thread a day ago and it's still going.  If I were you, I'd start over.  You said yourself, you don't want to be a geek; you just want to use your computer.

So use the Live CD you installed with to delete the partitions from your drive and install fresh.

Next, after installing, run **System>Administration>Update Manager**, check for and install all available updates and restart.

Then, check **System>Administration>Hardware Drivers** and enable proprietary drivers if it makes any available for you.

Then, click **Applications>Accessories>Terminal** and type in:

```
sudo apt-get install vlc
```

While you're at it you might as well install some other fun stuff, like video decoders...  So lets make that command:

```
sudo apt-get install vlc ubuntu-restricted-extras
```

This will install VLC along with some (but not every imaginable) video and audio decoder as well as some other plugins for Firefox.  There are more decoders available from the [Medibuntu]("http://medibuntu.org/") repositories.

The video-blacking at fullscreen and slow performance issues you are having quite possibly has to do with using slightly out-of-date drivers.  It could factor in if the video card you are using is so new that "proper" drivers for it have yet to be released by either the manufacture or the open source community (depending on the kind of card being used).  Updating your system and enabling proprietary drivers as mentioned earlier might clear all this up.

---

### Post by anewguy on 2010-10-03
+1 on ubuntu-restricted-extras

I can't remember if it directly installs the decryption or not - someone may know that off the top of the head.

Hang in there!  You're actually quite lucky if this is the major problem you are having.  Seems we've had a lot of people who have needed help with video and wireless drivers yet, though that it getting better.

Dave ;)

---

### Post by diablo75 on 2010-10-03
> **anewguy said:**
> +1 on ubuntu-restricted-extras

I can't remember if it directly installs the decryption or not - someone may know that off the top of the head.

If you're refering to libdvdcss2 (DVD Decoder), it does not.  It does install a decoder for use with unencrypted MPEG2 streams (found on homemade DVDs or non-commercial DVDs) but commercial DVDs require libdvdcss2 to play.  It can be installed via the Medibuntu repositories.  In fact if you wanted to do that with just one command it would be this:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install libdvdcss2
```

In addition there is the w32codecs package (or the w64codecs for 64-bit installations) that you can also install after adding the above repository with that command.  So after you do the above, you can just type:

```
sudo apt-get install w32codecs
```

or

```
sudo apt-get install w64codecs
```
(for 64-bit installs)

And it will add in additional decoders for some other proprietary file formats.

---

### Post by anewguy on 2010-10-03
Yep, that's what I was referring to.

Dave ;)

---

### Post by QuietOne on 2010-10-03
after a total reinstall from cd

I have exactly the same issues.

VLC is 1.06 and it behaves much poorer will not play avi's at all

segmentation error

with mpg I have no sound

and it gives

-Desk:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x81b0148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)

only now it is worse than before in that nothing play correctly

plus totem gives 
# no audio *(umpteen times*)
# no audio
(totem:2740): GStreamer-CRITICAL **: _gst_util_uint64_scale_int: assertion `denom > 0' failed

So yes it is worse

---

### Post by NightwishFan on 2010-10-03
Try this: (Source: [http://ubuntuforums.org/showpost.php?p=7795674&postcount=3](http://ubuntuforums.org/showpost.php?p=7795674&postcount=3))
> open vlc via application menu. go to tools>preferences and uncheck embed video in interface. should solve your problem.

Might be a different problem thought as a corresponding bug report named this fixed. VLC uses a different playback engine than Totem, so if there is a problem with both it might be graphics related. Though again, if that was the case, switching them to x11 video and not xvideo would solve the problem, and it appears it did not.

---

### Post by nikefalcon on 2010-10-03
Seems you are using kernel 2.6.34 or lower. Its known to have issues with some intel graphics cards.  try upgrading to the maverick backport kerne from a PPA.

[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

hope this helps, 
good luck

---

### Post by QuietOne on 2010-10-03
> **nikefalcon said:**
> Seems you are using kernel 2.6.34 or lower. Its known to have issues with some intel graphics cards.  try upgrading to the maverick backport kerne from a PPA.

[https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

hope this helps, 
good luck

You are way way past my skill set .. so Ubuntu does not upgrade itself???   

I have to update this thing daily?

---

### Post by jtarin on 2010-10-03
It's seems we have failed to get information about your system.
Let's do that now. Open a terminal and enter the command ```
lspci 
```then post the results here. You can copy and paste from the terminal.

---

### Post by d5xtgr on 2010-10-03
> **QuietOne said:**
> You are way way past my skill set .. so Ubuntu does not upgrade itself???   

I have to update this thing daily?
The 'maverick' (10.10) version hasn't actually been released yet (next Sunday, it will).  You wouldn't want to automatically upgrade to an incomplete/unstable version, would you?

Depending on your settings, you will probably be informed about new releases and have the option to change to them if you so choose, or possibly only other long-term versions.  Find out under System/Admin/Update Manager and click settings.

---

### Post by Bradtek on 2010-10-03
**Have you or have you not installed the CODECS ?**

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install w32codecs
```

Can't believe it took till page 4 for someone to suggest this

---

### Post by NightwishFan on 2010-10-03
That is probably not the issue, especially with VLC. :)

Edit: Yay less than 100 to go until I can change my title.

---

### Post by jtarin on 2010-10-03
> **Bradtek said:**
> **Have you or have you not installed the CODECS ?**
Can't believe it took till page 4 for someone to suggest this
Lack of codecs is not a reason for segmentation fault.....which has been the problem.

---

### Post by andrew.46 on 2010-10-03
Hi NightwishFan,

> **NightwishFan said:**
> That is probably not the issue, especially with VLC. :)

Indeed, as to utilise these codecs vlc must be compiled with the *--enable-loader* option and I believe that this is rarely if ever done in PPAs, Ubuntu Repositories etc.

> Edit: Yay less than 100 to go until I can change my title.

Is that at 3,500? D'oh!!! I only looked after 4,000 :(.

Andrew

---

### Post by nc_jed on 2010-10-03
> **QuietOne said:**
> ... So if I can get this working I have 30 HP boxes I can install Ubuntu on and donate to the schools or individual students.

Don't get me wrong, I applaud what you want to do, but just an observation.  Who will these thirty schools/students call when they also cannot get .avis to play correctly?

- nc_jed

---

### Post by jtarin on 2010-10-03
> **nc_jed said:**
>  Who will these thirty schools/students call when they also cannot get .avis to play correctly?
- nc_jed
Ubuntu-busters????:P

---

### Post by nc_jed on 2010-10-03
> **jtarin said:**
> Ubuntu-busters????:P

Nah, they'll be able to bust it all by themselves...

---

### Post by QuietOne on 2010-10-04
-Desk:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)

---

### Post by QuietOne on 2010-10-04
> **Bradtek said:**
> **Have you or have you not installed the CODECS ?**

```
sudo apt-get install ubuntu-restricted-extras
``````
sudo apt-get install w32codecs
```Can't believe it took till page 4 for someone to suggest this

Done a page or so back but thanks for the suggestion

---

### Post by QuietOne on 2010-10-04
> **nc_jed said:**
> Don't get me wrong, I applaud what you want to do, but just an observation.  Who will these thirty schools/students call when they also cannot get .avis to play correctly?

- nc_jed

If I can't get this test machine to run properly they will never see the machines, they will go to the local landfill.

---

### Post by NightwishFan on 2010-10-04
Try upgrading to a newer intel driver, run these in order:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by QuietOne on 2010-10-04
Did all three.

vlc from terminal window

Avi

-Desk:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x9979148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Segmentation fault

Mpg while plays has no audio.  On close gives
esk:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x8930148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8cf3eb8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture

---

### Post by NightwishFan on 2010-10-04
Last thing I can think of is to install the backport Maverick kernel.
Source: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Using%20Maverick%20Kernel](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Using%20Maverick%20Kernel)

Run these:
```
sudo add-apt-repository ppa:kernel-ppa/ppa
```
```
sudo apt-get update && sudo apt-get install linux-generic-lts-backport-maverick
```

Reboot.


Note: If you want to get rid of packages added with any of these ppas I suggested. (Especially if they did not help) I can help you do that. The following method will work but I can answer any questions.
[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/)

---

### Post by jtarin on 2010-10-04
Not much hope with that machine unless you boot in vesa mode.
[Bad news early on with no recent progress]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4#Installing the package").

[Not saying it can't be done]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance").

---

### Post by QuietOne on 2010-10-04
After running the backport

VLC gives the same error with avi's 
dwade-Desk:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x95af148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Segmentation fault

MPG's play but there is no sound  

VLC is not giving an error message 

Just no sound 

Now totem is a different kettle

it's worse.. but I have a udio though the video playback is all jerky and slow 

I get this
dwade@dwade-Desk:~$ totem
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio (for a long time)


The back porting doesn't seem to have made any detrimental changes that I have encountered. Should I leave it or remove the back porting of maverick?

I do hate to give up on Ubuntu due to this issue being unsolvable, I find it great that the OS installs in less than 45 mins and takes 23 seconds to boot

---

### Post by NightwishFan on 2010-10-04
I would remove the backport. Though such an issue baffles me. Could you upload your /var/log/syslog here? Also try what a previous poster suggested, use the vesa driver. How to:
Source: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Workaround%20B:%20Switch%20to%20-vesa](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Workaround%20B:%20Switch%20to%20-vesa)

Run:
```
sudo nano /etc/X11/xorg.conf
```

Paste this into the file 
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Press ctrl+x, then y to save. Then reboot. If it complains about file not found, you will have to do this manually by:

Press alt+f2 and type:
```
gksudo gedit /etc/X11/xorg.conf
```

Then paste the text above into the file. Reboot.

To revert back to the normal driver just run:
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by QuietOne on 2010-10-04
purge doesn't work
~$ sudo ppa-purge ppa:ubuntu-x-swat
[sudo] password for XXXXX: 
sudo: ppa-purge: command not found


and where would I find /var/log/syslog 

and _***HOW ***_of course, this is really over extending my skill set

---

### Post by NightwishFan on 2010-10-04
No it is quite simple. Just select "File System" on the side when prompted to upload or in the file browser. Then go to the folder /var/log. However that is optional, as I might not find anything useful anyway. :(

Also ppa-purge is not installed by default. Here is a link to the program: [https://launchpad.net/~xorg-edgers/+archive/ppa/+files/ppa-purge_0.2.7%7Elucid_all.deb](https://launchpad.net/~xorg-edgers/+archive/ppa/+files/ppa-purge_0.2.7%7Elucid_all.deb)

I am sorry I can not be of help. Though if the issue is at all graphics related, using vesa will fix it at the cost of being very slow with anything 3d.

---

### Post by QuietOne on 2010-10-05
When I try to attach the log files, I have two syslog and syslog1 the attacher says invalid file so that apparently is out.

The vesa thing I'd try but this is beyond me. I couldn't find it to open it to view much less edit it. 

I;m going to go through my collection of PCI video cards and see what I have and then see if any are compatible. Though I doubt it as they are all old ATI cards. The two I have looked at to now aren't and off course I have lots of those.

Is there a video card compatibility list somewhere? Cards that Ubuntu actively recognizes, not cards that need code added to?

---

### Post by NightwishFan on 2010-10-05
For vesa I listed the necessary commands. As for attaching the file, yes, it is a bother you have to open it and re-save it as .txt on your desktop.

---

### Post by jtarin on 2010-10-05
> **QuietOne said:**
> purge doesn't work
~$ sudo ppa-purge ppa:ubuntu-x-swat
[sudo] password for XXXXX: 
sudo: ppa-purge: command not found


and where would I find /var/log/syslog 

and _***HOW ***_of course, this is really over extending my skill setThe learning process is possible in the higher orders of animals by their ability to  
over extend their skill sets.

---

