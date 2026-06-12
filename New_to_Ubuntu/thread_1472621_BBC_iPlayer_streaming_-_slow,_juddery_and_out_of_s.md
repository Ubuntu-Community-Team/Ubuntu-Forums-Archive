---
title: "BBC iPlayer streaming - slow, juddery and out of sync in Ubuntu"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-05-04
Hope someone can help with this.

When streaming video (via browser) from BBC iplayer, the playback is juddery and loses sync with audio.

I've tried both Firefox and Google Chrome, both suffer though Chrome is noticeably worse.  The problem has existed in Karmic and continues post-upgrade to Lucid.

The playback in Windows is flawless (in IE and FF), so it isn't a problem with network speed or bandwidth etc.  I'm presuming this is bound to be a flash issue?  The flash install is as up to date as I know how to make it.  I tried to download the latest flash directly from Adobe but when I run the .deb I get the following message...."Error: Conflicts with the installed package 'flashplugin-installer'".

---

### Post by Helkaluin on 2010-05-04
Suggestion, by no means a real solution, but a feasible workaround given the imature state of Flash on Linux:

Try iplayer-dl in RubyGems. No more dependency on Flash or AIR. You'll just need a video player that can decode h.264.

[http://rubygems.org/gems/iplayer-dl](http://rubygems.org/gems/iplayer-dl)
[http://po-ru.com/projects/iplayer-downloader/](http://po-ru.com/projects/iplayer-downloader/)

---

### Post by carl4926 on 2010-05-04
Could be your flash version needs updating.
I have seen this before with BBC

I'm using get_iplayer
There have been problems relating to the BBC implementing crypto in flash. But it seems to less of an issue ATM.
Unfortunately I only have a .rpm of that application.

---

### Post by Scunnered on 2010-05-04
I experienced difficulty with the BBC iPlayer and found that it was down to my system being a 64 bit one.

I was directed to [http://ubuntuforums.org/showthread.php?t=1468743](http://ubuntuforums.org/showthread.php?t=1468743) which resolved the problem for me.

Perhaps as you did not state what system you are using this might assist.

---

### Post by aquascrotum on 2010-05-05
System is a 32-bit (ageing) Dell Latitude laptop.

The judder / sync problems arent as noticeable when playing in the small windowed mode in both browsers - the problems only really kick off when I full-screen the window.

Are any of the linux native apps named above streamers, or do they just download the whole video file before playing?

---

### Post by madjr on 2010-05-05
well on my computer it runs fine

usually the video card drivers also have to do with it (so is flash and/or drivers)

before, my drivers were not that good, so i had the same problems as you, but with lucid, they work really well.

when i had that problem i had 2 tricks:

zoom in on firefox or google chrome, the video will enlarge

or

use the compiz zoom (windows/super key + mouse wheel)

[http://www.youtube.com/watch?v=3usPs53xrpc](http://www.youtube.com/watch?v=3usPs53xrpc)

i still use it sometimes, is just cool :)

---

### Post by Helkaluin on 2010-05-05
> **aquascrotum said:**
> Are any of the linux native apps named above streamers, or do they just download the whole video file before playing?  Both iplayer-dl and get-iplayer download the whole file before playing. iplayer-dl is simpler, whilst get-iplayer gives you more options including the ability to download HD content.  iplayer-dl can be installed simply through RubyGems. get-iplayer is now a dropped project due as the original dev's (Phil Lewis) response to BBC's open source policies in March 2010. The project is now forked and being rewritten by James Laver. You have to build it from the git repository at [http://github.com/jjl/get_iplayer](http://github.com/jjl/get_iplayer).

---

### Post by aquascrotum on 2010-05-06
> **Helkaluin said:**
> Both iplayer-dl and get-iplayer download the whole file before playing. iplayer-dl is simpler, whilst get-iplayer gives you more options including the ability to download HD content.  iplayer-dl can be installed simply through RubyGems. get-iplayer is now a dropped project due as the original dev's (Phil Lewis) response to BBC's open source policies in March 2010. The project is now forked and being rewritten by James Laver. You have to build it from the git repository at [http://github.com/jjl/get_iplayer](http://github.com/jjl/get_iplayer).

Surely if I wanted to download the whole file before watching, I could use the official BBC iPlayer Desktop download manager which seems to be linux native?  Whats the advantages of the above named programs?

Bit of a pain all round tbh, the joy of iplayer is the streaming. Yet another reason I've to flick back to windows.

---

### Post by Helkaluin on 2010-05-06
> **aquascrotum said:**
> Surely if I wanted to download the whole file before watching, I could use the official BBC iPlayer Desktop download manager which seems to be linux native?  Whats the advantages of the above named programs?
An itch comes up trying to argue the semantics of 'native'... The program is written in AIR, and it's cross-platform...

The advantage is that the videos downloaded via those alternative methods are DRM-free, and you can play them with your favourite player, move them to another computer, and they won't self-destruct after a week after you've played it for the first time.

And really, give iplayer-dl a try. It's not hard at all: it's just <iplayer-dl http://the.link.to.the.programme.on.iplayer.website> one line and it's downloaded.

---

### Post by meznaric on 2010-06-27
The problem is that some of the programmes are being streamed live. You can't download the whole thing in that case, but the slow frame rate still occurs. If anyone knows of a solution for this, I'd be very grateful.

---

### Post by tinalee777 on 2010-08-01
BBCi is slow and juddery for me too when in full screen using FF. I have a pentium dual core 3G running 10.04 LTS and latest flash version 10.1. The PC is fast enough for everything else. What is strange is ITV player works fine. Also, if I play BBCi with the Boxee app I can view it in full screen without a problem, unless it's HD, then it's still juddery. By juddery I mean like a very slow frame rate. I really don't know what to try.

---

### Post by davidmohammed on 2010-08-01
agree - its a combination of poor flash implementation in linux and your graphics driver.

I'm in a similar situation - I use the "use low bandwidth" option which is at the bottom of the screen.  Works for me both "in window" and full screen.

---

### Post by daveybuntu on 2010-08-01
Hi,

I've been puzzling over this problem for over a year now.  I believe I've stumbled upon a simple solution to it.

When you go to view full screen video, you will always get a jerky, stuttering image, unless, you ZOOM OUT one level in your browser.

I use a Dell Netbook, so i am forever zooming in and out.  I noticed that I always got jerky video using Google Chrome, but not with Firefox.  Then I noticed that Chrome always starts up at the default zoom level.  On any web page, simply press CTRL and "-" <minus symbol>, to zoom out, and full screen video is as smooth as it would be on any file I had on my hard drive.

I have no idea why this works.  If, without being in full screen, while playing a programme, I press CTRL -, flash seems to "buffer".  I wonder if it's possible for it to call for a certain bitrate.  Zooming out means a smaller image, so lower bitrate, which is for some reason less problematic to play back.

I hope this works for you.

Dave

---

