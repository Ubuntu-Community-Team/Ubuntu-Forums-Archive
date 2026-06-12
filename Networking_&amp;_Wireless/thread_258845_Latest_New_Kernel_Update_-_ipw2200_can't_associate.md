---
title: "Latest New Kernel Update - ipw2200 can't associate"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Velox Letum on 2006-09-16
Okay, so last night I upgraded my laptop to the .47 from .46 kernel. This morning I turned it on (first boot with new kernel) and my ipw2200 wasn't being recognized at all. Looking at dmesg, I found symbol conflicts with ieee80211. So I reinstalled the ipw2200 firmware (3.0), ieee80211 (1.1.14), and ipw2200 (1.1.3), rebooted, and the interface showed up again.

Now when I try to associate to my WEP router, it doesn't work even though it has the past few months. I use the iwconfig commands manually and set the mode/essid/wep key and so on right on the fly, then the ap, then I use dhclient to get an IP. However it doesn't even try to associate, just says that it's unassociated, and using the status script included with the ipw2200 software shows the bit for "associating" and "associated" aren't on.

---

### Post by Velox Letum on 2006-09-16
Fixed. Apparently the newest kernel doesn't like ipw2200-1.1.3, but ipw2200-1.2.0 works great.

---

### Post by hasbean on 2006-09-19
I have the same issue as yours, but unfortunately the driver update didn't do it for me.

I'm wondering if there's anything I'm missing.  I don't even know why my wireless broke in the first place.  I just did today's kernel update, and it's still not working.

---

### Post by hasbean on 2006-09-19
I take that back.  The problem was from the stupid router as well! ](*,) 

It's working now

---

### Post by ilbozo on 2006-10-11
Sorry, could you explain how did u install the new drivers? I found a guide but it's Hoary related and seems to be quite different.
for example: where did u install the firmware? /usr/lib/hotplug/firmware?

---

