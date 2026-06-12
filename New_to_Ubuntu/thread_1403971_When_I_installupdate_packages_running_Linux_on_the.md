---
title: "When I install/update packages running Linux on the LiveCD, are they updating my HD?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by laurabray on 2010-02-10
I'm running the LiveCD and I was wondering if updating packages while running from the LiveCD will update my Linux on the hard drive?

---

### Post by Satoru-san on 2010-02-10
no, they are not.

If you want them to do this:

open up a terminal.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
apt-cache search <PACKAGE YOU WANT>
apt-get install <PACKAGE>
```

Otherwise, if you are wondering if you mean you need to install ubuntu to your computer in order for it to function, the livecd is just that, its live, not actually even touching your harddrive.

---

