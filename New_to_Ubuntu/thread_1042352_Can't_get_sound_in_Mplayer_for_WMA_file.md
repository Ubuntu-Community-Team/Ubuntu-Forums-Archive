---
title: "Can't get sound in Mplayer for WMA file"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Sugi on 2009-01-17
As the title says, no sound in either mplayer or totem.  Totem just won't play the file together.

```
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll
IMediaObject ERROR: 0x88abfc9  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wma9dmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmadmod.dll, /usr/lib/win32/wmadmod.dll, /usr/local/lib/win32/wmadmod.dll
IMediaObject ERROR: 0x88abfc9  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmadmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...

```

Sugi

---

### Post by ibuclaw on 2009-01-17
You could perhaps look at gstreamer-ugly plugins or enabling the medibuntu repository for the wma codecs.

Have a look at this thread here: [Comprehensive Multimedia & Video HowTo]("http://ubuntuforums.org/showthread.php?t=766683")

Regards
Iain

---

### Post by cwsnyder on 2009-01-17
You may also try VLC media player.  I have had better luck even after codecs are loaded using VLC for Flash and Windows media files.

---

### Post by Sugi on 2009-01-17
I'll check that out.  BTW, the audio was encodec with WMA 10 pro.

Sugi

---

### Post by seagullplayer77 on 2009-01-17
You can try the Medibuntu repos and see if you can get WMAs working that way, although I've never been able to play WMA files with Ubuntu, no matter what I've tried. It's a proprietary Windows codec, so it's not really surprising that the Linux support for it is sketchy at best.

I gave up on WMAs a while ago and I use FLACs exclusively now. If your whole librarty is in WMAs already, though, then I imagine it would be tedious to convert everything to another format :-).

---

### Post by Sugi on 2009-01-17
> **tinivole said:**
> You could perhaps look at gstreamer-ugly plugins or enabling the medibuntu repository for the wma codecs.

Have a look at this thread here: [Comprehensive Multimedia & Video HowTo]("http://ubuntuforums.org/showthread.php?t=766683")

Regards
Iain

Will this conflict with my ubuntu restricted extras?

Sugi

---

### Post by Sugi on 2009-01-17
Sorry, the file in question is a video WMA file, but I have been able to play WMAs file before, but this one is special.  The video file was encoded with WMA 10 Pro.

I am unable to find mediubuntu and I have ubuntu-restricted-extras installed.

Sugi

---

### Post by cwsnyder on 2009-01-17
If you have been able to play video WMAs before, the only suggestion I have is to try VLC.  If I cannot get a video or audio file to play in anything else (Windows or Ubuntu), I can still usually get VLC to play it.

---

### Post by ibuclaw on 2009-01-17
> **Sugi said:**
> Sorry, the file in question is a video WMA file, but I have been able to play WMAs file before, but this one is special.  The video file was encoded with WMA 10 Pro.

I am unable to find mediubuntu and I have ubuntu-restricted-extras installed.

Sugi

Medibuntu is a repository, not a package.
What version of Ubuntu are you running?
```
uname -a
```

Regards
Iain

---

### Post by Sugi on 2009-01-17
Ubuntu Hardy Heron 2.6.24-21 i686

Sugi

---

### Post by andrew.46 on 2009-01-17
Hi,

There could very well be a problem there as even the full codec pack from MPlayer may not support this:

```
andrew@skamandros:~$ mplayer -ac help | grep -i wma
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]
divx        acm       working   DivX audio (WMA)  [divxa32.acm]
ffwmav1     ffmpeg    untested  DivX audio v1 (FFmpeg)  [wmav1]
ffwmav2     ffmpeg    untested  DivX audio v2 (FFmpeg)  [wmav2]

```

Andrew

---

### Post by ibuclaw on 2009-01-17
> **Sugi said:**
> Ubuntu Hardy Heron 2.6.24-21 i686

Sugi

To quote from the link I gave earlier:
Get the medibuntu sources
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Add the GPG key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Install the essential packages for Audio/Video playback (and other non-free things)
```
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```
Then try playing it.

Regards
Iain

---

### Post by Sugi on 2009-01-17
tinivole, thanks.  The link was a bit overwheling and I didn't have the time to try it.  But I will follow those steps now.

tinivole
Installed everything.  Testing now...
EDIT:  Awesome. the medibuntu did the try.  Thanks. the sound is off by a second,  but that may be a issue on my behalf.  I'll report back with any new news.  Thanks everyone for the help. :D

andrew.46,
after installing medibuntu...
mplayer -ac help | grep -i wma

wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]
divx        acm       working   DivX audio (WMA)  [divxa32.acm]
ffwmav1     ffmpeg    untested  DivX audio v1 (FFmpeg)  [wmav1]
ffwmav2     ffmpeg    untested  DivX audio v2 (FFmpeg)  [wmav2]



Sugi

---

### Post by andrew.46 on 2009-01-17
Hi Sugi,

> **Sugi said:**
>  Awesome. the medibuntu did the try.  Thanks. the sound is off by a second,  but that may be a issue on my behalf.  I'll report back with any new news.  Thanks everyone for the help. :D

Great news! If sound and video are a little apart try using the + and - keys to adjust during playback. Not a final solution but it may help a little.

Andrew

---

### Post by Sugi on 2009-01-18
Thanks,  that's odd I would think the + or - would adjest the timer of the playback.  THanks for the tip, ill try it.

Sugi

---

### Post by cwsnyder on 2009-01-23
I was just checking my videos transferred from Windows XP, and I have the opposite problem:  Using MoviePlayer or VLC, the Windows WMV files do not show any video, just play the audio track.  Yes, I have Medibuntu repository enabled.

So I think it is a problem with the codecs not supporting WMA video or WMV video.  Of course, that is why I keep a Windows partition or Virtual Machine enabled.;)

---

### Post by Sugi on 2009-01-23
I also have a windows partition laying around on my computer.  It sucks, 40 gigs gone to waste.  I installed Windows and then my Linux partition.  I have not booted into my windows partition since the installation, I don't even have drivers on my windows partition. >.<

  Point being, You should not have to keep a windows partition for such a simple need, video playback.  Have you check the video file it's self?  Make sure its not a badly encoded file.  Fire up your video player within the terminal and post your output of the failing video file.

Sugi

---

### Post by cwsnyder on 2009-01-29
The problem was my audio drivers.  I fixed the audio drivers by using the directions on [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and audio is back.  Audacity from the Ubuntu repositories seems to have been what killed my video sound.

---

### Post by jastonas on 2009-12-18
I have a file encoded with wm 10 pro and the audio will only play with mplayer. Totem and vlc have only video.
I have installed almost any codec i could find. All gstreamer. W32codecs. Restricted-extras.
Now i am looking into the idea of installing the commercial fluendo pack..

---

