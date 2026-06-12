---
title: "Broadcom/Wifi connection drops - power-saving mode in Linux 4?"
date: 2016-05-12
forum: Networking &amp; Wireless
---

### Post by rjvbertin on 2016-05-12
Hi,

Edit: seems I'm not the only one with this kind of issue:

I'm running KUbuntu 14.04 LTS, up-to-date but since quite a while I use a home-built 3.14 kernel (3.14.59 with ConKolivas patches). This is on an Acer AO722 netbook with a BCM4313 802.11bgn WiFi controller, for which I use the bcma-pci-bridge . I know I could use the bcmwl driver for this device, but the bcma driver has always worked well enough.

I recently built and installed a mainline 4.5.2 kernel, configured with the config of the lts-xenial kernel for 14.04 (minus AppArmor and without the ConKolivas patches). 

I've always had the phenomenon where ssh/slogin connections to another host on the local network would freeze (direct X11 connections a bit less). That host is connected via wired ethernet, so I chalked those freezes down to something at the level of the WiFi connection, because it's definitely worse when I connect to another Linux host over a WiFi -> WiFi link.
I didn't notice it immediately, but the last few days those freezes or drops have become significantly worse, to the point where akonadi complains about dropped IMAP connection (and I thus end up restarting Kontact and sometimes all of akonadi). I have almost the same KDE PIM version running on my OS X workstation and there I'm seeing no signs of dropped connections, so the remote mailhost (gmail...) isn't to blame, nor my internet connection. I'm also not getting dropped packets doing a ping of an external host on OS X, while I do get them on Linux.

I'm currently back under 3.14.59 to see if that makes a difference; I cannot yet comment on that.

Has anything changed ("improved") in Linux 4, at the level of WiFi device power management for instance? This really looks as if the WiFi connection is suspended, without any feedback of that in the panel. I remember that I had connection drops when I tried Sabayon and OpenSUSE before settling on Ubuntu, but there I definitely saw them happen in the panel.

I could try the bcmwl driver under 4.5.2, but I'm a bit hesitant as I'm not sure how easy it'll be to roll back should it not improve things (or degrade under 3.14) ...

Thanks in advance ...

---

