---
title: "Karmic lockup - possibly networking fault"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by sn4re on 2009-11-09
Hi,

I'm running Karmic x64 on my laptop (only 4 months old) and it's constantly freezing up. I think it's a kernel panic, but don't know for sure (new to linux) - it becomes completely unresponsive and the caps lock light starts blinking (I've read that the scroll lock led should blink too, but my computer doesn't have one:D). Is it a kernel panic?

I have absolutely no idea, how to diagnose this. Any ideas, which log files to look at and what should I be searching for? Any commands/programs that can help me find the cause?

Also, keep in mind that I'm not 100% sure about this, but I am left with the feeling, that this has something to do with networking - the problem seems to occur more frequently when Deluge (bittorrent client) is running or I'm playing online games or something along those lines.

Thanks in advance!

---

### Post by JeSTeR7 on 2009-11-10
This happens to me as well on Karmic AMD64.  I'd be willing to bet that you also have the Broadcom STA driver installed, as that's what's causing the problem, as far as I can tell.  It happens when I do any sort of heavy downloading.  Bittorrent is virtually impossible, but even downloading file in Firefox can cause it to happen.

I've responded to a couple of similar bugs on Launchpad, but there doesn't seem to be any movement on getting this fixed.

---

### Post by sn4re on 2009-11-22
For a week there it seemed that the problem had eased up on me, but yesterday it came back with a vengeance - crashed twice within an hour. True, the first time I was using Bittorrent, yet the second time I didn't have any major internet app running - only chatting in Pidgin (don't like empathy; I think it needs more settings and polish).

I know that I have a Broadcom device, but have no idea (and don't know how to check) which drivers I'm running.

Are there alternatives or workarounds I could use? 'cause judging from jester's post, then there's no hope of getting it fixed soon...

---

