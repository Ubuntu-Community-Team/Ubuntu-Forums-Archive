---
title: "Screen Resolution"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by System Monitor on 2009-04-23
I just installed Jaunty Jackalope and oddly ubuntu did not suggest to install any drivers. THe last few times I have a done a clean install ubuntu suggested for me to install drivers. The screen resolution options are only 1280x1024 and their is no option for the optimal screen resolution 1440x900. How do I install the driver and change my resolution?

---

### Post by System Monitor on 2009-04-23
Also there is no option to install proprietary drivers under System>Administration>Hardware Drivers

---

### Post by Hospadar on 2009-04-23
If you go to System->Administration->Hardware Drivers, you can manage your restricted drivers.  Hopefully that will take care of the problem.

Edit:
Just saw your post.

Well, what sort of video hardware are you using?  If you're not sure, open up a terminal (Applications->Accessories->Terminal) and post the output of "lspci | grep VGA" (if there is no output, just post the output of "lspci"

Also this just occurred to me, Is your internet connection working fine on the machine?  Try updating your repos and then checking Hardware Drivers, from a terminal, "sudo apt-get update" (you can also do this in System->Administration->Software Sources)

---

### Post by System Monitor on 2009-04-23
> **System Monitor said:**
> Also there is no option to install proprietary drivers under System>Administration>Hardware Drivers

There are no drivers restricted drivers available.

---

### Post by Melk79 on 2009-04-23
This happened to me too.  I tried enabling Extra Visual Effects under System>Preferences>Appearance>Visual Effects and it searched and installed proprietary drivers (although it stalled and I cancelled it eventually). Upon going back into hardware drivers in Administration, my Nvidia drivers were shown and I activated 180 successfully upon the click and restart.

---

