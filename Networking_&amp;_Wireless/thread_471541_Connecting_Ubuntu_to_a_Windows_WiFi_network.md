---
title: "Connecting Ubuntu to a Windows WiFi network?"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by santuccie on 2007-06-12
Hi,

I've installed Ubuntu 7.04 x86 on my Compaq Presario SR2150NX, on which I have a Linksys WMP54G wireless PCI adapter installed.  I'm happy to say the installation was cakewalk, as Ubuntu automatically detected and installed each and every component (even my printer!!!) without any intervention from me.

I'm running a WiFi network on a Linksys WRT54GS router to share my Comcast cable connection, which I'd been accessing from Windows XP Pro Corporate until now.  I have my wireless PCI adapter setup as my primary networking device, and it sees my network, but it will not connect to the network.

I'm an experienced Windows user, but quite new to Linux.  I've caught glimpses of things like "samba" and "ndiswrapper" on the web, but haven't a clue which of them, or if either of them, can address my problem.  Is there anyone who has encountered this problem before, who might be able to explain in layman's terms how I might set about resolving this issue?  If there's something I need to do with the XP Home machine that is hard-wired to the router, I may catch on easily.  But as far as Ubuntu is concerned, consider me a novice.:-k

Thanks!

-santuccie

---

### Post by Jussi Kukkonen on 2007-06-12
Forget samba for now (it's for file sharing). A google search for "linux Linksys WMP54G wireless PCI" gives at least this:
[http://maxp.net/computers/wmp54g-linux.html](http://maxp.net/computers/wmp54g-linux.html)
and a few clicks gets you here:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

If you are ready for a bit of work, I suggest trying the second link: using native drivers is usually the best choice -- They will probably eventually end up in Ubuntu, and you an expect the drivers to get  better and better over time. Use ndiswrapper only if they don't seem to work properly.

EDIT: I missed the part where you said it's kind of working already -- **the instructions I linked to could be old, and everything might work fine in Feisty**... Have you tried removing WPA/WEP encryption on the router?

---

