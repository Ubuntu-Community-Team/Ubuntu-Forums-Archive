---
title: "Feisty/Kubuntu: Network operations within most KDE apps hangs randomly"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Pierre-Étienne Messier on 2007-05-23
[LIST]
[*]Upgraded from 6.10 to 7.04, bug started after the upgrade.
[*]Hardware: Dell Inspiron 9300 laptop, Broadcom BCM4401-B0 and Intel ipw2200 network interfaces.
[*]Problem occurs on both wired and wireless interfaces.
[/LIST]

Sometimes, I can't access any KDE network applications. Their display is just froze. This happens quite randomly, for a random period of time then the display is correctly working.

A few examples:
[LIST]
[*]KNemo icons freeze, and clicking on them do not raise the popup window. When the display unfreeze, the popup appears.
[*]When launching a new Konqueror window, the file browser do not display the files until the display unfreezes.
[*]Launching "dcop kded networkstatus status www.google.ca" from a Konsole hangs until the display unfreezes, but DO output 1 on the console.
[*]When the display is "frozen", Kopete is still working though...
[/LIST]

I see no errors in dmesg, nor in /var/log/daemon.log ...  Any ideas or similar experiences?

---

### Post by ubunik on 2007-05-23
I have found that network hangs can often be due to DNS problems.
Are your DNS settings set up correctly as suggested by your ISP?

---

