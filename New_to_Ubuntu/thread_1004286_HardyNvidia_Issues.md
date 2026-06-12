---
title: "Hardy/Nvidia Issues"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Tumpster on 2008-12-07
So I wanted a fresh install of Hardy as I'm happy with it and wanted to give it some more time before I would move on to another edition. Well everything is loaded EXCEPT Nvidia drivers. I have tried loading them through the Hardware Drivers portion of System->Administration and when I reboot, it flashes the main screen (text screen) three times and tells me that Ubuntu is running in low graphics mode. I then installed and tried loading drivers through Envy and I get the same thing. This is so frustrating and I could use any help someone would have! Thank you! :)


I almost forgot, I run an Nvidia 9600 GT.

---

### Post by chuckyp on 2008-12-07
I believe with the 9600gt you need version 177 and up of the nvidia drivers. Or the nvidia-glx-new package.

---

### Post by linux_tech on 2008-12-07
Try removing and manually re-installing nvidia
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by linux_tech on 2008-12-07
Here is another link for a how to for nvidia driver-

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Tumpster on 2008-12-08
> **linux_tech said:**
> Here is another link for a how to for nvidia driver-

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Thanks all, got it up and running by completely removing everything and downloading the beta drivers, killing x, and following the prompts!!!

---

