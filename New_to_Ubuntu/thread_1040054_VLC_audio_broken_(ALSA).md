---
title: "VLC audio broken (ALSA)"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by HavocXphere on 2009-01-15
[SOLVED]

I've lost audio on VLC. Amarok and system sound is still working.

Logged in one morning and it was gone....was still working when I shut it down the previous day. However, I think I broke when I tried to remove some PulseA packages that I had installed. I've tried reinstall everything I removed, but no joy.

So Amarok is pumping through ALSA but VLC isn't. How do I work out whats wrong.?:confused:

If I had to guess, I removed some VLC plugin that interfaces with ALSA.

If someone could throw in a fix/suggestion to solve the "Only 1 app controls sound at a time" problem then I'd be grateful too.

Sound is going through a MS USB headset...but it has worked 100% in the past, so I don't think the issue is there.

Thanks:KS

VLC 0.9.4
Kubuntu 8.10 x86
KDE 4.1.3

---

### Post by HavocXphere on 2009-01-18
For future reference:

The issue is the device selection. In the "simple" prefences display view, no devices are selectable. To get audio back, select "all"/advanced prefences view select Find the ALSA submenu and select the correct device there.

---

### Post by gareththomasnz on 2009-10-27
dude thats not a clear explanation of what to do !!!

For starters I assume you are talking about the settings in VLC - what you mean by "all" I have no idea.

In the advanced screen I see nothing referring to ALSA

---

### Post by smallming on 2009-10-30
Under VLC preferences, choose 'All' in 'Show settings'.

Then, on the tree menu, select Audio > Output modules > ALSA.

Finally, in the drop-down menu, select your device (instead of 'Default'). Save and you are good to go :)

---

