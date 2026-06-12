---
title: "Hardy or Intrepid for a NAS?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by BassKozz on 2008-12-04
I am building a NAS box using Ubuntu (desktop variant, because I like to have a gUI).  Should I install Hardy (8.04) because of it's LTS (Long Term Support) since this box will remain on 24/7 and will be headless (after the install)?  Or should I go with the latest and greatest, Intrepid (8.10)?

I will mostly just be running a few Samba Shares, FTP, Automated Backups (using JungleDisk to backup to S3), and possibly LAMP for internal web-serving.

**_EDIT_**: I forgot to mention I also intend on building a software RAID5 array using **mdadm** on this box.

---

### Post by hyper_ch on 2008-12-04
I would go for debian lenny...

---

### Post by BassKozz on 2008-12-04
> **hyper_ch said:**
> I would go for debian lenny...

I am not familiar with debian, althou I am sure it would not be hard to learn since Ubuntu is a fork of the debian codebase (thank you wikipedia :p), but I am curious as to why you suggested **lenny** and not **etch**, since lenny is still in "testing" phase and etch is "stable"?

---

### Post by hyper_ch on 2008-12-04
debian is just rock-stable and lenny is RC meanwhile... so it will be "stable" soon but in reality it's already more stable than a lot of other distros out there...

---

### Post by BassKozz on 2008-12-04
Thanks for the clarification hyper_ch, I didn't realize it was in RC.
But I think I am going to stick with my comfort-zone (Ubuntu), so if you were to pick between Hardy & Intrepid?

---

### Post by Paqman on 2008-12-04
I don't know about using it *as* a NAS, but I know Intrepid plays much more nicely *with* my COTS NAS. I used to have trouble with permissions between the two, but presumably the new version of smbfs in Intrepid is doing things better than the version in Hardy.

---

### Post by hyper_ch on 2008-12-04
> **BassKozz said:**
> But I think I am going to stick with my comfort-zone (Ubuntu), so if you were to pick between Hardy & Intrepid?

why did you then give "others" as option?

---

### Post by BassKozz on 2008-12-04
> **hyper_ch said:**
> why did you then give "others" as option?

Other Ubuntu release

---

### Post by AlanR8 on 2008-12-04
I've done the same thing in both 8.04 and 8.10. Both work well but I do have a problem. I use KUBUNTU 8.10 on server and clients and when I connect remotely to the server I suffer huge tearing of the images. It also happen when I access the server via an XP box.

I have another thread on this issue:

[http://ubuntuforums.org/showthread.php?t=973996](http://ubuntuforums.org/showthread.php?t=973996)

that explains the problem.

---

