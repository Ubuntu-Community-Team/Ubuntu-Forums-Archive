---
title: "Too many torrent connections -&gt; internet disconnects"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by Tampio on 2007-10-08
Torrents work otherwise just fine, but if there are a couple of those running at full speed, then the internet connection disconnects after a while. It stays on if I set the global connection limit in KTorrent to 30, any more and it will eventually disconnect. Needless to say that makes downloading really slow. Rebooting my ADSL modem gets the connection back up. Same thing happens in Deluge and uTorrent under wine. I don't have any connection problems with BitComet on Windows XP, even if I'm running it on VirtualBox. Any idea what's causing this?

---

### Post by mhenry35 on 2007-10-19
I think I know what's going on - Do a google search on the phrase "Traffic Shaping".  That would describe what's been happening to me.

Certain ISP's are sending fake TCP/IP Packets with an RST (reset) instruction when the upload speed goes up too high.

Doesn't look like a Linux problem at all.  Although in my case, it does completely knock me off the internet and I have to reboot.

---

