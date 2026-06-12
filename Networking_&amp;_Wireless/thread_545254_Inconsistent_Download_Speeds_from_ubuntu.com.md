---
title: "Inconsistent Download Speeds from ubuntu.com"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by thepianobar on 2007-09-07
Since dual-booting Ubuntu on my laptop I've noticed that anything I download from ubuntu.com (whether it's the latest .iso or updates) has very inconsistent download speeds. My speed will shoot up anywhere from 40-200KB/s for a second or two and then drop back down to about 5KB/s or less. This makes even a simple update take forever.

Two weird things in conjunction with this:
1) it only happens while I'm at work. I contacted our IT dept and they assured me we have no traffic shaping or limiting policies in place at the moment and I believe them (they're working on implementing a policy soon). I just downloaded a ~180MB file from VMware in Ubuntu in under a minute, it was going around ~4-5MB/s (yes, we have a huge pipe here, we do offsite datacenter hosting).
2) Downloading an Ubuntu .iso in Windows yields the same weird low speeds with medium spikes, so it's not related to the OS.

During my last update I ran a packet capture using Wireshark and I'm about to go through that. Anyone have ideas on what might be causing this? Stuff from Ubuntu.com seems to be the only thing affected since I can download from sites like VMware at incredible speeds.

Thanks in advance...

---

### Post by lisati on 2007-09-08
It sometimes depends on where the download is coming from - and the geographically closest server doesn't always produce the fastest download.

---

