---
title: "Wireless connection not working after re-boot"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by heyadc123 on 2008-08-30
Greetings all,

I'm having issues with my Network settings, My wireless card and internet access is working after it's configured manually,  But it's not connecting automatically after I reboot the system and I need to re-enter my share-secret key each time to access the internet.

It's the first time I'm using ubuntu, anything I'm doing wrong here?

Cheers

DC

---

### Post by GepettoBR on 2008-08-30
Doesn't it work in roaming mode? If you use Network Manager to store the connection data, it should connect automaitically.

---

### Post by heyadc123 on 2008-08-31
I did try the roaming mode no success.  I also stored my Wireless settings in the Network settings. One thing I noticed is the wireless is on eth1 and not on wlan0. but this shouldn't make any difference.

DC

---

### Post by GepettoBR on 2008-08-31
> **heyadc123 said:**
> I did try the roaming mode no success.  I also stored my Wireless settings in the Network settings. One thing I noticed is the wireless is on eth1 and not on wlan0. but this shouldn't make any difference.

DC

Indeed it shouldn't. I had an eth1 wireless connection once when I had to compile the drivers for a usb antenna. Currently, my wireless interfaces are wlan0 and ra0. The name makes no difference.

If you're manually storing the data, it's odd that you're prompted for your password on every boot. Is your keyring properly configured? If we get rid of the password prompt, then your auto-connect problem will probably be solved as well.

---

