---
title: "Computer slow after installing qcad"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by John Hale on 2009-02-04
Hi Guys, my computer running really slow after installing qcad, I'm not sure if it's some graphic clash, also when I go to load a cad file it says "cannot open file **** pleask check permissions"

Thanks

John

---

### Post by RomeReactor on 2009-02-04
Hi. Open the System Minotor (System->Administration->System Monitor) and see if there's any process (besides qcad) that's hogging the CPU. What video card do you have? If it's ATI or nVidia, have you installed the restricted drivers?

---

### Post by John Hale on 2009-02-04
It's an ati and I installed some driver and alls working know, why would it suddenly change after an installation when it's been ok for a month?

---

### Post by avtolle on 2009-02-04
Sounds, at first blush, there's a problem with qcad configuration. I'm not familiar with the package at all; thus, was there or is there any preferences or configuration routines that need to be looked into?

---

### Post by RomeReactor on 2009-02-04
If qcad required hardware acceleration from the video card, it's possible the open source drivers didn't provide it for your particular card; or perhaps the proprietary driver provided something required by qcad that the open source radeon or ati drivers didn't have. Is it working correctly now?

---

