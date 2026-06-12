---
title: "hardware modems"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by wormturns on 2009-08-12
Hey,

According to xmodem.org my old school v90 modem is listed as "full hardware" and "supported by Linux kernal and setserial". Lucky me! Most of the help pages on dial-up modems deal with getting a winmodem to work under Ubuntu, and I'm a little lost on how to get my hardware modem working.

I think I'll need 'setserial" to configure the com port the modem is attached to(/dev/ttysX). And this is a 'terminal' program. Then will I need 'wvdial' or isn't there is a ppp dialer that is included in the 9.04 cd?

Thanks

---

### Post by MyR on 2009-08-12
What's a modem??
?

just kidding.
[http://help.ubuntu.com/community/DialupModemHowto](http://help.ubuntu.com/community/DialupModemHowto)

peace

---

### Post by Bartender on 2009-08-12
Hey, I'm glad I stumbled across this thread.  I was trying to set up one of my trusty old US Robotics 5686 externals on 9.04 just last night.  Check this out.

```
bpbar@bpbar-laptop:~$ sudo wvdialconf /etc/wvdial.conf
[sudo] password for bpbar: 
sudo: wvdialconf: command not found
bpbar@bpbar-laptop:~$ 
```

I've set up wvdial a dozen times, but not on 9.04 until just now.  "wvdialconf" not found??

WTH does that mean?

I tried several times and gave up.  pppconfig worked fine.  I'm posting this via the USR.  If someone can tell me what I did wrong, or verify that wvdialconf has some sort of weird problem in 9.04, please contribute.

pppconfig is kind of confusing to work thru, but it seems faster than wvdial.  It sure connects faster!

I've never had to do anything with "setserial", whatever that is.  pppconfig was unable to find the modem during the intial setup, but I manually installed it right after it failed to detect the modem and that worked fine.  The USR is connected to a serial-to-USB adapter cable, so it's recognized as "dev/ttyACM0". That's a zero on the end, not an "oh".  The adapter cable is - uh, oh, hell, here's my dial-up diary from a few years back.  The adapter cable is described in post #12.

[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

P.S.  Well, ain't that a trip.  Posting to your thread got me to thinking about this some more.  I decided to download gnome-ppp

```
sudo apt-get install gnome-ppp
```

I usually go to the library and borrow their broadband for any kind of downloading but I knew gnome-ppp was a fairly small package.  I was watching the so-called "progress".  One of the downloads was "wvdial"!!  I guess the developers were looking for old crap to throw out in order to fit all the new goodies in and still keep the download small enuf for a 700 MB CD.  wvdial is not even included in the Jaunty .iso.  That explains why I couldn't call it up last night.  It wasn't there.  Sheez.

So I would suggest using pppconfig to set up a basic dialer.  Once you get online download gnome-ppp.  After installation you'll find the utility in Applications>Internet.  Right-click on the icon, put a launcher in your panel, open it up, type in the proper settings on the first page and under the Set-up tab.  It'll be the same info you gave to pppconfig.

I googled around a little bit but saw no mention of wvdial's absence in Jaunty.  Dialer instructions are unchanged from previous versions.

---

### Post by longtom on 2009-08-13
It appears that wvdial is not included in Jaunty.  See also here:

[http://ubuntuforums.org/showthread.php?t=1238954](http://ubuntuforums.org/showthread.php?t=1238954)

Why is anybodies guess.  I guess the main reason is, that dial-up is just no catered for anymore in Ubuntu.

---

### Post by GeorgeVita on 2009-08-13
Hi, look also: [http://ubuntuforums.org/showpost.php?p=7747593&postcount=10](http://ubuntuforums.org/showpost.php?p=7747593&postcount=10)

The idea is that you need to install ALL 5 packages below (installation must be done one after the other: 1-2-3-4-5)
1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

**Note that above are all for an i386 pc.**

...all started from the post below:> **HarryBhat said:**
> Thanks a lot for the reply buddy :)
But how do I download from repositories if my only means of connecting to internet is my 3G Wireless Card which fails to connect now? :(
Regards,
George

---

### Post by Bartender on 2009-08-13
*"But how do I download from repositories if my only means of connecting to internet is my 3G Wireless Card which fails to connect now?" *

Yeah, the dial-up situation has always had a Catch-22 feel to it.  Jaunty just made it a little worse is all.  

All I've ever done was try to make a traditional dial-up configuration.  The whole concept of using a cell phone or air card to dial sounds kind of weird.  Is it a lot harder to set up?

---

### Post by LowSky on 2009-08-13
complain to the developers, using the forums will not get you much response or change. Make a complaint on launchpad.

---

### Post by Bartender on 2009-08-13
Hi, LowSky -
The same suggestion was made on a similar thread.  I assumed wvdial was tossed out to make room for other stuff, but it could be broken.  

I hate reporting bugs if it's not really a bug...

---

