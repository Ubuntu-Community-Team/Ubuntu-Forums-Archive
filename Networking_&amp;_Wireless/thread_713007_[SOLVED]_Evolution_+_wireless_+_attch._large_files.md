---
title: "[SOLVED] Evolution + wireless + attch. large files = problem"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by bixejo on 2008-03-02
Hello all.

I'm getting a strange problem with trying to send one e-mail from Evolution in my home wlan with a fairly large file attached, say a few hundred of Kb. After a rather long time, it just says DATA command timed out. I get no problems to send small e-mails nor to receive e-mail of any size. I also get no problem to send large files with Evo using a wired connection.

However, I can successfully send this e-mail from a win-Xp system using Netscape 7.0 mail client (same home wlan, same message, same file, same SMTP server, ... same all.)

I can figure out that this should be some OS dependant config option that I've been unable to find so far.

Any ideas or suggestions will be welcome.
Regards, and thank you in advance,


--
I'm using Evolution 2.12.1 on an Ubuntu-Gutsy x86_64:
$ uname -a
Linux thader-portatil 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

If you need more info just ask!
--

---

### Post by bixejo on 2008-03-06
*bump*

OK, self-answer: The following upgrades were automatically suggested by the update applet:

>  evolution
evolution-common
evolution-plugins

From version: 2.12.1-0ubuntu1 => To version:  2.12.1-0ubuntu1.1
After installing them, the problem vanished. So I conclude that indeed this was some kind of bug in one or more of these packages.

Let's go after the *next* issue / malfunctioning program... My feeling is that I'll have got a fully working and functional installation more or less at the point in which Gutsy won't be supported any more...

---

