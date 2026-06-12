---
title: "Networking (wifi) latent/unusable in X but fine in a vc?"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by avsa242 on 2007-10-18
I have a rather strange problem.
I have a Compaq C550 laptop (C552US) with integrated WiFi.
I have upgraded from Feisty to Gutsy.
I am using ndiswrapper.

The problem:
The computer boots up, the WiFi card associates with my AP and receives an address. Any network access is unusably slow. Pinging either of my APs, I can see that most packets are dropped and those that are returned have a very long rtt (mostly 1-2sec+).
However, here's the kicker: if I switch to a vc (using Ctrl+Alt+F#; not logging out or killing X), network access is slick as it should be, with no or minimal dropped packets. [EDIT: Incoming traffic is fine as well; e.g., if I ping this machine from another the latency is normal). A bit of a longshot, but I thought perhaps somehow the video card was assigned overlapping resources (io, irq, etc) with the WiFi card - it is not.
Please note I am still using the 2.6.20-15 kernel from Feisty. I wanted to use the 2.6.22-14 as shipped with Gutsy so I could try the in-kernel bcm43xx driver, but unfortunately that has an even nastier still problem: the machine locks up hard at a somewhat random time after the gdm login screen (usually after logging in).

The WiFi is an internal miniPCI Broadcom 4311 (according to lspci, rev 01)
Video is i945GM.

Cheers,
Jesse

[EDIT: I got this working. I can confirm this appears to be a conflict of sorts with the "intel" X server; I thought for sure I had tried this but apparently not: using the legacy i810 server instead solves this problem for me. There doesn't appear to be any remotely pertinent information in any system logs, X startup log, etc.
drm module version is 1.1.0 20060810
i915 module version is 1.6.0 20060119]

---

