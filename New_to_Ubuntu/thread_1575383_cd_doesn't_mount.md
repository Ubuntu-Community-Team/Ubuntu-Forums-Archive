---
title: "cd doesn't mount"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by m3t3ors on 2010-09-15
im trying to install sims 3 but my dvd doesn't auto mount ?
theres no icon to select mount or unmount?

and play on linux cant find my cd/dvd drive

---

### Post by garvinrick4 on 2010-09-15
> **m3t3ors said:**
> im trying to install sims 3 but my dvd doesn't auto mount ?
theres no icon to select mount or unmount?

and play on linux cant find my cd/dvd driveWill it eject on command.
```
sudo eject /dev/sr0
```

---

### Post by m3t3ors on 2010-09-15
Will it eject on command.
Code:

sudo eject /dev/sr0





yes it will eject via command

---

### Post by garvinrick4 on 2010-09-15
Then it will mount when you put a disk in and close?

---

### Post by m3t3ors on 2010-09-16
on other linux distros ive tried theres been an icon on desktop telling me the cd/dvd has mounted, i dont get the icon?
also in other distros theres been a my computer icon in "places"

---

### Post by garvinrick4 on 2010-09-16
> **m3t3ors said:**
> on other linux distros ive tried theres been an icon on desktop telling me the cd/dvd has mounted, i dont get the icon?
also in other distros theres been a my computer icon in "places" Yes when there is a disk in the drive it should mount on desktop and in Places telling you what is in drive and if it is a blank it will say Blank DVD or CD. Never had problem but am wondering if it is not a setting in Configuration Editor like most other media preferences in Nautilus? Worth a google or two.

---

### Post by m3t3ors on 2010-09-17
ok thanks ,will look into this

---

