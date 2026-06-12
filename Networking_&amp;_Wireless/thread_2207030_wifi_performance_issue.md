---
title: "wifi performance issue"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by chpnp on 2014-02-21
I have a lenovo x130 with a bcm4313 wifi configurer with brcmsmac under 12.04 and have performance issues:

Download 1.4 mbps upload 130 mpbs
with windows 7: download 13,5 mbps upload 700 to 900 mbps

Anyone has been able to make it work with decent performances ?

And, 
I am considering a tew-648ubm to improve performance; any feedback from someone ?
Is there another adapter that would be more appropriate ? (i am lookinf for a real tiny one, this is for a laptop).

Thanks

---

### Post by varunendra on 2014-02-21
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It'll give us a detailed info about your wireless setup. We'll then see what all we can do to make it better.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by chpnp on 2014-02-22
Varun 
Thank you for your answer.
I seem to have found a workaround using the wl  driver instead; by doing this:
Remove and blacklist all B43 driver by adding in /etc/modprobe.d/blacklist.conf :

```

blacklist bcma
blacklist brcmsmac
blacklist ssb
blacklist b43

```

Then rebooting and making sure that wifi was not configured at all (later steps failed if there was still some configuration)
Then installing from synaptic the package : bcmwl-kernel-source
(and probably rebooting once more)

It has been a bit hectic of a try and fail attempts until that worked

I had in the past worked with the default driver, then the non-free driver, then had blacklisted some of the drivers to force use of brcmsmac (as was recommended elsewhere), and neither of these had worked. 
I am back since yesterday to similar speed as with win7 - and no loss so far of the wireless. Crossing fingers and hoping it is going to last.
Will come back if it does not.

Thanks

---

