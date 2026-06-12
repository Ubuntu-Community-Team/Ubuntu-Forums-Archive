---
title: "clear entire terminal window, not just screen"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by PGScooter on 2009-04-20
Hi, how can I clear the entire terminal window? When running programs over and over I like to have a clear cutoff between one run and the other when I scroll upwards. When I clear (or ctrl-l) it only appears to clear everything but scrolling upwards everything is still there.

Thank you!

---

### Post by philinux on 2009-04-20
If I read you right you mean the contents of this file.

/home/username/.bash_history

This contains previously used terminal commands. The up arrow shows them.
Very useful I'd say. But there you go.

Otherwise click the Terminal tab and use Reset and clear

---

### Post by calrogman on 2009-04-20
Try typing
```
reset
```
It won't delete your history but it will clear the entire terminal, and also fix it if you nessed it up with a binary file, by using, for example
```
cat /usr/bin/firefox
```

---

### Post by ostrm on 2009-04-20
I think, you'd like to clear the scroll-back buffer, such that scrolling up doesn't show the output of preceding commands, right?

I don't know which terminal you use, but to my knowledge there is no alternative to a 'reset and clear' in gnome-terminal, which is annoyingly slow.

There is one terminal emulator however, **mrxvt**, of which I know that it that has this nice feature built-in: Executing a command with Shift-Enter clears the whole scroll-back buffer before execution.

It's just a sudo apt-get install mrxvt away :-)

---

### Post by PGScooter on 2009-04-20
thank you both!

reset was exactly what I was looking for.

---

### Post by aeiah on 2009-04-20
i just hold down return for 5 seconds :P

---

