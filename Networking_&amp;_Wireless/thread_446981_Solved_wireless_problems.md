---
title: "Solved wireless problems"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by JCook21 on 2007-05-17
Hi everyone,

I've just managed to sort out some niggling problems I've had with my wireless networking.  I have a Broadcom BCM4318 card and have installed Feisty.  I managed to get the card to work using Ndiswrapper but I had a few problems.  I couldn't get the Gnome network manager to work with my network and while Wicd worked it wouldn't automatically connect to the network at startup even though it was included in sessions.  I also had problems with passwords in that I couldn't make the network connect with WPA2 and a long password-I had to use WPA2 with the routers default 8 digit password.  I managed to sort all of this out by downloading and installing the latest version of Ndiswrapper from sourceforge and all of the problems disappeared immediately.  Wicd connects on startup, I can use the gnome network manager and I can also use long passwords (my network is now secured with a 64 digit hexadecimal pass code).

Just thought I'd post this in case it helps anyone who's having similiar problems.

---

