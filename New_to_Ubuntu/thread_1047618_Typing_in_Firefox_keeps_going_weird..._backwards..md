---
title: "Typing in Firefox keeps going weird... backwards."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by NEUR0M4NCER on 2009-01-22
Hi all.

Every now and again, typing in a text entry box in Firefox (userinterface, as-well as web-pages) starts going... wrong. It's not consistent - it puts some characters before the cursor, some afterwards, so that you end up trying to second guess where it will put the next character. As I said, it's *very* random, so i've been unable to reliably replicate the problem. Web/Forum searches yield no clues, aside from others experiencing similar problems - I even found a YouTube vid of someone having the exact same problem, and the comments insisted the guy was performing some kind of trickery!!!

Any help would be awesome.

---

### Post by mjheagle8 on 2009-01-22
[http://ubuntuforums.org/showthread.php?t=988824](http://ubuntuforums.org/showthread.php?t=988824)
this looks like a similar problem. hope it helps!

---

### Post by NEUR0M4NCER on 2009-01-22
Hi - thanks for your reply.

I followed the links through to the LaunchPad Bug, which says this:> right clicking switches page direction.
 Robert Pollak wrote on 2008-07-25: (permalink)

As a small improvement (less surprise for inexperienced users), one can disable bidirectional text:

1) Type "about:config" into the address bar.
2) In the "Filter:" text box, type "bidi"
3) The "bidi.browser.ui" entry was set to "true" in the "value" column. To change it to "false", right-click on this entry and select "Toggle".
4) Restart Firefox.

After doing all this, the "Switch page direction" context-menu entry has disappeared.

(Copied from [http://ubuntuforums.org/showthread.php?t=619481](http://ubuntuforums.org/showthread.php?t=619481))

Now the last menu entry is "Page Info" or "Properties", whose windows can be closed by pressing Escape.
I went into about:config but the dialogue was already set to false. I've had the problem appear when i've only had one tab open also, so while this might be related, i'm not sure if it's the exact same issue.

Thanks.

---

### Post by mjheagle8 on 2009-01-22
no problem. glad i could help.

---

### Post by NEUR0M4NCER on 2009-01-22
I should probably also add, for the sake of completeness, that i've tried different keyboards; PS/2, USB and USB/Wireless combo. I didn't actually change due to the problem, that's just been how it's worked out.

Also - Is there any Firefox key-combo or similar that might trigger the affect described? I ask this because (and bear with me here...) the problem only seems to happen when my GF uses the PC... initially, I thought she was doing something daft, but i've watched it happen, and it doesn't seem to be her fault, unless she's making some quick mis-key that i'm not catching.

---

### Post by fubbleskag on 2009-01-22
is this a laptop?

do you and the GF use the same or different logins?

---

### Post by NEUR0M4NCER on 2009-01-22
No, it's a C2D desktop running Intrepid AMD64... We both use the same account (set to auto-login).

---

