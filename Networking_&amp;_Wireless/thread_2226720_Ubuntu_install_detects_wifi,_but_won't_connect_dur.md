---
title: "Ubuntu install detects wifi, but won't connect during install"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by Andrew_Brennan on 2014-05-28
Hi guys,

wondering if anyone has encountered a similar issue to me. I've been a long time Ubuntu user and wanted to install the latest version. But I'm encountering a little challenge and wanted to see if anyone knows what the cause is.

To cover some brief history. I have 2 routers in my house. One is a newer router (2years old), using WPA to manage connections. The second is an older one, using WEP. The newer router has been acting up lately and I've reverted to the older one temporarily.

The problem I'm having is as follows:

A Ubuntu install goes perfectly fine from the newer router.
however, the install won't connect to the older router during install. It detects all network connections fine and I can connect to both mine and neighbours wifi connections. However, when I initiate the installation it re-prompts me to connect to a wifi connection and when I select my wifi connection the 'connect' button is greyed out. However, I can connect to pretty much any other wifi connection.

basically, my ubuntu install will connect and install fine to every other wifi router, except my older router. I never had this problem the last time I installed ubuntu (11/12 versions of ubuntu).

once installed, there are no issues connecting to the wifi router. The problem only occurs during installation.

it's not a router problem, as I've noticed FileZilla also goes considerably slower when using this wifi connection on Linux. However FileZilla goes perfectly fine, when, using this wifi connection on Windows 7.

the incompatibility between this specific router, with the latest versions of ubuntu is the problem. I can't figure out where the hiccup is coming from. It's not a problem that I can't find a way around, but interested to see what is causing it.

anyone experience this problem before? Google hasn't helped at all.

---

### Post by mörgæs on 2014-05-29
> **Andrew_Brennan said:**
> 
once installed, there are no issues connecting to the wifi router. The problem only occurs during installation.


Hi, welcome to the fora.

The best you can do is always install and apply updates using a wired internet connection. When that is done and everything is stable it's time to focus on the wirefree.

Buntu (as any other operative system) is buggy at release date and it might affect network connections too. When updates have been applied Trusty lives up to its name.

---

### Post by Andrew_Brennan on 2014-05-29
Yeah I understand that I can just do that. But there is an issue between Ubuntu and this specific router. After updating and installing correctly. FileZilla only on Ubuntu and when used with this specific router, goes particularly slow. There is just a few "anomalies" that I am experiencing with the last few Ubuntu versions and this specific router. It's more for piece of mind and ensuring I understand the reasons behind the problem, given that it is my work machine, as well as my personal machine. I like to educate myself a bit on the configuration of my machine i guess.

The most obvious issue is during installation from a live USB, in which despite connecting to this router and the internet working in a browser, the installation wizard still has an "X" beside "is connected to the internet". But this ONLY occurs with this router. And its not my PC's problem, as it happens on ALL PC's in my house, when booted from a live USB and with this router. It's really a strange problem [CENTER][COLOR=#000000]:confused:[/COLOR][/CENTER]

---

### Post by mörgæs on 2014-05-29
Have you checked if the router firmware needs updating?

---

### Post by Andrew_Brennan on 2014-05-30
Yeah I am working on updating the firmware. But the router providers website is giving me problems. :-/

i found a launch pad bug that is the exact same as my issue.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/940334](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/940334)

i have the same output for
wget -q [http://start.ubuntu.com/connectivity-check.html](http://start.ubuntu.com/connectivity-check.html) --timeout=15 --tries=1 -O - | md5sum

and I've tried multiple PCs to see if the erro persists. Additionally, I've tried older ubuntu versions (as far back as 11.04) and this still is happening. This hasn't been an issue with these versions before, leading me to believe it's solely a router issue. :-/

---

