---
title: "Can't get DVD to play correctly"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by deason7 on 2009-06-20
So I have just base installed Ubuntu 9.04 and I put in a DVD and it starts to play it but the picture doesn't come through. The picture is all scrambled and different colors are all over the screen.

At first it would not even play, then I installed "ubuntu-restricted-extras" package but it now presents this problem. I have both MPlayer and Movie Player installed. But neither works.

Is this a codec problem or application problem or what?? Any help is greatly appreciated.

THANKS!

---

### Post by SuperSonic4 on 2009-06-20
If other videos work it is likely to be because you're missing libdvdcss2. Either open synaptic and search for it or open a terminal (system -> Administration -> Terminal) and paste in ```
sudo apt-get install libdvdcss2
```

If you've got the restricted extras I doubt it's a codec thing but rather a scrambling issue, especially if local videos work

---

### Post by NightwishFan on 2009-06-20
I think you may need Medibuntu to get libdvdcss2. A how to is here, please make sure you run the correct command for your version of Ubuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Please note it might be arguably illegal in some places.

---

### Post by Prince Valiant on 2009-06-20
Try VLC player.  I'm not sure, but it may solve your problem.

Cheers!
-Val

---

### Post by NightwishFan on 2009-06-20
Still needs libdvdcss2, which is essentially the most annoying thing alive. Pirates will STILL pirate media despite their efforts to make it hard for anyone other than Windows to watch their media. Money in money out..

---

### Post by SuperSonic4 on 2009-06-20
> **NightwishFan said:**
> I think you may need Medibuntu to get libdvdcss2. A how to is here, please make sure you run the correct command for your version of Ubuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Please note it might be arguably illegal in some places.

Wouldn't the OP need medibuntu to get ubuntu-restricted-extras?

---

### Post by philinux on 2009-06-20
No.

Click the restricted formats link below for info.

---

### Post by hyperdude111 on 2009-06-20
> **SuperSonic4 said:**
> Wouldn't the OP need medibuntu to get ubuntu-restricted-extras?

No

---

