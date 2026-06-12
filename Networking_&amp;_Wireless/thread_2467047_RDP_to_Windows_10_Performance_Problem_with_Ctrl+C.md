---
title: "RDP to Windows 10 Performance Problem with Ctrl+C"
date: 2021-09-14
forum: Networking &amp; Wireless
---

### Post by calmdownmonkey2 on 2021-09-14
Hi,

I want to RDP to my workplace's Windows 10 laptop from my Ubuntu 21.04 PC so that I can re-use my desk setup for work, but there is a performance problem preventing me from using it properly.

The laptop is connected to the same router. Everything works okay from Windows 10's Remote Desktop client, but if I use Remmina from Ubuntu, everything freezes for 10 seconds if I try to Ctrl+C anything on the laptop. It looks like it's the Remmina client itself freezing, because during a freeze I can't access the sliding menu at the top of the screen (where you can connect, minimise, etc, the RDP session). Everything displayed on the RDP session is frozen too - e.g., Performance Monitor. Then after 10 seconds it will all suddenly resume (I can tell I've missed 10 seconds of action).

Through experimentation I've discovered:
[LIST]
[*]It happens 80% of the time - I can't find a pattern.
[*]It doesn't seem to matter whether I use Ctrl+C or "Copy" from the context menu. It also doesn't seem to matter what I'm copying and what app I'm in (MS Word, Excel, Outlook, a basic Markdown editor, etc).
[*]The performance monitor on the laptop shows nothing of note when I Ctrl+C (no CPU spikes etc)
[*]The performance monitor on the Ubuntu PC shows nothing of note either (no CPU spikes etc)
[*]Disabling clipboard syncing on Remmina doesn't make a difference
[*]Flipping open the laptop and trying the same Ctrl+C on the real laptop itself - it's always instant
[/LIST]

My Remmina settings seem fairly unremarkable... 
Security protocol negotiation: TLS
Gateway transport type: Auto
Audio: Local
Enable multitransport protocol (UDP): Checked
Network type: LAN
Quality: Best 
Server: 192.168.1.47
No Shared folders
Smooth scrolling disabled
Multi monitors enabled

Can anyone offer a suggestion, or help teach me how to debug what's happening a little more?

Thanks a lot!!

---

