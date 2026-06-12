---
title: "Drivers"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by daniell59 on 2009-06-01
Just reflecting. When I first built my computer, and installed Vista, various drivers had to be installed. These included, motherboard, video card etc. Why is it not necessary to install these with Ubuntu? I hope this is not an inane question, I am just looking to learn.

Thanks for listening

---

### Post by halitech on 2009-06-01
In Ubuntu (Linux in general) the drivers are loaded as modules in the kernel so outside a few things like wireless and some video cards, Linux actually autosearches for all hardware on boot and loads the needed modules so you don't have to. Even with the video card it will usually load a driver that will work but you may want to get the non-free drivers (depending on your card) for 3d acceleration.

---

### Post by Celauran on 2009-06-01
Linux isn't Windows. Drivers are built into the kernel rather than added separately.

---

### Post by Hospadar on 2009-06-01
In linux, hardware drivers are included in the kernel since they are (almost) all open source, there is no reason or need to distribute them separately (since there are no real restrictions on their free distribution.

That's not to say there arn't proprietary drivers, the hardware-accelerated nvidia driver for example is closed source and must be obtained from nvidia (although there's a package that will do all the work for you in that case)

There's no fundamental reason you *can't* download drivers, and occasionaly you may if it's a very new driver not yet included in the kernel (though typically they get integrated as soon as thay at least sort of work.

---

