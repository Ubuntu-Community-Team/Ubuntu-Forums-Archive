---
title: "Per application rules in iptable"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by dimanne on 2014-02-01
Is there possibility to add rule via iptable for specific process name?

Good explanation of why I need it is [here]("http://forums.opensuse.org/showthread.php/399236-Controlling-outgoing-traffic-per-application"):
[COLOR=#333333]"Under Windows, this helps making the PC more secure. There are many applications that "phone home" over standard ports, i.e. send information about behavioral patterns of the user (e.g. Real Player, Adobe Acrobat Reader, WinAmp, etc.), or surf the internet for whatever it is they do. Many applications send information every time an application is started to the Microsoft registration server, generating a usage pattern. While most of this information is rather harmless, once in a while you encounter an application that sends data you would rather not have in the public.[/COLOR]
[COLOR=#333333]It was always quite interesting to see what a newly installed application would want to send out to the internet. "[/COLOR]

I googled that there WAS option -m owner --cmd-owner, but what to use now?
Or may by analogue of that option will be available in upcoming nftables?

---

