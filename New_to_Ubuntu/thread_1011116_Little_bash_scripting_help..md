---
title: "Little bash scripting help."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by RATM_Owns on 2008-12-14
What I need is:

1. Grep a number from `svn update` (Updated to revision ##, I just want to save the number into $REVISION)

2. Use said number to use sed to search and replace the old revision number with the new one (I'll just use some text around the number and a wildcard to find the old number)

Is it possible to do that in bash scripting so I can start the script and let it do everything with be being lazy and not touching anything?

---

### Post by malathion on 2008-12-14
This probably doesn't belong in Absolute Beginner Talk :) Have you tried looking at the guides on linuxcommand.org? They are good scripting manuals for newbies (if you are one...)

---

### Post by snova on 2008-12-14
I think SVN has something similar builtin. Like $Revision$ or something. I think you have to set a file attribute before it'll do it...

---

### Post by andrew.46 on 2008-12-16
Hi,

The initial command would be 'svn info'. A demo with the svn MPlayer for example:

```
andrew@skamandros:~/mplayer$ svn info
Path: .
URL: svn://svn.mplayerhq.hu/mplayer/trunk
Repository Root: svn://svn.mplayerhq.hu/mplayer
Repository UUID: b3059339-0415-0410-9bf9-f77b7e298cf2
**[COLOR="Red"]Revision: 28145[/COLOR]**
Node Kind: directory
Schedule: normal
Last Changed Author: diego
Last Changed Rev: 28145
Last Changed Date: 2008-12-13 23:33:22 +1100 (Sat, 13 Dec 2008)

```

So to extract the Revision number something like this would work:

```
andrew@skamandros:~/mplayer$ svn info | grep '^Revision: ' | sed 's/^.\{10\}//'
28145
 
```

And to use this as a variable in a script something like:

```
REVISION=$(svn info | grep '^Revision: ' | sed 's/^.\{10\}//')
```

Does that furnish you with at least a starting point?


  Andrew

---

