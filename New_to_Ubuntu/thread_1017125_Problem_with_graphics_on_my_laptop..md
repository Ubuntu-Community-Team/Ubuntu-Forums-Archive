---
title: "Problem with graphics on my laptop."
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Zerocool947 on 2008-12-20
Hello. I've been having lagging problems with my laptop since I installed Ubuntu 8.10. Graphics are on lowest settings and still firefox typing lags, switching tabs lags, and so does moving windows across the screen.

Now, my laptop is pretty beefy, so I don't know why this would be happening.

I have a Dell Latitude D830 with an NVIDIA Quadro NVS 140M.

---

### Post by nhasian on 2008-12-20
did you install the proprietary nVidia Quadro NVS 140 drivers?

---

### Post by Zerocool947 on 2008-12-20
Yes. Currently, it's at version 173.14.12.

---

### Post by nhasian on 2008-12-21
okay so far so good, take a look at this [launchpad bug talking about lost resolutions when using the NVIDIA binary driver]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292") along with [FixVideoResolutionHowto]("https://wiki.ubuntu.com/X/Config/Resolution") for further details and potential workarounds.

---

