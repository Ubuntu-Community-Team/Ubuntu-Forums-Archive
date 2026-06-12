---
title: "Failed to eject cd"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Harlequin. on 2009-08-31
Given device "/org/freedesktop/Hal/devices/storage_model_DVD_RAM_GSA_H55N" is not a volume or drive

It´s happened a few times so far, but of course it has to happen during my installation of Diablo 2 lol :P

Anyone know how to fix this?

---

### Post by 4Orbs on 2009-08-31
It's my understanding that xfce considers it a safety feature that, in order to eject a cd, you right click on the cd Desktop icon and select eject. But the icon is inaccessible if you happen to be installing something with wine and the install page defaults to full-screen. So, before I installed Diablo 2 on my system, I made .iso copies of all 4 installation discs then mount and unmount the discs as needed using gmountiso. To do this requires configuring wine to work with a virtual cd drive. The good part is that you never have to use the actual playdisc again, just mount the .iso and play. Another point: Diablo 2 probably won't work unless you install the correct patch (112a) available from the Blizzard website.

---

### Post by Rytron on 2009-08-31
Hi. Try this:-

Note: disk name can be found by looking at /etc/fstab

```
sudo eject /dev/scd0
```

alternatively try:

```
sudo umount -l /dev/scd0
sudo eject /dev/scd0
```

---

### Post by Krovas on 2009-09-05
This particular *feature* appears to interfere with Brasero...is there any way to turn it off?

---

### Post by Harlequin. on 2009-09-14
> **4Orbs said:**
> It's my understanding that xfce considers it a safety feature that, in order to eject a cd, you right click on the cd Desktop icon and select eject. But the icon is inaccessible if you happen to be installing something with wine and the install page defaults to full-screen. So, before I installed Diablo 2 on my system, I made .iso copies of all 4 installation discs then mount and unmount the discs as needed using gmountiso. To do this requires configuring wine to work with a virtual cd drive. The good part is that you never have to use the actual playdisc again, just mount the .iso and play. Another point: Diablo 2 probably won't work unless you install the correct patch (112a) available from the Blizzard website.

Thanks for the info :D but the D2 installer doesn't default to full screen, so once I knew how to actually EJECT the cd from the drive I was good to go haha.

Bit off topic, but if you ever see this thread again lmk what realm you play on :p

---

