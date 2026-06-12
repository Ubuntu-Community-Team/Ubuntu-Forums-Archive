---
title: "Ubuntu 11 Installation Froze on my first attempt"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by disposablechild on 2011-06-22
I planned to install ubuntu 11.4.0 on my external hard drive so that it would not affect windows on my computer. I partitioned my external hard drive. The installation files were on the partition that I used for the installation. After booting from the hard drive and starting the installer in the allocate drive(r?) space window I chose the partition, formatted to ext4 successfully, and chose mountpoint "/" I clicked the next button (I think it said install now.) After that the loading cursor spun for about 27 hours before I unplugged the hard drive and shut down the computer. The installer did not respond to the hard drive being unplugged. Could it have gone wrong because the installation files were on the same partition being used for the installation, or that I chose the wrong format? I cannot find the other partition in windows... I assume thats because I formatted it? What should I do now?

---

### Post by wildmanne39 on 2011-06-22
> **disposablechild said:**
> I planned to install ubuntu 11.4.0 on my external hard drive so that it would not affect windows on my computer. I partitioned my external hard drive. The installation files were on the partition that I used for the installation. After booting from the hard drive and starting the installer in the allocate drive(r?) space window I chose the partition, formatted to ext4 successfully, and chose mountpoint "/" I clicked the next button (I think it said install now.) After that the loading cursor spun for about 27 hours before I unplugged the hard drive and shut down the computer. The installer did not respond to the hard drive being unplugged. Could it have gone wrong because the installation files were on the same partition being used for the installation, or that I chose the wrong format? I cannot find the other partition in windows... I assume thats because I formatted it? What should I do now?Hi, I would say that was the exact problem, you need to create a live cd or usb stick.

---

### Post by Rubi1200 on 2011-06-22
Before you continue, boot the computer with a LiveCD/USB and post the output of this command from the terminal:

```
sudo parted -l
```

(lowercase L not 1)

Thanks.

---

