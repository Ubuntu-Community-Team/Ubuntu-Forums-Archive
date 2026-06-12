---
title: "installing ubuntu on a USB through backtrack"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by h3llt0y0 on 2010-06-04
Is it possible for me to install ubuntu 10.04 on my USB while logged into Backtrack 4. A.K.A. installing from a USB to another while on the USB's linux os?  Thank you in advance for the help :D

---

### Post by c9-3Rr0r on 2010-06-04
dd comannd should be helpful 

```

dd if=/path/to/iso_file of=/dev/usb_drive

```

that will move iso image to the external usb drive make sure that u have correcly configured external drive and partition then without any problem you should be able to boot from that device

---

### Post by h3llt0y0 on 2010-06-21
um I am kinda new to this stuff so is it possible to post an example of what you just told me step by step please?  P.S. sorry for the time it took to reply :S

---

