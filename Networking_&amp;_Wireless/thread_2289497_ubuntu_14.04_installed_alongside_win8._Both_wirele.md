---
title: "ubuntu 14.04 installed alongside win8. Both wireless are unstable"
date: 2015-08-04
forum: Networking &amp; Wireless
---

### Post by nur4 on 2015-08-04
I recently installed ubuntu 14.04 LTS along side Win8.1 on my new laptop. Wireless connection had problems for a while (it started disconnecting whenever I downloaded something or  rebooted the pc. T**he connection can only be brought back  again if I switched the router on and off.**) and then in this thread:

[http://ubuntuforums.org/showthread.php?t=2288778](http://ubuntuforums.org/showthread.php?t=2288778)

I turned off power management permanently and it seemed to work fine for 5 days or so. and then the same problem occurred all over again.
I've tried almost everything here and now I think the problem might be with windows where wireless connects but unstable.

Any suggestions please? I'm helpless here..

---

### Post by weatherman2 on 2015-08-04
If you're also having issues in Windows, maybe it's not an Ubuntu problem at all?

If you use both Windows and Ubuntu regularly, I'd start with Windows and get wireless to be stable there.  Check the laptop manufacturer's website for a newer wireless card driver.

What kind of wireless router/access point is it?  Have you looked at the router manufacturer's website for an updated firmware?  Even if older devices connect fine to the router now, newer devices may not.  Sometimes an update to the router's firmware, if available, can help.  Sometimes routers are old and no longer supported by the manufacturer and it's time to get a new one.  (Or if the router supports Tomato or DD-WRT firmware, you could try that.)

How is the router configured?  I prefer using WPA2 + AES security (certainly not WEP which is long obsolete).  I also avoid "WPA2 + WPA mixed" mode which really isn't needed anymore - all modern devices and most older ones support WPA2 now, and sometimes the mixed mode causes connection issues.

---

### Post by weatherman2 on 2015-08-04
I also wouldn't slow your wireless card down with the 11n_disable=1 setting.  Try 11n_disable=8 instead. My Intel wireless cards work great at full 802.11n speeds in Ubuntu - slowing down to G speeds would be unacceptable to me.  But I am not using your particular wireless card and not using Ubuntu 14.04 daily on my laptops.  The one device I have using an older Intel wireless card with Ubuntu 14.04 seems to work perfectly with the iwlwifi driver, though, at full 802.11n speeds without any tweaks to settings.

---

### Post by nur4 on 2015-08-06
> **weatherman2 said:**
> If you're also having issues in Windows, maybe it's not an Ubuntu problem at all?

If you use both Windows and Ubuntu regularly, I'd start with Windows and get wireless to be stable there.  Check the laptop manufacturer's website for a newer wireless card driver.

What kind of wireless router/access point is it?  Have you looked at the router manufacturer's website for an updated firmware?  Even if older devices connect fine to the router now, newer devices may not.  Sometimes an update to the router's firmware, if available, can help.  Sometimes routers are old and no longer supported by the manufacturer and it's time to get a new one.  (Or if the router supports Tomato or DD-WRT firmware, you could try that.)

How is the router configured?  I prefer using WPA2 + AES security (certainly not WEP which is long obsolete).  I also avoid "WPA2 + WPA mixed" mode which really isn't needed anymore - all modern devices and most older ones support WPA2 now, and sometimes the mixed mode causes connection issues.

I checked windows wireless card and upgraded as you suggested and it worked fine for days now (I have had recovered to an early version of win8 before i installed ubuntu alongside and it turns out that that version didnt have drivers installed.) Now the problem doesnt happen anymore when I turn the laptop on and off but it does happen if I rebooted. Any idea why?

---

