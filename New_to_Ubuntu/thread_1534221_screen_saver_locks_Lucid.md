---
title: "screen saver locks Lucid"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by TimRV on 2010-07-19
Just upgraded to Lucid from 9.04 via 9.10 and have hit problems which appear to be associated with the screen saver.

If it comes on (after the default 5 mins), the machine locks up. If I open Prefs to change either the default time or the saver (which was Drempel), it locks the machine (possibly the saver preview?).

This means I can't leave my machine for more than five minutes without having to do a complete reset.

I tried deleting Drempel in case it was a problem with the file and I don't have the rights to do that, apparently.

I've tried searching the forums and got loads of interesting stuff, but nothing exactly like this.

Can anyone explain in words of one syllable what is going on and how to fix it please?

---

### Post by hansdown on 2010-07-19
Welcome to the forum, TimRV.

The default for lucid, is to lock the screen, when activated.

If you open your screesaver preferences, you can uncheck the box that says,

"lock screen when screensaver is active".

---

### Post by TimRV on 2010-07-19
> **hansdown said:**
> Welcome to the forum, TimRV.

The default for lucid, is to lock the screen, when activated.

If you open your screesaver preferences, you can uncheck the box that says,

"lock screen when screensaver is active".


Hi, thanks for the welcome.

Sorry, I didn't mean "locks the screen" I mean locks the machine, totally. If I go into the Prefs-Saver option area to try to change anything, everything freezes. I have no mouse movement, no keyboard response. It locks solid. I have rebooted more in the last hour or two than I have in the last two months.

It *seems* to be related to the fact that Lucid can't work out what screen mode works on my Intel 845GE chipset. (Weird. 9.04 had no problems, although 9.10 did.) If the saver comes on due to inaction on the PC, I get an odd message telling me it needs to go into low res, but I click okay and it sort of spirals down from there.

Thanks for the suggestion though.

---

### Post by ajgreeny on 2010-07-19
Try a different screensaver.  I have had one or two in the past that have locked my machine solid as well.  I can't remember which it was, unfortunately, but it was repeatable, so I just didn't try to use it again.

---

### Post by hansdown on 2010-07-19
Sorry for the mistake.

ajgreeny is right about some screensavers causing problems.

---

### Post by philinux on 2010-07-19
> **TimRV said:**
> Just upgraded to Lucid from 9.04 via 9.10 and have hit problems which appear to be associated with the screen saver.

If it comes on (after the default 5 mins), the machine locks up. If I open Prefs to change either the default time or the saver (which was Drempel), it locks the machine (possibly the saver preview?).

This means I can't leave my machine for more than five minutes without having to do a complete reset.

I tried deleting Drempel in case it was a problem with the file and I don't have the rights to do that, apparently.

I've tried searching the forums and got loads of interesting stuff, but nothing exactly like this.

Can anyone explain in words of one syllable what is going on and how to fix it please?

Try the blank screen screensaver.

---

### Post by TimRV on 2010-07-19
> **philinux said:**
> Try the blank screen screensaver.

Okay .... how do I do that *without* going into Pref-Saver??

As I mentioned earlier:

"If I go into the Prefs-Saver option area to try to change anything,  everything freezes. I have no mouse movement, no keyboard response. It  locks solid."

This happens just *entering* the Preferences box. It may be a broken saver, but every time I try to go in to change anything, the first thing it tries to do is preview said broken saver and it locks up before I can change anything.  : (

Cheers

---

### Post by ajgreeny on 2010-07-19
You can probably use gconf-editor and navigate to apps ->gnome_screensaver and edit the keys to show as my screenshot shows.

---

### Post by Jazzy_Jeff on 2010-07-19
If you still are having problems it might be easier to backup your important files and so a clean install. That is the only way I put a new version of Ubuntu on any machine now. Too many problems in the past with upgrades. Good luck.

---

### Post by hansdown on 2010-07-19
One other way, is to install 

```
ubuntu tweak
```

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Once it's installed, click applications> system tools> ubuntu tweak.

In the left column, under startup, click auto start...

In the right column, scroll down to screensaver, and uncheck the box.

---

### Post by TimRV on 2010-07-21
Thanks to everyone who answered - Ubuntu Tweak has let me shut down the screen saver and that has helped a lot.

I'm not sure whether this is a bug (it is, at least, reproducible in the behaviour it generates) or just a dud screen saver, but this has thrown out my Wait-For-Two-Months-Before-Upgrading Theory.

Again, thanks for all your help!

Cheers

---

### Post by hansdown on 2010-07-21
I'm glad it worked,TimRV.

This problem, has been around for some time.

Some screensavers have this effect on a lot of user's computers.

I was helping make a list of which ones do this, but I somehow got side-tracked.

---

