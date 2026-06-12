---
title: "Internet Very Slow 15.04 But Not 14.04"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by 7-webmaster on 2015-07-16
For the last 5 days from my laptop running 15.04 all access to the internet is excruciatingly slow with frequent timeouts.  However there is no problem with a desktop running 14.04 that is connected to the Internet through the same modem.  Rebooting the laptop does not improve the performance.  Rebooting the modem provides temporary relief but then the poor performance returns.  The problem was so persistent that my ISP even replaced the modem for me.  The problem started quite suddenly five days ago, when there had been no change in the modem.  The ISP tech even remarked on the fact that the modem log showed that it had not been powered off for several months.  However I had applied a routine set of updates to the software on the laptop, including a change to webkitgtk but nothing else that I can see as relevant to the issue.  I have reported the problem on Launchpad, which has further information. [https://bugs.launchpad.net/ubuntu/+source/webkitgtk/+bug/1473794](https://bugs.launchpad.net/ubuntu/+source/webkitgtk/+bug/1473794).  The network manager icon is behaving strangely.  Even though it has connected both to the ethernet port and the Wi-Fi it continues to cycle as if it is trying to set up some other connection, even though there are no other defined connections available.

Since 14.04 is unaffected, and the problem popped up suddenly on 15.04, I am assuming that the problem is in 15.04 and not in the modem, even though rebooting the modem solves the problem temporarily.

I would appreciate any suggestions about how to identify exactly why this is happening.

---

### Post by weatherman2 on 2015-07-16
The fact that you are running 14.04 on entirely different hardware from your 15.04 laptop doesn't mean anything about some problem in 15.04 but not in 14.04.  It means that different hardware works differently in Linux.  Some hardware - particularly wireless cards - has better support in Linux than other hardware, in any version.

Try to remove some of the variables.  First of all, disable WiFi on the laptop temporarily and see if the problem persists with a wired-only connection.  If it works fine when wired, then you know you have a WiFI problem.  (Typically, you should connect one way or the other - wired or wireless, not both, anyway.)

If you find you are having a WiFi problem, then run the wireless script in the sticky post at the top of this forum and post the results here.  Perhaps only some tuning of your wireless card driver is required - but no one can offer many meaningful suggestions without knowing exactly what hardware you are using (e.g. what type of wireless card), and the wireless script will indicate that.

---

### Post by 7-webmaster on 2015-07-19
> **weatherman2 said:**
> The fact that you are running 14.04 on entirely different hardware from your 15.04 laptop doesn't mean anything about some problem in 15.04 but not in 14.04.  It means that different hardware works differently in Linux.  Some hardware - particularly wireless cards - has better support in Linux than other hardware, in any version.

Try to remove some of the variables.  First of all, disable WiFi on the laptop temporarily and see if the problem persists with a wired-only connection.  If it works fine when wired, then you know you have a WiFI problem.  (Typically, you should connect one way or the other - wired or wireless, not both, anyway.)

If you find you are having a WiFi problem, then run the wireless script in the sticky post at the top of this forum and post the results here.  Perhaps only some tuning of your wireless card driver is required - but no one can offer many meaningful suggestions without knowing exactly what hardware you are using (e.g. what type of wireless card), and the wireless script will indicate that.

You are not understanding the problem.  Firstly I did not say anything about wireless.  Of course my laptop has a wireless port, but it is also attached by Ethernet to the hub most of the time.  Since it is admittedly a requirement for this forum even if I am not reporting a wireless problem, I have attached the required wireless info.  Secondly this suddenly started happening after _years_ of no networking problems whatsoever.  The ISP technician was actually surprised that I had been able to go so long without ever rebooting my modem, but then most of his customers run Windoze.  The problem is NOT in the hardware because the hardware did not change.  The problem is NOT in the modem, even though rebooting the modem temporarily resolves the problem, because the modem had not been changed in over 6 months and even the software in the modem had not been rebooted so it was the exact same software and exact same configuration.  I installed 15.04 on my laptop the moment it became available to download because on all previous releases of Ubuntu my laptop would not resume when the lid was opened, so I have been running 15.04 for many months now with no problems.  Then suddenly at 7pm Friday July 10th network performance started to suck.  Also the icon of the network manager has been weird throughout this issue.  It continues to show the "trying to connect to WI-FI" icon rather than the bi-directional arrow icon, even if I disable WI-FI.  If I never shut my laptop I have not observed any performance problems.  My primary concern is not to fix network performance, since rebooting the modem does that, and I can do that any time my wife is not watching TV (our TV signal comes over the Internet, which reminds me that obviously our PVR is not observing any performance problems).  My primary objective is to collect whatever information is necessary to diagnose the problem so that whatever bug was introduced into my system a week ago gets fixed.  The following is all installs in my system in the last week and a half.  I have no idea how to identify which one is to blame.  The problem was first observed 3 days after the last kernel install.

2015-07-07 04:21:45 install linux-image-3.19.0-22-generic:amd64 <none> 3.19.0-22.22
2015-07-07 04:22:16 install linux-image-extra-3.19.0-22-generic:amd64 <none> 3.19.0-22.22
2015-07-07 04:22:34 install linux-headers-3.19.0-22:all <none> 3.19.0-22.22
2015-07-07 04:23:06 install linux-headers-3.19.0-22-generic:amd64 <none> 3.19.0-22.22
2015-07-09 18:19:57 install chromium-browser:amd64 <none> 43.0.2357.81-0ubuntu0.15.04.1.1170
2015-07-09 18:20:08 install chromium-browser-l10n:all <none> 43.0.2357.81-0ubuntu0.15.04.1.1170
2015-07-09 18:20:50 install libjavascriptcoregtk-4.0-18:amd64 <none> 2.6.2+dfsg1-4ubuntu1
2015-07-09 18:20:51 install libwebkit2gtk-4.0-37:amd64 <none> 2.6.2+dfsg1-4ubuntu1
2015-07-09 18:20:56 install epiphany-browser-data:all <none> 3.14.2-0ubuntu1
2015-07-09 18:20:58 install gnome-icon-theme:all <none> 3.12.0-1ubuntu1
2015-07-09 18:21:00 install gnome-icon-theme-symbolic:all <none> 3.12.0-1
2015-07-09 18:21:01 install epiphany-browser:amd64 <none> 3.14.2-0ubuntu1
2015-07-09 18:22:15 install bluefish-data:all <none> 2.2.6-2
2015-07-09 18:22:16 install bluefish-plugins:amd64 <none> 2.2.6-2
2015-07-09 18:22:17 install bluefish:amd64 <none> 2.2.6-2
2015-07-09 18:24:51 install libjavascriptcoregtk-1.0-0:amd64 <none> 2.4.8-1ubuntu2
2015-07-09 18:24:52 install libwebkitgtk-1.0-common:all <none> 2.4.8-1ubuntu2
2015-07-09 18:24:53 install libwebkitgtk-1.0-0:amd64 <none> 2.4.8-1ubuntu2
2015-07-09 18:24:56 install gphpedit:amd64 <none> 0.9.98-3
2015-07-13 21:25:31 install vsftpd:amd64 <none> 3.0.2-18ubuntu1

---

### Post by wildmanne39 on 2015-07-19
Hi, your ethernet is slow because you are using the 8169 driver and you need the 8168 driver and yes we learned that because you posted the information from the wireless script, however that is one of very few things the script tells us concerning ethernet connections so it was just lucky that it is useful in your case.

Please do:
```
sudo apt-get install r8168-dkms
```
I do not think the 8169 driver needs blacklisted because think that is done automatically when the new driver is installed.
It is just a miracle you have not had that issue with other version of ubuntu because it has been around a long time.
Reboot

---

