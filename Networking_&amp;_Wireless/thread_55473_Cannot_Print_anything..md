---
title: "Cannot Print anything."
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by sheed on 2005-08-09
Hi there...

I'm running Ubuntu Hoary on a Dell d810 laptop. Everything work fine even if bluetooth doesn't seems to be detected (No problem, I'm not using it).

On the network, I  have got a dell M5200 printer .

Linux doesn't seems to have any problems with it. Drivers exists, printer seems to be recognized.

When I open gedit, write "test", then try to print, everything works fine, but ONLY with gedit. If I try to print via "open office 2", "evinve" "firefox" or anything else, it fails.
That is, printer seems to start working correctly. Rollers start to turn, makes a noise, but nothing else. Then, printer and ubuntu seems to think that printing was ok, and stops without any error...

Anyone got an idea ?

Thanks !!

---

### Post by ubick on 2005-08-09
check that both your printer and your applications are configured with the same print format (letter/a4..)

---

### Post by sheed on 2005-08-09
[QUOTE=sheed]Hi there...

I'm running Ubuntu Hoary on a Dell d810 laptop. Everything work fine even if bluetooth doesn't seems to be detected (No problem, I'm not using it).

On the network, I  have got a dell M5200 printer .

Linux doesn't seems to have any problems with it. Drivers exists, printer seems to be recognized.

When I open gedit, write "test", then try to print, everything works fine, but ONLY with gedit. If I try to print via "open office 2", "evinve" "firefox" or anything else, it fails.
That is, printer seems to start working correctly. Rollers start to turn, makes a noise, but nothing else. Then, printer and ubuntu seems to think that printing was ok, and stops without any error...

Anyone got an idea ?

Thanks !![/QUOTE]
 Ok, another tips !

When I wrote "test" in Open office, then try to print, it works...
But if I try to load a document, (.sxw for exemple) with head, tails, and text, it fails...

Looks like a pain in the **** to get it work... (at least to understand where's the trouble).

And yes, everything is configured in A4 format... :(

Same for evince...
Only single text "test" work...

Is there a way to configure cache size or something like this ?

---

### Post by oraknabo on 2006-04-05
I had this exact problem and tried LPD instead of TCP/CUPS and now it works perfectly thanks to [this thread]("http://ubuntuforums.org/showthread.php?p=892708#post892708").

---

