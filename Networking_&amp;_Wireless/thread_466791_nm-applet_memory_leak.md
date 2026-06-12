---
title: "nm-applet memory leak?"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by greg.hagen on 2007-06-07
Since upgrading to Feisty, my network card has worked splendidly without needing windows wireless drivers. However, after my computer is left on for about 3 days all programs become sluggish and the hard drive thrashes constantly. Launching the system monitor reveals that all programs are running normally... except nm-applet which is using up 80+ megs, It's a pretty old computer, so this is a huge performance problem.Killing and relaunching nm-applet removes the system sluggishness and nm-applet begins it's slow crawl back up from 2.1 megs again.

Is this normal? If not, where and how do I file a bug report?

---

### Post by spd106 on 2007-06-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/106262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/106262) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				To create a bug report or add any information you must first create an account on launchpad.
There is a similar bug open, though there isn't much information on it.

---

### Post by greg.hagen on 2007-06-12
Oddly enough, I can no longer reproduce this problem. I installed a few updates in the last week and added my hostname to the first line of "/etc/hosts". Now the system is nice and quick with an uptime of 3 days. Thanks for the info, though.

---

