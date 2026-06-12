---
title: "[SOLVED] FutureWarning"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by archolman on 2009-01-05
[SIZE=4][FONT=Arial Black]I just upped from Hardy to 8.10, & all went well, but I'm wondering why I got  the following[/FONT][/SIZE] [FONT=Arial Black][SIZE=4]msg in the terminal[/SIZE][/FONT][SIZE=4][FONT=Arial Black];
[/FONT][/SIZE][FONT=Arial Black][SIZE=4]/usr/lib/python2.5/site-packages/apt/_init_.py:18: FutureWarning: apt API not stable yet:confused:

Cheers,
Dick[/SIZE][/FONT]

---

### Post by Michael.Godawski on 2009-01-06
hi, 
might be a problem with your graphic card... have you used envy to install the drivers for it ?

>  Your card is no longer supported by ATI’s proprietary driver. You should keep using the “ati” open source driver.
found here [http://albertomilone.com/wordpress/?p=184#comment-4094](http://albertomilone.com/wordpress/?p=184#comment-4094)

---

### Post by archolman on 2009-01-06
[SIZE=4][FONT=Arial Black]I didn't use anything to install drivers; as I had no probs with[/FONT][/SIZE] [FONT=Arial Black][SIZE=4]the graphics[/SIZE][/FONT][FONT=Arial Black][SIZE=4] under 8.04.1.LTS, just did an upgrade via update manager.[/SIZE][/FONT][FONT=Arial Black][SIZE=4] However, I think the answer is elswhere[/SIZE][/FONT]. 
[FONT=Arial Black][SIZE=4]([/SIZE][/FONT][SIZE=4][FONT=Arial Black]If you have time, check my name for further posts. I think my HDD is sick:(
Thanks[/FONT][/SIZE],
[SIZE=4][FONT=Arial Black]Dick[/FONT][/SIZE]

---

### Post by sdennie on 2009-01-06
If I had to guess, it would be because python breaks backward compatibility fairly regularly.  This module is just preemptively giving you a warning that it's probably going to be broken in the not-so-distant future.  It seems like a safe warning to ignore.

(Some would argue that all python modules should emit this warning...)

---

