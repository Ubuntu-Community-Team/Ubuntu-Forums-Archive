---
title: "Nvidia driver broken?"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-12-10
I updated my system last week through the normal channels and after I restarted I got the Ubuntu splash screen and a login prompt which wouldn't accept my password. I traced the problem in a previous thread to my video driver. I'm using a GEForce 7200 GS video card and was running the most current version of the Nvidia driver. but because I can't login to disable the driver I can't reinstall it. any help in fixing this problem would be appreciated.

---

### Post by sikander3786 on 2010-12-10
Press Ctrl + Alt + F1 at your login screen. Type your credentials and log in to tty1 and do these commands.

Reconfigure your graphics:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Ignore if there is an error and proceed to next one. Remember capital 'X' for X11 ;-)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot:

```
sudo shutdown -r now
```

If you are still unable to log-in, you can uninstalled the drivers by using this command.

```
sudo apt-get remove --purge nvidia-current nvidia-common nvidia-settings
```

Again reboot and if needed, re-configure your graphics once more.

---

### Post by Messyhair42 on 2010-12-10
it seems to have fixed itself without me doing anything else, or at least i was able to start it up with no apparent problems. should I disable or reinstall any graphics units or just leave it as is?

---

### Post by sikander3786 on 2010-12-11
You mean you did none of the commands above and it got fixed itself?

If yes, All is well :-)

If you get problems later, remove and re-install the drivers from System > Administration > Additional Drivers/Hardware Drivers.

---

### Post by Messyhair42 on 2010-12-11
Thank you. something similar to this has happened before, with the same solution, it just took a lot longer this time.

---

