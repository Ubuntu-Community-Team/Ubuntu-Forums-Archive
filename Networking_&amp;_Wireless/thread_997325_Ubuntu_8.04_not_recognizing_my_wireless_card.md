---
title: "Ubuntu 8.04 not recognizing my wireless card"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by HunterAmacker on 2008-11-29
I just used Wubi to install Ubuntu 8.04 on a family member's laptop. Everything works fine, except for the wireless card. When I go to System > Administration > Network, the only thing under the connection tab is "Wired connection" and "Point to point connection." I would assume their would also be  a 'Wireless connection' option if the wireless was being recognized. 

The Wireless card in question is a "Intel Corporation PRO/Wireless 2200BG"

---

### Post by J172 on 2008-11-29
By the clock, see if there is a little Network Interface Card graphic with a triangle/exclamation mark or padlock on it. If so click it. It might require Restricted (non-free) drivers. However, I have the same card, and it worked right out of the box, but I also clean installed Ubuntu Ibex. (If that fails you could try [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net)). I doubt this will help, but you could check it out.
[http://ubuntuforums.org/showthread.php?t=996573](http://ubuntuforums.org/showthread.php?t=996573).

It might need a patch.

I think the problem might lie in that it was installed with Wubi but I can't say for sure. Any ideas anyone?

---

