---
title: "Prepare partitions."
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Legendman3 on 2010-07-27
You have probably seen this problem and answered it before but... Im trying to install 64-bit ubuntu 10.04 desktop edition on my laptop. When I get to step 4 its blank and the buttons are all grayed out. My hard drive just got wipe and theres nothing on it. Help. :(

---

### Post by cariboo on 2010-07-28
The ubuntu installer sometimes has problems detecting Sata drives, you can try manually mounting the drive, then when you get to the pertitioner it may get detected. otherwise, use the alternate install iso, as it has no problems detecting any type of drive.

You can get the alternate install iso [here]("http://releases.ubuntu.com/lucid/").

---

### Post by philinux on 2010-07-28
> **Legendman3 said:**
> You have probably seen this problem and answered it before but... Im trying to install 64-bit ubuntu 10.04 desktop edition on my laptop. When I get to step 4 its blank and the buttons are all grayed out. My hard drive just got wipe and theres nothing on it. Help. :(

How about trying either gparted or the diskutility. Both in system admin menu.

---

### Post by gordintoronto on 2010-07-28
To run Gparted, boot from the LiveCD, open accessories/Terminal, and paste in this command:
sudo gparted

---

