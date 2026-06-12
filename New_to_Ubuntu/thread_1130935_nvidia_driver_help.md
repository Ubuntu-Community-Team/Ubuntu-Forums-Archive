---
title: "nvidia driver help"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by sjmcyyc1960 on 2009-04-20
I am having problems installing my nvidia drivers in 9.04. I ad the same problem with 8.10 but the fix that got it working in 8.10 is not working in 9.04. Here is what my xorg.conf was in 8.10 and my drivers worked great:

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
Bus ID "1:0:0"
End Section

I used the 180.xx driver in both 8.10 and 9.04. I hace 2 8800GT vid cards. I did run the lspci command and the 2 cards were listed as 1:0:0 and 2:0:0. Can somebody tell me what I need to do to get this to work again?

Thanks
Sean

---

### Post by sjmcyyc1960 on 2009-04-20
Is there somewhere somebody can point me to get this info?
Thanks
Sean

---

### Post by Hospadar on 2009-04-20
I'd suggest (After making a backup of xorg.conf), go back to the default config, remove nvidia drivers, then install them with the hardware drivers manager.  I've been using that since 8.04 with no problems at all on any of my nvidia machines.

To go back to default config ```
sudo dpkg-reconfigure -*phigh xserver*-xorg
```I believe (again, make backups!)

---

