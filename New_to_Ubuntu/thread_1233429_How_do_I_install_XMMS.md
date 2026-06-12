---
title: "How do I install XMMS?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by xxhopingtearsxx on 2009-08-06
I have Audacious but I've used XMMS many times before on my old desktop.. before switching back to windows and using it.. don't ask why.
I don't know how to install XMMS. I go to add/remove and I type in Xmms and I see xmms2tray, gxmms2, qmmp, and abbraca but idk what those things are, and if they are the actual xmms player.

Someone help. Give me some simple step by step instructions.

---

### Post by starcraft.man on 2009-08-06
XMMS2 is what your looking for, XMMS is not in repos, been discontinued and forked from what I see. gxmms2 is simply a GUI for GNOME. Install gxmms2 from the add menu you were at should do it. For more explanation on install, see my sig. Audacious is also one of the forks from XMMS (actually a fork of Beep media, a fork of XMMS), it is in the repos and also installable same way.

I can't really comment beyond that, I use Songbird.

---

### Post by mcduck on 2009-08-06
XMMS was dropped from repositories since it was ridiculously outdated and hasn't been developed for ages, and because there are so many forks available that are still supported and developed (BMP, XMMS2) and actually XMMS is so old that even it's forks have also been forked by now (BMPx, Audacious).

In other words, there are so many still maintained alternatives with the same features and interface but with considerable improvements over the old XMMS that there really was no reason to keep XMMS around any longer.

(If you have some old XMMS plugins that you need, BMP is able to use them)

---

### Post by bodhi.zazen on 2009-08-06
Of the many forks personally I prefer audacious.

---

### Post by andrew.46 on 2009-08-07
Hi mcduck,

> **mcduck said:**
> In other words, there are so many still maintained alternatives with the same features and interface but with considerable improvements over the old XMMS that there really was no reason to keep XMMS around any longer.

Oddly enough one of the more conservative distros around, [Slackware]("ftp://ftp.osuosl.org/pub/slackware/slackware-12.2/ChangeLog.txt"), has brought xmms back:

> 
+--------------------------+
Fri Sep 12 17:26:34 CDT 2008
ap/sox-14.1.0-i486-1.tgz:  Upgraded to sox-14.1.0.
  See the documention for changes to the command-line options.
  Thanks to tasos and misiu for the update suggestion.
l/libvisual-plugins-0.4.0-i486-1.tgz:  Added libvisual-plugins-0.4.0.
  These create some cool special effects with Amarok.
  Thanks to Darrell Anderson for suggesting the addition.  :-)
**[COLOR="Red"]xap/xmms-1.2.11-i486-2.tgz[/COLOR]**:  Patched to fix the doublesize option.
  Thanks to Patryk Krawaczynski, Keith Richie, and Catalin Tomozei for all
  sending in the same working patch.  Honorable mentions to LukenShiro, misiu,
  and Willy Sudiarto Raharjo for proposing "XLIB_SKIP_ARGB_VISUALS=1 xmms" as
  another possible workaround for the problem.
+--------------------------+
Thu Sep 11 16:02:24 CDT 2008
**[COLOR="Red"]xap/xmms-1.2.11-i486-1.tgz[/COLOR]**:  Added xmms-1.2.11.  This is an audio player that
  is similar to audacious, but uses about a third of the CPU power.
  Please note that "doublesize" mode seems broken -- if it is enabled, XMMS
  will crash, and then will not start again until $HOME/.xmms is cleared out.
  Any patch for this issue would be appreciated.
+--------------------------+



 It would be nice if Ubuntu / Debian would do the same :-).

Andrew

---

### Post by vladanian on 2009-08-07
Looks like you can get xmms from this ppa: [https://edge.launchpad.net/~mapopa/+archive/ppa](https://edge.launchpad.net/~mapopa/+archive/ppa)

That package was built for intrepid, but I just tried installing it on a jaunty system and it installed and ran fine. It looks pretty old school, but it's xmms all right.

So the step by step on that would be click here: [http://ppa.launchpad.net/mapopa/ppa/ubuntu/pool/main/x/xmms/xmms_1.2.11-1ubuntu7_i386.deb](http://ppa.launchpad.net/mapopa/ppa/ubuntu/pool/main/x/xmms/xmms_1.2.11-1ubuntu7_i386.deb) and install the package with gdebi.

---

### Post by mcduck on 2009-08-07
> **andrew.46 said:**
> Hi mcduck,



Oddly enough one of the more conservative distros around, [Slackware]("ftp://ftp.osuosl.org/pub/slackware/slackware-12.2/ChangeLog.txt"), has brought xmms back:




 It would be nice if Ubuntu / Debian would do the same :-).

Andrew

Why? What does it do better than it's more up-to-date forks? I've never, ever, heard anybody demanding XMMS back to repositories actually explain why they can't use BMP or Audacious instead..

---

### Post by andrew.46 on 2009-08-07
Hi mcduck,

> **mcduck said:**
> Why? What does it do better than it's more up-to-date forks? I've never, ever, heard anybody demanding XMMS back to repositories actually explain why they can't use BMP or Audacious instead..

Simply for sentimental reasons, it was great software in its day and it saddens me a little to see it discarded as everbody moves on to bigger and better things. I do not seriously expect to see its return to Ubuntu, its return to slackware was something of an anomaly.

Andrew

---

### Post by mcduck on 2009-08-07
> **andrew.46 said:**
> Hi mcduck,



Simply for sentimental reasons, it was great software in its day and it saddens me a little to see it discarded as everbody moves on to bigger and better things. I do not seriously expect to see its return to Ubuntu, its return to slackware was something of an anomaly.

Andrew
Hi, and thanks for answering.

That was pretty much what I was guessing the reason to be. :)

I used to be a big XMMS fan. Then I found out that there was a player that was exactly like XMMS, but with nice GTK2 menus instead of the horrible GTK1 crap XMMS has. So I moved to BMP.

And some years later there appeared program that was exactly like XMMS and BMP, only with nice popup window to show track details in the playlist and Last.fm support etc, and so I moved to Audacious..

All the time I had all the things that made me like XMMS in the first place (including the XMMS skin :D), every update just made things slightly better.

(These days I stick with MPD, my music collection has grown way beyond what's usable without a library)

---

