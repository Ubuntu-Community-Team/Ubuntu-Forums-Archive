---
title: "Better graphics with NVidia GeForce 6150 LE and Ubuntu 10.10??"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2011-01-27
So I want to be able to customize my Ubuntu setup but unfortunetly I ran into the Nvidia Driver issue... I did the whole LiveCD "quiet shell nomodeset" thing and got it loaded up fine but now I want to use some graphic's and animations but I can't set my Visual Effects to extra because I believe the driver isn't what it should be... Is there anyway to get Meerkat (10.10) to run like Karmic (9.10) ran with all the animations and Compiz setups..?? Thanks...

---

### Post by JDM_SOHC on 2011-01-27
I found this link but thought i'd ask first before I just start downloading stuff..

[http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04](http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04)

---

### Post by mikewhatever on 2011-01-27
The driver for 6150 LE should be available through the Additional Drivers utility. I suggest you try that instead of following random howtos.

---

### Post by JDM_SOHC on 2011-01-27
I tried that already, but there are three versions listed and I'm not sure which one to use..?? Version (173) Version (96) or Version (current) - recommended..??

Currently I'm not allowed to have Enhanced settings in the Animations tab from the desktop...

---

### Post by mikewhatever on 2011-01-27
Well, obviously the current, that's why it's labeled as recommended.

---

### Post by JDM_SOHC on 2011-01-27
> **mikewhatever said:**
> Well, obviously the current, that's why it's labeled as recommended.

So in 9.10 I'm aloud to have Extra Visual effects but in 10.10 I'm not aloud and it's on the same PC..???

---

### Post by mikewhatever on 2011-01-27
In 9.10, you install the driver, and that allows the desktop effects. In 10.10 - exactly the same.

---

### Post by JDM_SOHC on 2011-01-27
> **mikewhatever said:**
> In 9.10, you install the driver, and that allows the desktop effects. In 10.10 - exactly the same.

I been reading and something about X not being supported in 10.10 through NVidia drivers..?? I did exactly same setup as 9.10 on 10.10 and I'm not able to enable any extra visualizations..

---

### Post by mikewhatever on 2011-01-27
At the time Maverick was released, Nvidia didn't have the legacy drivers (nvidia-96,nvidia-173) ready for xserver1.9. Those drivers are used for Geforce4/5 and some other older GPUs, and are now available in the Maverick repositories. Your card should work with any of the more recent drivers (nvidia-current==260.19.06, nvidia-185 and nvidia-180), all of which are in the repositories.

Did you install the nvidia-current driver?

---

### Post by JDM_SOHC on 2011-01-27
> **mikewhatever said:**
> At the time Maverick was released, Nvidia didn't have the legacy drivers (nvidia-96,nvidia-173) ready for xserver1.9. Those drivers are used for Geforce4/5 and some other older GPUs, and are now available in the Maverick repositories. Your card should work with any of the more recent drivers (nvidia-current==260.19.06, nvidia-185 and nvidia-180), all of which are in the repositories.

Did you install the nvidia-current driver?

Yes, the current driver was already installed...

---

