---
title: "please help with wireless issue"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by tongueman on 2009-08-25
OK folks...

My wireless adapter has been working fine for months and even this morning, return from work and my wireless adapter is not showing as working or at least not showing any networks. i've disabled driver and re enabled it but cant find any networks. its as if ubuntu does not recognise that my wireless adapter is present at all. 

Please help i'm at a loss.

---

### Post by coldReactive on 2009-08-25
What's your wireless adapter? (Brand/Manufacturer and model)

Did you update your kernel (linux-image/headers) recently?

---

### Post by tongueman on 2009-08-25
thanks for your quick reply cold...

please excuse my ignorance, the manual states..

wlan:IEEE 802.11b/g in emachine laptop g720

kernel question? I accept all updates available. should i be manual finding updates?

Apologies for ignorance again. thanks

---

### Post by mapes12 on 2009-08-26
This happened to me yesterday. I rebooted my wireless router. Once it had reconfigured itself I rebooted my Desktop and the wifi connected.

---

### Post by Luca_turicci on 2009-08-26
> **tongueman said:**
> thanks for your quick reply cold...

please excuse my ignorance, the manual states..

wlan:IEEE 802.11b/g in emachine laptop g720

kernel question? I accept all updates available. should i be manual finding updates?

Apologies for ignorance again. thanks

I've had many issues with new kernel versions and wireless/audio.

I suggest, by now, at startup, when grub's loading hit ESC and choose to boot from a previous kernel (3rd on the list) and then wait a day or two, then look for updates again and retry with your normal kernel. (first in the list, or don't press ESC at startup)

---

