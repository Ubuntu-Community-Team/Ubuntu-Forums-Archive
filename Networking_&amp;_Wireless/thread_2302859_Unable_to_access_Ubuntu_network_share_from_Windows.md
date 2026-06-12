---
title: "Unable to access Ubuntu network share from Windows, Ubuntu web interfaces are down"
date: 2015-11-14
forum: Networking &amp; Wireless
---

### Post by matthew120 on 2015-11-14
[COLOR=#111111][FONT=Ubuntu]First off I am very much a novice!
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have a home media server running Ubuntu server 14.04.3 LTS[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
On Thursday evening, after months of smooth operation, web interfaces for webmin etc. became unavailable. I tried to connect via the browser on my phone and from Firefox and Chrome on my Windows 7 PC.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I then tried to connect to the network share via Windows 7 which timed out and failed to access.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I tried to connect via PuTTY which also timed out and failed.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I pinged my server from Windows and all packets were lost (Destination host unreachable).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I then hooked up a keyboard and monitor to my server to check it out. I was able to log in and navigate through folders. The Webmin service was running, so too was SSH and my Ubuntu firewall was disabled. It also had access to the internet.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
At this point I tried to access the network share via my Android phone and Kodi on my Raspberry Pi. Both of these devices were able to access the share, stream videos, music and open pictures without any issue.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I did not make any manual changes to my server or my router and I had automatic updates off. It was working normally Thursday morning, I shut it down and headed for work. And when I turned it back on Thursday evening is when all these problems arose.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
In my attempts to fix it. I performed all the updates, of which there were 87, on Friday night. But this didn't resolve my issue.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Any advice to get access to my server via the web and through Windows would be greatly appreciated. If you need more information please let me know and I'll try and get it for you.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Thanks very much,[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Matt[/FONT][/COLOR]

---

### Post by tripp98 on 2015-11-14
did the ip address change?  on the server type ifconfig and verify that your still on the same IP.

---

### Post by matthew120 on 2015-11-14
You are absolutely right! It makes perfect sense now and I can't believe I didn't think to check that.

Suppose I need to look into setting up a static IP so as I don't embarrass myself like this again :-\"

Thank you

---

### Post by matt_symes on 2015-11-14
Hi

As this is fixed, I'll mark this thread as [solved] for you.

Kind regards

---

