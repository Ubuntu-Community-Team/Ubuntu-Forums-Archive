---
title: "When checking disks, pressing buttons do nothing."
date: 2010-05-16
forum: New to Ubuntu
---

### Post by LinuxFox on 2010-05-16
I started up Ubuntu 10.04 on my laptop and it did the routine disk check.  When I press C to cancel, nothing happens.  Then it said I had a serious error, when I either press I, S, or M, nothing happens.  I had to boot up my laptop while running off battery power.

Is there any reason why buttons won't respond.  I remember if I press ESC in Ubuntu 8.04's check it would skip it.  So why aren't the buttons working here.  Some help please.  If it helps, I'm dual-booting with Wubi.

---

### Post by -humanaut- on 2010-05-16
My guess is it has something to do with Wubi and Plymouth but I'm not sure I'd say just let it finish scanning it can't hurt anything.

---

### Post by sandyd on 2010-05-16
if you installed the propriety ati/nvidia drivers, it screws up plymouth cause those drivers dont have KMS (kernel mode setting). to fix it, either disable the splash, so that you get a text startup splash, or revert back to the open source radeon/nouveau drivers

---

### Post by LinuxFox on 2010-05-16
> **-humanaut- said:**
> My guess is it has something to do with Wubi and Plymouth but I'm not sure I'd say just let it finish scanning it can't hurt anything.I decided to let it finish scanning, and I didn't get that serious error again.  Thanks, although I can't help but wonder why pressing C or other keys didn't work.  Maybe it's a bug or something I guess.

Thanks for the tip Carlee, but I don't use any of the NVidia or ATI drivers, I believe my laptop has an Intel graphic chip.  At least that's what Windows tells me.

---

### Post by -humanaut- on 2010-05-16
> **LinuxFox said:**
> I decided to let it finish scanning, and I didn't get that serious error again.  Thanks, although I can't help but wonder why pressing C or other keys didn't work.  Maybe it's a bug or something I guess.

Thanks for the tip Carlee, but I don't use any of the NVidia or ATI drivers, I believe my laptop has an Intel graphic chip.  At least that's what Windows tells me.

I have Just Ubuntu installed when I get that check "although its very fast" hitting C doesn't respond for me (or atleast it didn't once I haven't tried in awhile I just let it finish the scan now)

---

