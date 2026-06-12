---
title: "Burning ISO image, OS in Ubuntu"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by 2blue on 2009-10-20
How do you burn ISO images in Ubuntu? I usually burn bootable CD's in Windows using Easyiso, and now I have only Ubuntu on my portable, no windows. I need to burn Puppy Linux on a bootable CD. Is that possible?

---

### Post by oboedad55 on 2009-10-20
> **2blue said:**
> How do you burn ISO images in Ubuntu? I usually burn bootable CD's in Windows using Easyiso, and now I have only Ubuntu on my portable, no windows. I need to burn Puppy Linux on a bootable CD. Is that possible?

You should be able to right-click on the .iso file and select "open with" and select brasero, which is the cd burning app and just follow the prompts.

---

### Post by swoody on 2009-10-20
As mentioned above, you should be able to simply right-click on the .iso icon. You can also find Brasero in Applications>Sound&Video>Brasero Disc Burner. Be sure to select 'Burn Image', and then you can select your blank CD as well as the .iso file, and you're good to go :)

---

### Post by MelDJ on 2009-10-20
or you can get gnomebaker from synaptic. after installing it, run it and under tools, press burn cd image

---

### Post by 2blue on 2009-10-20
Thanks both of you, It worked fine and Puppy is booting :)

---

### Post by swoody on 2009-10-20
Great to hear :D

Just to let you know, it may be useful to other users if you could mark your threads as [SOLVED] after your issues have been answered. Simply go to 'Thread Tools' in the top-right of this page, and then select 'Mark thread as solved'. Thanks :)

---

### Post by vinutux on 2009-10-20
Yeh..plz mark thread SOLVED....

---

### Post by 2blue on 2009-10-20
Thanks for help. I appreciate it.

---

### Post by Al Ricco on 2009-10-20
If you are not afraid of typing few chars within a console, the following should make the job :
# cdrecord yourcdimage.iso

---

