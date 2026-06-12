---
title: "VPN Can't Get It Installed"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by victor9191 on 2008-10-04
I'm trying to install pptpconfig and it gives me this error. "BREAK (install)". I just want to be able to use my vpn. I have network manager, but I can't even find it. I have a relakks VPN btw.

---

### Post by digao45 on 2009-04-15
I think network manager is located in the net's applet, at top right. click on it.

and
the pptpconfig seems to be old in ubuntu:

*"On distributions that support NetworkManager, pptpconfig is deprecated in favour of the PPTP Plugin for Network Manager. On Ubuntu and derivatives the package name is network-manager-pptp."*

[see here]("http://quozl.netrek.org/pptp/pptpconfig/pptpconfig.phtml")

---

### Post by apanloco on 2009-04-24
Have you managed to get this working? I have tried both 8.10 and 9.04 now with Relakks and it just doesn't work. Credentials are right since it works in windows. It just said Connection to VPN failed. Nothing more. I'm using network-manager-pptp.

---

### Post by apanloco on 2009-04-24
LOL when I posted this I just got an idea. Maybe I can only have one connection at a time (always connected on my windows machine). I disconnected on Windows and now it works :-) I had to check use MPPE under advanced settings though. Hope this helps someone.

---

### Post by SabreWolfy on 2009-04-24
Strange co-incidence. I've just been trying to install pptpconfig myself. The project homepage lists links to php-pcntl and php-gtk-pnctl which I downloaded (deb files). I could not install them though, because of many broken dependencies. The files are dated from 2004 and 2006. I don't know if it is possible to install them under Jaunty. One of the packages required is "libglade0" which I could not find. I have managed to get PPTP VPN working in Jaunty this evening though -- I'll make a separate post for that shortly.

---

### Post by SabreWolfy on 2009-04-24
For what it's worth, I found a solution to PPTP VPN in Jaunty (and presumably Intrepid too). Link [here]("http://ubuntuforums.org/showthread.php?t=1136020").

---

