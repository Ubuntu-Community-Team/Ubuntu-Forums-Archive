---
title: "Where does update-manager store the debs!?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by troyzero on 2009-10-30
Hi Guys,
Perhaps a silly question, but I am relatively new to Ubuntu.
We have 2 workstations here that are 9.04 and will be updated to 9.10.

To save on bandwidth and server impact, I am looking for the cache where update-manager stores the deb's, so I can copy them over to the second one manually once this one is updated.

I found /var/cache/apt/archives but nothing there is time stamped today and it looks suspiciously like those are deb's it downloaded when I requested it from Synaptic or apt-get

Thanks in advance, please excuse my newbie question.
Regards
Troybuntu

---

### Post by troyzero on 2009-10-30
..and I did a "du -sh" in the directory I mentioned before.. It is growing in size.
Looks like I found my cache, self help at its best :)
cheers anyway
troy.

---

### Post by dj-toonz on 2009-10-30
You'll probably have dependency problems by using Jaunty packages in Karmic as for example a = z = y, u can always try it and see

---

### Post by troyzero on 2009-10-30
> **dj-toonz said:**
> You'll probably have dependency problems by using Jaunty packages in Karmic as for example a = z = y, u can always try it and see

I might not of explained myself correctly sorry, I have 2x 9.04 workstations, I am updating workstation A to 9.10 atm, Workstation B I will dump the debs into the cache folder from Workstation A then run update-manager and select upgrade.
I guessed since it will find most of the debs it wants in the cache, it will have to download only 10% or so (some packages are different obviously I assume most will be the same, both amd64 similar hardware)

Do I have this wrong?
Cheers
Troy

---

