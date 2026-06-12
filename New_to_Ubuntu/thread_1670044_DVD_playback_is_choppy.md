---
title: "DVD playback is choppy"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by maryalesia on 2011-01-18
I'm having trouble with screen tearing and general choppiness during DVD playback. I installed libdvdcss2 or something in order to get them playing at all, but it isn't exactly smooth. 

I tried ripping them and then playing the ripped file, but it's still choppy / laggy. 

Is there another package I need to download? I've been using VLC.

---

### Post by gordintoronto on 2011-01-18
It sounds like a performance issue. How fast is your computer? What video adapter? Do you have a proprietary video driver installed? What version of Ubuntu?

You might try Totem, which is probably called "Movie Player" under Sound & Video. Some people install another program, called SMPlayer.

---

### Post by diacad on 2011-11-16
Like many others, I am also having choppy DVD playback problems with a configuration that may be a bit "behind the times", but would play the DVDs smoothly under Windows XP.  If Ubuntu cannot play video as well as XP on an equivalent hardware configuration, then that is really a major black mark against it.
 
I think it is reasonable to use WinXP as a benchmark when assessing Ubuntu, since its backers constantly suggest its use as a viable alternative.
 
The configuration is Athlon XP +2200 with 512 Mb RAM and GeForce4 440 64 Mb AGP, running  Ubuntu 10.4, fresh install.  The proprietary nVidia driver is not used, as it is only capable of 640x480 resolution, which is ridiculous.  Apparently, a good proprietary nVidia driver is not available for the older cards (most anything below a 6200) - the open source driver loaded by default is the best that can be expected.  Or if not the graphics card, what is the weak link?
 
Youtube playback is also choppy, but not as bad as DVD video.
 
Since people expect a computer to play video these days, I am afraid that Ubuntu may not be the solution often touted for rescuing XP class computers from the dump.  Unless there is a clear answer to this video playback problem.  Please, some guru out there, if you know some definite fix, tell us about it.

---

### Post by beew on 2011-11-16
@diacad

It seems to be a  driver issue. I try the latest open source nouveau driver (through xorg-edgers) on some newer Nvidia machines and it works great, but unfortunately support for old cards isn't that great either. I have an old Dell Inspiron with a Geforce 4200 card, the  nouveau drivers bundled with 10.04 and 11.04 didn't work  at all , can't even read the screen without the graphics all screwed up--the nvidia driver did work though, at least for 10.04, don't know if the diver is still supported by Nvidia in later Ubuntuss. With the Nvidia driver the Dell works as well as XP even with Compiz on,--which is not great but xp freezes a lot too if watch videos,-- with openbox it is definitely faster than  XP.

Since you have a weak machine Ubuntu may not be the best choice, Lubuntu would work much better on a machine with that kind of specs.  Also flash is resource demanding, even more so the Linux version. If you have an old or weak machine flash is a really bad idea. There are ways to watch Youtube without flash. Try install minitube from ppa (the Ubuntu 10.04 version is broken and very outdated), or use the flashvideoreplacer addon for Firefox,--need to install gecko-mediaplayer from repo as well,-- it works on a few sites beside Youtube, disadvantage is that it needs to use Firefox so it is still resource intensive during streaming comparing to minitube.

Minitube ppa

[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

---

### Post by Linuxisfast on 2011-11-16
Video drivers need to be installed, in case of nvidia, you need vdpau files installed as well. Then in vlc, enable GPU acceleration for inputs and codecs. For ATI cards and Intel, apart from drivers, xvba-va driver needs to be installed. On my puny little ASUS 10" Netbook with integrated ATI 6250, HD movies play with no choppiness either via HDMI or its built in screen.

---

### Post by beew on 2011-11-16
> **Linuxisfast said:**
> Video drivers need to be installed, in case of nvidia, you need vdpau files installed as well. Then in vlc, enable GPU acceleration for inputs and codecs. For ATI cards and Intel, apart from drivers, xvba-va driver needs to be installed.


 If use vdpau or have multicore mplayer2 is much better than VLC, which doesn't use Vdpau and seems to not very good in multithreading. 
For mplayer2 [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

---

### Post by diacad on 2011-11-17
to beew: The configuration I posted (Athlon XP +2200, 512 Mb RAM, GeForce4 440 64 Mb AGP) is not really a "weak machine" - well above Ubuntu's minimum specifications - and capable of playing DVDs correctly under Windows XP. Do you need a "stronger" machine when switching from XP to Ubuntu - just to play DVDs?
 
to Linuxisfast: I substituted an nVidia GeForce 6200 AGP card, which does have an adequate proprietary driver from nVidia which goes beyond 640x480.  The choppiness did not go away or diminish.  If those other drivers you mention "need to be installed", then why in #@&* aren't they installed by default?  Are they in place of, or in addition to, the proprietary driver? Where did you get that arcane information?  BTW methinks Linux is not as fast as it should be - faster than what, may I ask?

---

### Post by beew on 2011-11-17
512 M of ram is weak. Minimum requirement means you can install, doesn't say it will perform well. I think Lubuntu will perform well but hey it is your computer, you also didn't install the graphic driver so what a surprise if video playback is poor? If you don't like my suggestions, go back to XP and contribute to MS's monopoly for all I care, don't need to be snarky. 

I told you about my old inspiron, XP just froze as much as it was under Ubuntu (with Compiz), but performance was reasonable with Lububtu.

---

### Post by diacad on 2011-11-22
No intention to be "snarky" whatever that means (sounds pejorative).  I think it is reasonable to expect performance out of Ubuntu at least comparable to XP.  Therefore XP is the benchmark to beat.  Actually, I tried adding RAM, also installed on a more powerful machine with faster processor (P4 - 2.8, same results).  I think I solved my problem without changing the hardware at all, but there still is a mystery.  Ubuntu 10.4 has "Movie Player" out of the box - and it seems to have a buffering bug, at least with some DVD movies.  I clicked on "Applications", then "Ubuntu Software Center" and tried some other DVD players available there under "Sound and Vdeo".  "Bangarang" didn't seem to work at all for DVDs.  But "VLC Media Player" worked well, no choppy problems, etc.  On the basis of this, I would recommend loading VLC in addition (or instead of) the supplied "Movie Player", at least until someone looks into the Movie Player buffering problem - occurs with some, not all, DVDs.  Maybe VLC should be the default loaded with 10.4.  It would save headaches and finger-pointing.  Is there a good reason why not?

---

