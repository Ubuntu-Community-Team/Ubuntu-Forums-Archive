---
title: "Wake on LAN seems to be enabled by default on Xubuntu 14.04, how do I disable it?"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by argonvegell on 2014-09-27
I just upgraded from Xubuntu 12.04 to 14.04, and I noticed that whenever I shut down my PC, the LAN light of my modem doesn't turn off and the Network adapter behind my PC is still on after shut down.

According to JKyleOKC in [http://ubuntuforums.org/showthread.php?t=2246013](http://ubuntuforums.org/showthread.php?t=2246013)
> **JKyleOKC said:**
> It's possible that the network adapter in your  PC has the "Wake on LAN" feature that allows the box to be turned on  remotely via a command received over the LAN. For that to work, the  network adapter has to remain powered up after the rest of the box is  turned off. It's also possible that some change in a network driver is  causing such a feature to be activated, when it never was before.

I'm seeing a slightly similar situation in my newly installed 14.04  system, that didn't happen with 12.04. In my case, one of the network  adapters (the box has three, but only two are in use and the third is a  spare) introduces several seconds of delay after powering on, to  initialize the PXE boot-over-LAN feature -- which I do not use and don't  know how to disable. What's more, that delay is coming from the **spare**  network card! With 12.04, that did not happen during boot-up, so I  suspect we may be seeing two different aspects of the same change. I  don't know whether to call it a bug or not, though...

It seems that Wake on LAN is enabled by default on Xubuntu 14.04, since in 12.04 I didn't experience this, how do I disable it?

---

### Post by argonvegell on 2014-09-28
I seemed to have solved my own problem.
[http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/](http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/)

I followed the steps outlined in this site and WOL is disabled.

---

