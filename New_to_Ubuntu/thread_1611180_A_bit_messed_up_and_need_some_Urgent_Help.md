---
title: "A bit messed up and need some Urgent Help"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by D3SI on 2010-11-01
I installed this splash screen
> [http://gnome-look.org/content/show.php/Ubuntu+10.04+and+10.10+Plymouth+Splash?content=128607](http://gnome-look.org/content/show.php/Ubuntu+10.04+and+10.10+Plymouth+Splash?content=128607)

it's working when computer is shutting down but not when loading....

how do I remove the theme?

i followed these commands to install it
```

sudo cp -R INT2MIL-Ubuntu-10.04-Eng/ /lib/plymouth/themes/
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/INT2MIL-Ubuntu-10.04-Eng/INT2MIL-Ubuntu-10.04-Eng.plymouth 100
sudo update-alternatives --config default.plymouth  #here, choose the number of the theme you want to use then hit enter
sudo update-initramfs -u
```

Thank You

---

