---
title: "VPN &amp; Proxy server"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by osborni on 2011-06-21
So... (total noob for Ubuntu/linux)

What I want to do is set up a VPN and proxy (I think) server so that I can connect my iPad from work or hotspots and have some security.

Side note is that the only way I can connect an iPad at work is through a VPN since the IT dudes don't like equipment that they don't own accessing the network.  They use a VPN so they can't be accused of sniffing proprietary information from visiting suppliers.  (I work at a big multi-national manufacturing corporation...)

Yes, there are paid services, but that's not the point of having a linux box running at home now is it? :)

Anyway, the topology that I imagine that I need is:

[wireless iPad out on the internet]=>=[VPN]=>=[home firewall]=>=[proxy server]=>=[back out to the internet]

The Ipad can only connect through a VPN with PPTP, L2TP or IPSec protocols.

I can connect to my XP home machine with PPTP with no issues, but it won't (for some reason) let me get back out to the internet.  It's also my wife's primary machine so I don't want to mess with it too much.  She also has an annoying habit of putting it into standby mode when she's not using it. :)

Links to help files and basic pointers would be cool.  I'm totally ignorant of all but basic home networking and need some pointed for the right language and terminology to use.



So far I have samba running and connected a NAS raid dlink box and have internet access to Sockso music player (though I doesn't work on the ipad...  cool but pointless so far.)  I'll eventually get a home distributed music server set up, but that's for later.

---

### Post by osborni on 2011-06-21
Or is there a better way?  (my only real consideration is that it be free... or nearly so.)  VPN > Bridge > internet?

---

### Post by osborni on 2011-06-22
I made progress.  The hardest part was figuring out what to search for in google.  "unbuntu vpn pptp" yielded a bunch of how-tos to git-r-done.

An odd thing though.  When i connect my ipad to the server through VPN, the pptp apparently closes out the internet connection for the server's browser.  I get a DNS error.  Not really a huge deal as I normally won't run a VPNed ipad and browse the web on the server PC, but still.  Any ideas?

---

