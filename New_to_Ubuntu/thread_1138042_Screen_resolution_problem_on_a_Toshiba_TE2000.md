---
title: "Screen resolution problem on a Toshiba TE2000"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Widget on 2009-04-26
Hi

I've installed version 8.04 on my (elderly) Toshiba TE2000.  When I boot up, only the central part of the laptop's screen is used, so I'm guessing I have a problem with screen resolution.

System -> Preferences -> Screen resolution brings up a screen with 'Unknown' on the dipiction of the monitor screen.  The highest resolution available is 800x600 which seems to a bit on the small side.

Pressing the 'Detect Displays' button seems to do nothing.

Help!  How can I use the whole laptop display?

Thanks in advance,
W.

---

### Post by Spiritous on 2009-04-26
> **Widget said:**
> Hi

I've installed version 8.04 on my (elderly) Toshiba TE2000.  When I boot up, only the central part of the laptop's screen is used, so I'm guessing I have a problem with screen resolution.

System -> Preferences -> Screen resolution brings up a screen with 'Unknown' on the dipiction of the monitor screen.  The highest resolution available is 800x600 which seems to a bit on the small side.

Pressing the 'Detect Displays' button seems to do nothing.

Help!  How can I use the whole laptop display?

Thanks in advance,
W.

System >>> Administration >>> Update manager 

Get 9.04, It has added res for lots of cards.

---

### Post by Widget on 2009-04-26
> **Spiritous said:**
> System >>> Administration >>> Update manager 

Get 9.04, It has added res for lots of cards.

Thanks Spiritous.  I've done so, but no dice.  The display preferences screen still only has a maximum of 800X600.

Any idea what I should try next?

---------------

Problem solved!

I found this link:
  [http://ubuntuforums.org/showthread.php?p=7144637#poststop](http://ubuntuforums.org/showthread.php?p=7144637#poststop)
and followed the link mentioned in it to:
  [http://ubuntuforums.org/showthread.php?p=6969113#post6969113](http://ubuntuforums.org/showthread.php?p=6969113#post6969113)
and (nervously) incorporated the changes to xorg.conf.text relating to my monitor and the screen that are in the text file there and it worked!

---

