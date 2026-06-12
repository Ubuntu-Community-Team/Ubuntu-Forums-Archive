---
title: "Dial-up Connection"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by RjsGuitar on 2007-12-25
I am a Ubuntu newbie using Ubuntu 7.10.
. My ISP is Dial up. I need to be able to dial a connection through my external modem.
With Ubuntu 6.10 I was able to download a dialer and access the internet with KPPP.

I downloaded KPPP but when I attempt to install it, I get a dependency error, KDlibs4C2A

What do I need to do to get a dial up connection?

Thanks

RJS:guitar:

---

### Post by _duncan_ on 2007-12-25
KPPP requires a lot of KDE library packages, not just KDLibs4C2A. Even if you download the said package from another computer, the installer will keep asking for other packages until all dependecies are satisfied. This is what people refer to as "dependency hell".

It's ironic, but the easiest way to install KPPP is if your ubuntu machine is already connected to the internet. Otherwise, you will have to go through about 30 MB of downloads spread over 8-10 packages.

My suggestion is to try connecting using one of the built-in command line dialers like pppconfig or wvdial, then use synaptic package manager to install KPPP. Details on these dialers can be found in the 2nd link of my signature (Dial-Up Modem Wiki).

---

### Post by RjsGuitar on 2007-12-26
Thanks to Duncan for your reply. 

I will try to get to my ISP via one of themethods you link to.

---

