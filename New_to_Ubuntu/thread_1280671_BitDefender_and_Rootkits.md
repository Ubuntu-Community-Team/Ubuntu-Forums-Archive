---
title: "BitDefender and Rootkits"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-10-02
Hi all, hope your all doing very well.

I have another question if thats ok?

Info = I dual boot between Vi$ta and UB 9.04

Ok, a friend of mine's PC has a rootkit (don't know yet if it was his
Mac or Win box). Anyway, due to this (and unbeknownst to him, his mail
account was sending out spam email).

Now, I opened his mail in Linux using firefox from my webmail account.
BUT I DIDN'T click on any links is the message. And then deleted the
message.

I've ran an exhaustive scan from Windows using Kaspersky, and I've just
installed BitDefender on my linux partition. Both apps say I'm clean.
(I understand that Kaspersky's only gonna tell me that my Win partition is clean,
so Its not much help for my Linux partition).

However Does BitDefender also scan for rootkits? I have also installed rk hunter
from the repositories, but I cant find it on my system (gahhh).
I've just ran it from the terminal it seems to be there, but I was
hoping for a GUI version.

Any help or advice would be greatly appreciated.

---

### Post by cariboo on 2009-10-02
Windows exploits don't work in Linux. Most Linux anti-virus programs only scan for Windows viruses.

There are several rootkit scanners available in the repositories, rkhunter and chkrootkit are the most common. Tiger which is also in the repositories is another program you may want to try.

As far as I know, clamav is the only av program that claims to scan for Linux viruses, it is also available in the repositories.

Generally you don't need an av scanner in Linux, as there are no viruses in the wild. Do watch out for social engineering, that could cause you to install some sort of malware.

The biggest security risk running Linux is the user, so use a strong password, and browse safely.

---

### Post by FreewheelinFrank on 2009-10-02
You have nothing to worry about. Relax.

---

### Post by LewRockwell on 2009-10-02
[http://en.wikipedia.org/wiki/Rootkit#Hardware.2FFirmware](http://en.wikipedia.org/wiki/Rootkit#Hardware.2FFirmware)

.

---

