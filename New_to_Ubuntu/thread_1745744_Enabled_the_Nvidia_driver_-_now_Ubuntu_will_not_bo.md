---
title: "Enabled the Nvidia driver - now Ubuntu will not boot!"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by mr_luksom on 2011-05-01
I enabled the Nvidia driver in my 11.04 install, as I had previously used it in 10.10, however it is now stopping ubuntu from booting.

I am not so interested in getting too the bottom of why it doesn't work, but I would like to disable it so I can use my computer again.

I can get to a cli by using the tty's 1-6. Is it possible to remove the Nvidia driver in the terminal?

---

### Post by Adanufgail on 2011-05-20
I am also having the same problem. I have Xubuntu 11.04, and after installing the latest nVidia drivers, I get stuck during boot.

---

### Post by TeoBigusGeekus on 2011-05-20
```
sudo rm /etc/X11/xorg.conf
```
It won't remove the drivers, but you will (probably) be able to go into gui to uninstall them.

---

### Post by gsmanners on 2011-05-20
If that doesn't work, you could try:

```
sudo apt-get remove nvidia-current
```

Then reboot.

---

### Post by kosach on 2011-12-11
Hi all,
I also have similar problem - I get the message about hci0 timer timeout something.
I solved it by replacing xorg.conf with xorg.conf.backup (which was the original file). Hope it helps.

---

