---
title: "Reverting to FF 3.0.14 from 3.5.4"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by BobJam on 2009-11-06
Canonical recently released an upgrade from FF 3.0.14 to 3.5.4 in the repository.  I downloaded that upgrade, but have decided it's too buggy . . . so I want to revert to 3.0.14.

I knew how to do that in Windows, and am wondering if the same procedure would work:  I saved my profile to another directory, uninstalled the version I didn't want, and then installed the version I DID want and then replaced the new profile with the backed up old one.  (That may be "going around the barn" and perhaps there's a better way, but this way always worked for me).

But, I used to keep the previous version installation .exe in a "downloads completed" folder JUST FOR THAT REASON.  However, since I install in Ubuntu using the Upgrade Manager, I don't have the 3.0.14 deb.

I'm sure this is possible, but I don't know how to do it in Ubuntu.

So, how would I revert to 3.0.14, or even go to 3.5.5? (I understand that 3.5.5 is not as buggy, but while it's available from the moz site for linux, it hasn't come out in the repository yet).

I won't go into detail on the "bugginess", and perhaps what I consider bugs is just a matter of new settings I need to make in 3.5.4, but I've messed around with it and I'm very frustrated . . . which is why I want to revert or try to do 3.5.5)

---

### Post by oldsoundguy on 2009-11-06
you can't even revert now in Windows.

Try putting 3.5.5 on instead.  It FIXES that bug!

---

### Post by rb0171610 on 2009-11-06
> **BobJam said:**
> Canonical recently released an upgrade from FF 3.0.14 to 3.5.4 in the repository.  I downloaded that upgrade, but have decided it's too buggy . . . so I want to revert to 3.0.14.

I knew how to do that in Windows, and am wondering if the same procedure would work:  I saved my profile to another directory, uninstalled the version I didn't want, and then installed the version I DID want and then replaced the new profile with the backed up old one.

But, I used to keep the previous version installation .exe in a "downloads completed" folder.  However, since I install in Ubuntu using the Upgrade Manager, I don't have the 3.0.14 deb.

I'm sure this is possible, but I don't know how to do it in Ubuntu.

So, how would I revert to 3.0.14, or even go to 3.5.5? (I understand that 3.5.5 is not as buggy, but while it's available from the moz site for linux, it hasn't come out in the repository yet).
Have you tried ubuntuzilla? I am using 3.5.4 and thought it was the latest version.  I would suggest uninstalling firefox, and finding the .deb online somewhere and installing that in order to downgrade.  Ubuntu does not allow  you much freedom with firefox.

---

### Post by BobJam on 2009-11-07
ubuntuzilla did it.  I finally got 3.5.5 and am now trying it.

It was not as straightforward, though, as I thought it would be.

When I first tried to run the ubuntuzilla script, it ran with the terminal command that was recommended and wouldn't complete (it displayed an error).

I had downloaded "firefox-3.5.5.tar.bz2" to my desktop (from another site), and apparently the script got hung up on that file.  So I transferred that file to the trash, and the ubuntuzilla script ran (I also had to copy the script file to my desktop to get it to run . . . it buried itself in one of the root folders . . . and I had to use "gksudo nautilus" to do that . . . didn't run the ubuntuzilla script in sudo though).

Anyway, I finally got it to work but the whole thing was pretty twisted, but now I have 3.5.5 from mozilla (not the Canonical repository . . . but the script gives an option to have an update notification).

However, I'm still searching for the 3.0.14 deb.  Haven't found it yet, but maybe I won't need to if this 3.5.5 works out.

---

### Post by wilee-nilee on 2009-11-07
Firefox 3.6 beta is available as well. You might ask a few questions or try just reinstalling 3.5 it should not be buggy something is wrong with it probably with the upgrade from the earlier version.

---

### Post by rburkartjo on 2009-11-07
ff 3.6beta is a lot faster also

---

### Post by winotree on 2009-11-07
This [http://support.mozilla.com/en-US/kb/Installing%20a%20previous%20version%20of%20Firefox]("http://support.mozilla.com/en-US/kb/Installing%20a%20previous%20version%20of%20Firefox") is a page from Mozilla.  It has a link to version 3.0.15 if you still want it -- it will be maintained only until January.  I never used version 3.5.4 but know *that on my device* both 3.5.5 and 3.5.6 are fine.  :)

SEE - [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

NOTE - Google Search Terms: *firefox previous versions*

---

### Post by KcLKcL on 2009-11-07
Actually you can upgrade Firefox with

```
gksudo firefox
```

Then Help>Check For Updates

But if you want to upgrade to new major release I guess you have to use Ubuntuzilla (The easy way)

---

### Post by tacantara on 2009-11-07
> **KcLKcL said:**
> Actually you can upgrade Firefox with

```
gksudo firefox
```Then Help>Check For Updates

But if you want to upgrade to new major release I guess you have to use Ubuntuzilla (The easy way)

I used Ubuntuzilla to attempt to install the 3.5.3 version (currently using 3.5.4).  The installation process appeared to run smoothly, but when I restarted the browser, it opened up as 3.5.4 (I checked the version info via the Help menu).  Any thoughts on that?  It's not really a deal-breaker for me, as 3.5.4 is running good enough for me, and I have Chrome as a back up.

---

### Post by Barriehie on 2009-11-07
Can get mozilla releases [here](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/).

Barrie

---

### Post by BobJam on 2009-11-07
@wilee-nilee,

3.5.5 seems buggy too . . . it stalls opening (and then on the second try it opens), but that may be because I have 23 tabs remaining open on start (Will try a clean profile to see if it does the same thing).  However, I had that many tabs on startup with 3.5.4 and 3.0.14 and they both started just fine.  Looks like I may have gone from the frying pan into the fire with 3.5.5.

Don't know yet if I'll go back to 3.0.14, 3.5.4, or try 3.6 beta.  My inclination right now is to go back to 3.0.14 (finally found it thanks to winotree).


@rburkartjo,

Am reluctant to try a beta, but I may do that.  (Have never tried a beta, and since I'm having so many problems . . . which may be of my own doing, so I can't really say these versions are buggy for sure . . . a beta may increase the problems).


@winotree,

Thanks for the links.  I went to the mozilla page and downloaded the .tar.bz2 from their FTP site for 3.0.14, and made a deb out of it with Alien.  Haven't tried installing it yet.  Have to read the mozilla installation instructions again so that I'm sure I've got my arms around the procedure.  As willee-nilee implied, my problems may be due to a faulty installation routine . . . I may be messing up there.

But by the time I get done with all these reinstallation efforts, I'll either be a real pro at it, or will have totally messed up my machine (and I have, BTW, made a backup of my profile on removable media, and also backups of my / and /home directories).

I took a look at the PPA's maintained for mozilla builds, but these are for beta's and alpha's so I don't think I'll use that . . . plus downloading directly from the mozilla site seems a little more straightforward.  As far as repository updates go, if I ever get to a stable version again, I'll likely want to remain there for a while without any automatic Update-Manager updates (which was what got me in this fix in the first place).  If I do end up with 3.5.5 (assuming I get it stable), it's got an update notification installed from the ubuntuzilla script.  And if I try 3.6b, I'll likely get it from ubuntuzilla (thanks again, rb0171610, for turning me on to that) so it has the update notification.

Since you gave me that mozilla link for old versions, and I bookmarked it, I now have access to 3.0.14 (and other older versions) and no longer need to do Google searches for reverting.  (Plus I now have the 3.0.14 deb, which is like having the old install .exe that I used to keep when I used Windows . . . see my OP).


@KcLKcL,

That command, which starts FF 3.5.5 with the "Check for Updates" item enabled but showing NO updates essentially puts me where I'm at already.  So you are correct about using ubuntzilla.  BTW, what's the "easy way"?


> **tacantara said:**
> I used Ubuntuzilla to attempt to install the 3.5.3 version (currently using 3.5.4). The installation process appeared to run smoothly, but when I restarted the browser, it opened up as 3.5.4 (I checked the version info via the Help menu). Any thoughts on that? It's not really a deal-breaker for me, as 3.5.4 is running good enough for me, and I have Chrome as a back up.As I understand it, ubuntuzilla will only go FORWARD and not BACKWARD (IOW, revert).  If you told it to revert to 3.5.3, my guess is that it just defaulted to your current version of 3.5.4.

I also have Chromium, but until it accomodates a TMP-like add on (which is my main attraction to FF), I'll stay with FF as my default browser.


@Barriehie,

Basically, your link is the same as the one that winotree gave me, but I bookmarked it also.  Thanks.

---

