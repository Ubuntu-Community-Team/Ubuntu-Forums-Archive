---
title: "How to switch back to automatic VGA driver install from manual installation?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by legolas_w on 2009-02-11
Hi
Thank you for reading my post
I finally managed to install Nvidia driver manually from its .run file. now I become aware that every time which a new kernel version become available I should do the installation again.

I want to revert back to the automatic installation which Ubunut itself was installing the restricted drivers.

any suggestion?

thanks

---

### Post by RomeReactor on 2009-02-11
Hi. If you still have the nvidia installer, switch to a console by pressing CTRL+ALT+F1; then, navigate to where the nVidia installer is located, and run:
```
sudo /etc/init.d/gdm stop
```
to stop the display; then, uninstall the driver:
```
sudo ./NVIDIA_INSTALLER.run
```
Just change NVIDIA_INSTALLER.run to the actual name of the file. Then, start the display again:
```
sudo /etc/init.d/gdm start
```
Now install the driver using the restricted driver manager in 'System->Administration->hardware Drivers'.

---

