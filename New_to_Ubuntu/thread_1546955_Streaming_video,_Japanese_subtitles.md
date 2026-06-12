---
title: "Streaming video, Japanese subtitles"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by akira27 on 2010-08-06
Hi, I'm having an issue with correctly displaying Japanese subtitles on streaming video.

I have Ubuntu 10.04 Lucid, and on both Google Chrome and Mozilla Firefox, the subtitles are garbled (shown as little boxes) on the swf player.

The video I'm trying to watch is this: [http://www.ted.com/talks/lang/jpn/tan_le_a_headset_that_reads_your_brainwaves.html](http://www.ted.com/talks/lang/jpn/tan_le_a_headset_that_reads_your_brainwaves.html)

As can be seen, the Japanese font is displayed fine on the page itself, but when viewing the video, the subtitles don't show up correctly.

I'm guessing the problem is with the encoding setup on the swf player plug-in.  Could anyone help me with this issue?

Thank you.

---

### Post by diablo75 on 2010-08-06
I'm running Windows, which is apparently missing the appropriate fonts because nothing shows up on that page correctly for me (and I just watched that video a couple days ago in English so I'm familiar with the site).  So my guess is Flash is calling out to use a font that's not installed on your computer...

---

### Post by akira27 on 2010-08-06
Hi diablo75,

Thanks for the input -- it gave me an idea to search for Japanese fonts which might be necessary for the subtitles.

Here's a link that explains how to install MS Gothic and MS Mincho, which are quite standard Japanese fonts.  I didn't realize these fonts didn't come default with Ubuntu.

[http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)

The part I will try is called "Setting up the system to display Japanese characters properly".  I guess I should have searched the forums more carefully before posting my problem..

I'll post the result, if it works or not.

---

### Post by proxess on 2010-08-06
The best thing you should do is in the Langauge settings, install Japanese.

---

### Post by akira27 on 2010-08-06
Thanks for your suggestion, proxess.  One of the first things I did when installing Ubuntu was to set up the language preference to include Japanese.  I quite like the default Japanese font.

To update: I installed MS Gothic and MS Mincho, rebuilt the fonts cache, created a font configuration file (~/.fonts.conf) as written on the link above, and restarted the system -- the streaming video still doesn't display subtitles correctly.  Nothing has changed, it's all displayed as little boxes.

So, if anyone else has any ideas, I appreciate it.

One thing I'm wondering, is there a different fonts configuration file for Ubuntu 10.04 perhaps? This file (~/.fonts.conf) didn't exist so I created it..

---

