---
title: "Huh.  Wi-fi adapter driver changed..."
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Cilionelle on 2008-09-15
I've got a laptop that was running an AR5007 wi-fi adapter, and it has somehow changed to give me an AR242x 802.11abg adapter.  Having done the setup of the wifi card numerous times (hence the sig!) I am at a loss now as to how to get it to work again.

Could someone please help me?  I can even get the main wired connection working.  It's a pain in the butt.

(I know you guys will want me to post lshw -C network and lspci, but is there specific info from those commands that I can post instead, to cut down on typing time?)

Never mind, this helped!  [http://ubuntuforums.org/showpost.php?p=4791500&postcount=7](http://ubuntuforums.org/showpost.php?p=4791500&postcount=7)

Nope, didn't work.  I still get a "no scan results" message on ath0 when I look for "wireless" (using **iwlist scan**, the network I want to connect to.  Doing **lshw -C network** gets me the Ethernet interface (eth0) and the wireless interface (logical name wifi0).  wifi0 doesn't support scanning tho.

---

### Post by Cilionelle on 2008-09-16
Bump.

---

