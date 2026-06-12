---
title: "workaround for dwl-520+ after upgrade"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by f-bomb on 2005-10-18
I upgraded from hoary to breezy last week with little trouble, except for my AirPlus DWL-520+ wifi card didn't work anymore.  I saw no errors i any of the logs, dmesg, etc, but iwconfig said the card wasn't registering a signal from my AP.  The AP was working, as i could connect with my laptop.  I posted in another thread about it, but got no help.  I've discovered a workaround that allows me to connet to my AP again, but does not solve my problem.  I'm going to share what I did, but it may be unique to my setup, so i'm not going to promise thos will work for others having problems with their acx100 based cards.

I had added in my wifi card after I installed hoary, so I had to jump few a couple hoops to get it working, namely creating symlinks pointing to the correct fimware with the names that the acx_pci module was looking for

```

sudo ln -s /lib/hotplug/firmware/RADIO11.BIN-2.6.10-5-386 /lib/hotplug/firmware/RADIO11.BIN
sudo ln -s /lib/hotplug/firmware/WLANGEN.BIN-2.6.10-5-386 /lib/hotplug/firmware/WLANGEN.BIN

```

This got my card working under hoary.  After my upgrade, as i described above, card no worky.  After a little research, I saw that there were new firmware versions for the new kernel, but the file sizes, diffs, and md5s were the same.  My guess, which was confirmed later, is that the acx drivers hadn't been updated for breezy.  Rather than (possibly) completely hosing my wifi setup by compiling the latest driver code, on a whim I decided to boot back to the old 2.6.10 kernel rather than the new 2.6.12 one.  Wouldn't you know it, my card works again!  There's something broken between the 2.6.12 kernel shipped with breezy and the acx drivers.

I may attempt a recompile of the driver at some point, but i'm too lazy at the moment.  I'll try to post my findings if i ever get around to it. :)

---

### Post by Antal on 2005-10-27
Do let me know if you found away to work with the new kernel.

I didn't upgrade (new install)and I dont know how to get back to the old one...

---

