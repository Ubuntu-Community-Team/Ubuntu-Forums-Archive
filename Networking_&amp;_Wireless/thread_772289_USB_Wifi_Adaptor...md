---
title: "USB Wifi Adaptor..?"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by spick on 2008-04-28
Hey Gang,

I am a new user of ubuntu and just installed the latest release on my Windows box via Wubi. The installation went well enough and I am pleased with the performance and feature set of the Hardy Heron release.

I am experiencing intermittent wifi connection issues. Initially wifi wasn't working well at all until I disabled WEP on my wireless router. Once I did that the connection and speed was much better.

My wifi adaptor is a D-link USB device. I don't have the exact model number with me at the moment, I can add that later today if necessary. The connection will work fine for some time and then suddenly the connection will break, it will drop in signal strength and just not resolve any connections. If I unplug the USB device and plug it back and reconnect to the router it will continue to work for some time.

I also have an external USB hard drive connected to the computer and this morning I thought I noticed a connection issue after accessing the drive. Is this possible? Could the two devices be interfering with each other?

If I can resolve this issue, and find a way to stream my media collection to my 360, I may configure a dedicated partition on the drive for a proper installation.

Thanks for your time,

Steve Pick
St. John's, NL
Canada

---

### Post by bitterbug on 2008-06-07
Hey Steve
Shouts out to the celtx forum. :)

Did you get your Dlink adaptor online consistently since the post? I just moved and am now trying to get a DWL-G122 to work, but the network manager is acting flaky and keeps forgetting the settings as soon as I close it.

If I can actually get online with it, I'll see if there's any connection stability issues.

---

### Post by ivra on 2008-06-14
what is your version of UBUNTU ?

---

### Post by bitterbug on 2008-06-15
I'm running Hardy Heron.

---

### Post by bitterbug on 2008-06-15
Steve,
Have you tried out WICD? I stuck the package for it on a USB drive, installed it and now have working, stable wireless with the Dlink G122 C1.

[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

It's in a .deb, and there's even a repository (though the repo isn't much good if the machine you want it on is only running wireless).

It appears to be much more stable than network-manager. You'll have to remove that first as the two packages conflict.

---

