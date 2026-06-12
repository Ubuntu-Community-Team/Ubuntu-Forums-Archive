---
title: "Firefox url bar keeps highlighting while typing"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by jjblackfox on 2009-09-09
Hi, I just installed ubuntu 9.04 on my girlfriend's machine and everything is working perfectly except for the url bar on firefox. 

While I type in an address, after I type about two characters, the whole bar gets selected so when I type more characters the first two letters disappear. This happens constantly, so I'm unable to type addresses in. The same thing happens with the google search bar at the top.

This doesn't happen all the time and I haven't been able to find a trigger that causes it yet. 

I can click the google search bar, hit enter, then type the address in on google, but it takes longer and it's irritating. I have this problem on my laptop and my friend has the same problem on his. Any suggestions would be greatly appreciated.

---

### Post by shae on 2009-09-09
Is it possible that you are hitting the Touchpad and activating its "tap to click" feature?

---

### Post by XCan on 2009-09-09
This actually happens to both of my machines every time after I resume from screensaver (+locked screen). I always have to select another window first, before typing something into firefox.

---

### Post by gordong11 on 2009-09-12
I'm getting this same bug but in the mini google search bar only to the right of the url bar in Firefox. After I type 2 characters, they highlight and the 3rd character becomes the 1st now. Can only type in 2 characters.

I have manually changed a setting in "about:config","browser.urlbar.clickSelectsAll = true". Which I need, but is probably the cause.


Confirmed: after the screensaver kicks in. I have to close firefox and re-start to fix. but it will happen again. so weird. only in google search bug.

---

### Post by mike984 on 2009-09-19
This happens on 2 of my computers and one of my friends.  Has been happening since 9.04 was installed.  

I don't think it's related to the screensaver because I don't it enabled.  However, after using Firefox for about 30 mins or so, it exhibits this behaviour.  When I start to type something in the Google search box at the top right of Firefox, it seems to highlight my text after the first character.  If go to the URL address box, it happens there as well.

I deleted my ~home/.mozilla folder and reinstalled my extensions.  I am still having the same problem :(

---

### Post by Ricket on 2009-09-20
Same problem here. I have a theory - I think the bar highlights when normally the suggestion box would drop down - for example, when you start typing something, normally the location bar shows elements from your history that match what you're typing, or the same thing happens in the Google bar and normally it would show search suggestions. But when this bug occurs, if you type something so odd that no results would happen (and the drop-down would not normally appear), then the bug doesn't happen. Try it next time you encounter this bug.

If my theory is correct, then this problem is surely related to this other one: [http://ubuntuforums.org/showthread.php?t=1152059](http://ubuntuforums.org/showthread.php?t=1152059)

I'm on Ubuntu 9.04 32-bit by the way, and the same thing happens in both Shiretoko (firefox-3.5) and Firefox 3.0 (firefox).

---

### Post by mike984 on 2009-09-23
I think you're right.  Looks like a bug has been reported.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703)

---

### Post by LewRockwell on 2009-09-23
Informational Report:

We have Firefox running on both mac and pc machines 1996 thru 2008 vintage

OSX, Windows, and a dozen flavors of *nix distros

we have not experienced this behavior

we refuse cookies and use:

Adblock Plus

NoScript

BetterPrivacy

Flashblock

Ghostery

Firebug

User Agent Switcher

.

---

### Post by Ricket on 2009-09-23
Okay, well, those of you experiencing this bug please reply with the Firefox add-ons you have enabled. Though I've tried disabling all my add-ons in the past and I still experienced the problem. Here are mine:

Adblock Plus
Download Statusbar
Firebug
Google Gears
Novell Moonlight
ReloadEvery
Xmarks

My system is:
Dell Inspiron E1705
Core 2 Duo T7200 2.0ghz
2.0gb ram
Nvidia GeForce 7900GS
320gb 7200rpm drive (~70% free)
Ubuntu 9.04, kernel 2.6.28-15-generic

---

### Post by farsight on 2009-09-23
Hey all,

Have any of you tried configuring Firefox, using about:config in the URL bar? It may be that an option that should be set to false has inadvertently been set to true?

I'm not currently experiencing this problem so I'll not bother fixing something that isn't broken :)

Good luck,
Farsight

---

### Post by Ricket on 2009-09-23
Hey, did any of you install swiftfox? I was going through my about:config, nothing unusual there, but I remembered I tried swiftfox and that is a possible reason maybe. I did uninstall it though.

I think my solution will be just keep putting up with it until I reformat to karmic. It's not too much longer now, and I'm okay now that I found out that opening a new window will "fix" it.

---

### Post by XCan on 2009-09-24
FF 3.0.14
Extension: Adblock Plus 1.1.1

---

### Post by ssouthparkk on 2009-11-07
I am having the same issue.  Has a fix been found?

I have Ubuntu 9.10 and the FF that comes on it: 3.5.4

I have Ad Block, Screengrab, and Stylish enabled.  The theme is Compact Classic.

---

### Post by distortedecho on 2009-11-08
I'm having his issue too.. I use Ghostery, NoScript and Ad-Block Plus..

So annoying - can this be fixed???

---

### Post by ssouthparkk on 2009-11-09
Seems to be a very common bug.  Maybe it will be fixed in the nest Ubuntu Firefox release?

---

### Post by phillw on 2009-11-09
> **ssouthparkk said:**
> Seems to be a very common bug.  Maybe it will be fixed in the nest Ubuntu Firefox release?

Firefox is not released solely for Ubuntu. lovinglinux keeps an excellent thread for fire-fox over this way --->> [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

My 9.04 --> 9.10 went fine, the auto update to Shiretoko months ago spooked me, and that was when I found his thread.

He's a real nice guy (And he'll be blushing if he reads this).

My Sig has an info link, follow it to linux (ubuntu) resources. They're a decent set of links to hold onto.

Phill.

---

### Post by Mr_B on 2009-11-20
I have the same problem. I changed "browser.urlbar.ClickSelectsAll=True" in "about:config"

Minimizing and restoring Firefox fixes the problem until the next time the screen saver comes on. It is still annoying.

There is already a bug report like mike984 mentioned...
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703)

---

### Post by Hovik on 2010-10-02
I have the same problem in 10.04 Netbook Remix. I'm going to give Mr_B's suggestion a shot. Glad to see I am not the only one in this boat...

---

### Post by jsgarvin on 2010-12-30
See my instructions in post #9 on the first page of [this thread]("http://ubuntuforums.org/showthread.php?p=10299204#post10299204"), for instructions to consistently reproduce what appears the be the same bug.

Does not appear to have anything to do with browser.urlbar.ClickSelectsAll

Mr_B's mention of the screen saver is what clued me in on how to reproduce this.

---

### Post by sabaitechnology on 2011-02-21
We're having the same problem with a brand new install of Ubuntu 10.10 with all patches and Firefox 3.6.13.  Any ideas?  It's any field, not just url bar.

---

### Post by mooses on 2011-04-10
I've started using chromium-browser because of this annoying bug. Chromium with ad-blocker is very nice!

---

