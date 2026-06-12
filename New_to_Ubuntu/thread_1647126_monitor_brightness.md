---
title: "monitor brightness"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by senorian on 2010-12-16
I need to reduce the brightness of the monitor. I am using a dvi connection and a Nvidia gpu. Ubuntu 10.04
I cannot find the control window for the Nvidia card.
I know that when using the vga connection the contrast and brightness controls on the monitor (Dell 2405) work. and the quality of any text seems just as good as that using a dvi connection
I would also like to know how to install "glipper"
Thanks

---

### Post by Rex Bouwense on 2010-12-16
you shouldn't have a problem installing glipper.  Just go to Applications->Ubuntu Software Center.  The search for glipper.  Click to install.

---

### Post by matt_symes on 2010-12-16
Hi

On my laptop i can change the brightness from the command line by...

```
sudo -i
```to enter a root shell
```

echo -n 50 > /proc/acpi/video/VGA1/LCD/brightness
```then 

```
exit
```The values of n are 0 - 100. The folders VGA1 and LCD might be different on your system (you will have to look) but hopefully that, or something similar, will work.

Kind regards

---

### Post by KL_72_TR on 2010-12-16
I hope to be helpful with this. Click: System > Preferences > Monitor, on the icon that will pop-up click 'Yes' and in the next window you can see for the brightness.

---

### Post by senorian on 2010-12-18
Thanks but I have a desktop and no such file
kl 72tr--there is no "yes"
Thanks

---

