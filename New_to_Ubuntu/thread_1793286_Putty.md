---
title: "Putty"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by xxsawer on 2011-06-29
Hi, I am using Putty to log on remotly on a unix machine.
To make Home and End keys work normally I changed the putty setting:
Connection -> Data -> Terminal-type string
from xterm to linux...
I gues putty sets this string as a value for the TERM variable whenever I log on.
Home and End keys are now working as expected, but when I edit some file with vim, the file content remains displayed when I exit vim.
Is it somehow possible to return to previous screen when exiting vim (as it was with the xterm)?

Thanks in advance

---

### Post by Monotoko on 2011-06-29
Hi,

Sadly I don't think it is possible, as puTTY uses something called "pterm" whereas Linux & other distributions use "xterm". Maybe if you go back through the versions you may find one that does as you are after (ref: [http://www.leagueofreason.co.uk/viewtopic.php?f=67&t=6930](http://www.leagueofreason.co.uk/viewtopic.php?f=67&t=6930)) Cgywin may also be a viable alternative to look into :)

Sorry I couldn't help you any more,
Daniel

---

### Post by xxsawer on 2011-06-29
I think its not a putty problem...When I revert the setting described in the first post back to "xterm" everything works and former screen is restored when exiting vim. But when I keep the setting to "linux", the file content remains displayed when exiting vim.
As I wrote above, I found out that putty sets the TERM variable when loging in, so maybe this is some system thing...

---

