---
title: "Boot errors on new installation"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by John Peschken on 2010-07-31
On boot up, when Ubuntu is still in text mode, I see some disturbing messages zip by.  It's way too fast to actually read, but it seems to be reporting[COLOR=Red] EDID [/COLOR]errors of some sort including some checksum verbiage.

1, Do I need to worry about this?  Should I be looking for an equivalent of MS's chkdsk or something else to detect and lock out bad sectors?  Is Ubuntu telling me my HD is dying a slow death?

2. Is there a log somewhere that boot messages get logged so that I can find out what these messages actually say?

---

### Post by bodhi.zazen on 2010-07-31
A log is kept in /var/log/dmesg

google search or post the errors.

---

### Post by John Peschken on 2010-07-31
Found the file you referenced.  It appears there are checksum complaints about several devices; Everything from my NIC which is unplugged to my touch pad. I *think* some of these lines are the messages I am seeing at boot time.  Since all these things seem to work fine, I imagine it's nothing to worry about.  A sample is shown below which seems to refer to the touch pad.   

[   12.818745] elantech.c: Synaptics capabilities query result 0x00, 0x02, 0x64.
[   12.865416] ath: EEPROM regdomain: 0x60
[   12.865424] ath: EEPROM indicates we should expect a direct regpair map
[   12.865434] ath: Country alpha2 being used: 00
[   12.865440] ath: Regpair used: 0x60
[   12.930963] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 147
[   12.931031] [drm:edid_is_valid] *ERROR* Raw EDID:
[   12.931085] <3>00 ff ff ff ff ff ff 00 22 64 25 03 b2 e1 00 00  ........"d%.....
[   12.931094] <3>00 12 01 03 80 14 0b 78 0a 80 36 9a 5e 5d 91 28  .......x..6.^].(
[   12.931103] <3>20 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01   OT.............
[   12.931111] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[   12.931119] <3>45 00 c3 71 00 00 00 19 00 00 00 fd 00 37 41 22  E..q.........7A"
[   12.931127] <3>29 05 00 0a 20 20 20 20 20 20 00 00 00 fc 00 48  )...      .....H
[   12.931134] <3>53 44 30 38 39 49 46 57 31 0a 20 20 00 00 00 10  SD089IFW1.  ....
[   12.931142] <3>00 0a 20 20 20 20 20 20 20 20 20 20 20 20 00 74  ..            .t

---

### Post by bodhi.zazen on 2010-07-31
If things are working I would not worry about those messages.

I believe the EDID is , basically, your monitor settings and is used by xorg.

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

---

### Post by John Peschken on 2010-08-01
I guess there's no point stressing over it.  

The example I gave was a small example cut out of a dozen or so various checksum errors.  Xorg is a mystery to me.  Not a clue, and the Wikipedia entry you directed me to was 75% Greek to me too.  I'm an old network admin from the DOS/CPM Novell Netware days, but all this Unix-y stuff is brand new.

Nonetheless, everything seems to work correctly.   I'm calling it done.

---

### Post by John Peschken on 2010-08-25
Okay, I'm not stressing over it.  Someone above said it's complaining about my monitor.  Well, it's a netbook, I can't change the monitor, and it works fine.

However, I find the errors scrolling by on my screen a little untidy, and I hate that.  Is there a way to sweep the errors under the rug?   To be more concise than I was above, i am getting this error 
   **12.930963] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 147**

on my screen four times in text mode, Then when the display goes graphical, I see them flashed up again.

In the olden days, if I had a program running in MS-DOS putting things on the screen I did not want displayed, I would add [FONT=Courier New]> nul[/FONT] to the command line to redirect screen output to the bit bucket.  Is there a script somewhere I can add a[FONT=Courier New] > nul[/FONT] to or maybe a command line option for whatever program is displaying these errors that would suppress this output?

---

### Post by bodhi.zazen on 2010-08-25
> **John Peschken said:**
> Okay, I'm not stressing over it.  Someone above said it's complaining about my monitor.  Well, it's a netbook, I can't change the monitor, and it works fine.

However, I find the errors scrolling by on my screen a little untidy, and I hate that.  Is there a way to sweep the errors under the rug?   To be more concise than I was above, i am getting this error 
   **12.930963] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 147**

on my screen four times in text mode, Then when the display goes graphical, I see them flashed up again.

In the olden days, if I had a program running in MS-DOS putting things on the screen I did not want displayed, I would add [FONT=Courier New]> nul[/FONT] to the command line to redirect screen output to the bit bucket.  Is there a script somewhere I can add a[FONT=Courier New] > nul[/FONT] to or maybe a command line option for whatever program is displaying these errors that would suppress this output?

In Linux you redirect to /dev/null

> /dev/null

You would probably want to redirect the standard error, see

[http://www.cyberciti.biz/faq/redirecting-stderr-to-stdout/](http://www.cyberciti.biz/faq/redirecting-stderr-to-stdout/)

BUT, finding were to add that is goging to be difficult, it may require you to review the source code for X , which is no trivial task.

You are almost certainly better off reporting the error on Launchpad and allowing it to be reviewed by the Ubuntu developers and referring upstream.

Be sure to include the make and model of your lap top.

---

### Post by John Peschken on 2010-08-25
Yeah, reviewing the source code is way out of my league.  I've submitted it to launchpad.  I'm not sure it's truly a bug; more of an untidiness.  I will let them decide that.  Thanks for the reply.

---

