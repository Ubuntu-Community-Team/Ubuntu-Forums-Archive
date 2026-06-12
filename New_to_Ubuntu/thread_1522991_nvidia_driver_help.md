---
title: "nvidia driver help"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by j0hnr on 2010-07-02
hi there ok what iam trying to do is install the nvidia driver but keeps saying x is started how can i close down to command line with no x loaded thanks

this is my card 00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

---

### Post by 3rdalbum on 2010-07-02
Don't do it that way.

Go to System > Administration > Hardware Drivers and you'll be offered the correct driver for your card. It will be one-click to install and it will stay in sync with your kernel, which the download from Nvidia will NOT do.

If Hardware Drivers does not offer you a driver, then go into Synaptic Package Manager and click on the Reload button.

---

### Post by j0hnr on 2010-07-02
well it came up with 3 i tried them all every time it reboots it goes all to funk :(
the 3 versions i tried were 185 / 173 / 96 tested in that order iam on 10.04 lts

---

### Post by stderr on 2010-07-03
You may want to try some of the configuration commands post-reboot before dismissing the ppa versions which 3rdalbum recommends. T

There are some benefits to running the latest drivers from nvidia's site. However, the main 2 disadvantages are: 1) no automatic updating, and 2) when you install a kernel update and reboot, you'll likely find you need to repeat the process and reinstall the driver (although there's a shortcut to regenerate the DKMS module).

Anyway, that aside, you need to 1) Log Out. This'll take you back to the GUI login screen. Then you need to 2) switch to another tty with Ctrl+Alt+F2, and log in. Finally, you need to 3) stop **gdm** with:

```
sudo service gdm stop
```

You can then install your nvidia driver - good luck!

---

### Post by 4Orbs on 2010-07-03
Just so you know: If you are using Ubuntu 10.04 and you install the correct driver from the Hardware Drivers menu... the Ubuntu splash page will go to funk. However, once you make it to the login screen everything will be wonderful. Hopefully the Ubuntu developers are working on some sort of fix for the ugly bootscreen with nvidia drivers. There are already workarounds if you feel ambitious, but the wart is only visible for a moment.

EDIT: And installing the driver from nvidia's website won't make any difference in the bootsplash screen.

---

### Post by j0hnr on 2010-07-03
tried all ways here thanks guys i will try figure it out.
4Orbs it just goes to shell i even type startx gives out errors

---

