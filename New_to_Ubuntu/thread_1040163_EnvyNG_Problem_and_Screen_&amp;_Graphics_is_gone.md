---
title: "EnvyNG Problem and Screen &amp; Graphics is gone"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by yizuman on 2009-01-15
EnvyNG will no longer work for Ubuntu 8.10

I tried installing it under terminal using NVIDIA 71.89.04 as the driver since it did work for Ubuntu 8.04, but does not anymore for 8.10. The system locks up and the driver fails to load.

Also the "Screens & Graphics" has been completely removed since I have no way of changing the default 800x600 resolution to 1024x724.

Why was the "Screens & Graphics" completely removed? It was a very useful tool to use.

It should be put back.

---

### Post by mc4100 on 2009-01-15
Can't help you with Envy, but I know that Screens and Graphic was removed because it was becoming obsolete, due to it being unable to work with xrandr. In general, the expectation was the you shouldn't **need** to configure the device -- it should just work.

---

### Post by yizuman on 2009-01-15
> **mc4100 said:**
> Can't help you with Envy, but I know that Screens and Graphic was removed because it was becoming obsolete, due to it being unable to work with xrandr. In general, the expectation was the you shouldn't **need** to configure the device -- it should just work.

Well it doesn't, so now the question remains, how do I go beyond 800x600?

---

### Post by avtolle on 2009-01-15
Please read [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)

---

### Post by gjoellee on 2009-01-15
1. Run an xfix, to reset xorg (which is more like the GUI (Grapihcal User Interface) program). You can read how here: [http://www.kshoster.net/content/howto-run-xfix](http://www.kshoster.net/content/howto-run-xfix)

2. Keep away form Envy, you already have a graphical driver installer that comes wiht Ubuntu be default. It is found in the menu System->Administration->Hardware Drivers (be believe).

3. In the hardware drivers program install the driver seen as "Recommended"

4. Reboot, and your graphic driver should work properly

---

### Post by yizuman on 2009-01-15
> **gjoellee said:**
> 1. Run an xfix, to reset xorg (which is more like the GUI (Grapihcal User Interface) program). You can read how here: [http://www.kshoster.net/content/howto-run-xfix](http://www.kshoster.net/content/howto-run-xfix)

2. Keep away form Envy, you already have a graphical driver installer that comes wiht Ubuntu be default. It is found in the menu System->Administration->Hardware Drivers (be believe).

3. In the hardware drivers program install the driver seen as "Recommended"

4. Reboot, and your graphic driver should work properly

I already did that, the result was that my entire screen became scrambled. Couldn't get it off cuz I couldn't see anything, so I had to reinstall clean to start over.

---

### Post by yizuman on 2009-01-15
> **avtolle said:**
> Please read [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)

So reading this....

> The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

That's what I use. So does this mean I'm screwed now?

---

### Post by yizuman on 2009-01-15
Bump!

---

### Post by yizuman on 2009-01-15
Hello? Anybody has the answer to my last question?

---

