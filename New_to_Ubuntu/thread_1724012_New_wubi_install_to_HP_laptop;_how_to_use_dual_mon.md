---
title: "New wubi install to HP laptop; how to use dual monitors?"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by dcoaster on 2011-04-07
I just installed Ubuntu 10.10 through Wubi on my HP dv6t laptop. When I installed the OS, only my laptop's screen would work and the external monitor (through HDMI) just had random fuzz continuously. I went into the monitor settings and it doesn't recognize the other monitor. I've done some research and found that I shouldn't install the closed source drivers that it recommends because it will mess up 10.10 at boot. Is this true? If so, what do I need to do to get two monitors working?

Thanks!

---

### Post by 123456789123456789123456 on 2011-04-07
I don't know what driver is needed, however that is mostly true.  I have experienced problems with wubi installs before.  one most notably is that I have an wubi install on my machine, since my video card is ati, and since windows did not have the full driver for the video card installed, ubuntu therefore would not reconize the card.  secondly after I finally got all the drivers for the card downloaded, the installation reconized the card, but was unable to load the specialized display manager.  I'm hoping a fresh install of 11.04 with wubi will repair this issue.  if not I am thinking of duel booting the system.  the only problem with dual booting is the shrinking the vista partition, which I believe that Ubuntu has gotten better at doing lately.

---

### Post by beew on 2011-04-08
Forget about WUBI, if you want to experience Ubuntu fully give it its due and do a real install. Either with a dual boot or install it in an external drive. My 2 cents.

---

### Post by dcoaster on 2011-04-11
I'm thinking about dual-booting, but I won't be able to perform the transition until this summer. However, does anyone have an idea how to enable both the laptop screen and the external monitor connected through HDMI with the open source ATI drivers on Ubuntu 10.10?

I've done some searching, but it seems as though installing the proprietary drivers would cause the system to go blank at boot. I want to avoid this which is why I'm using the open source drivers. If it makes a difference, I do not have an xorg.conf file in the /etc/X11/ directory.

---

### Post by beew on 2011-04-11
> **dcoaster said:**
> I'm thinking about dual-booting, but I won't be able to perform the transition until this summer. However, does anyone have an idea how to enable both the laptop screen and the external monitor connected through HDMI with the open source ATI drivers on Ubuntu 10.10?

I've done some searching, but it seems as though installing the proprietary drivers would cause the system to go blank at boot. I want to avoid this which is why I'm using the open source drivers. If it makes a difference, I do not have an xorg.conf file in the /etc/X11/ directory.

WUBI is limiting and installing proprietary drivers is probably more complicated than if you would in a real install, and it is not difficult to make a real install.

You can install in an external hard drive if your computer supports booting from usb hard drives.

Check out this tutorial.
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

You can use the same procedure for full install into an external hard  drive instead of a usb flash drive (runs much faster) That would give  you a real Ubuntu install with all the power and flexibility the OS has  to offer (including installing proprietary graphic drivers and so on)

This is for 10.04 but for 10.10 it is similar. Basically you boot into a live usb (or CD) and then install as usual except you install into the external drive instead of the internal one.

The main points are.

1) Choose manual install even if you use the entire hard drive, make sure you are installing into the correct drive. it would be something like sdc (sda is your internal drive, sdb would  be the live usb you use for installing,--if you use that instead of a  live cd for installing) But check carefully.
2) Using manual install you can control where the bootloader is going to be installed. Make sure it is installed in the external drive (the target, say sdc)
3) You should make two partitions, the mount point of the first one should be / (the root partition) ,  it should be 15 -20G (actually you could use less, but just to be safe) and then you should have a /home partition to store data and settings. It can be as big as you want. Both should be formatted as ext4.

P.S. As said this is a full and real install and you can install proprietary driver like you would normally. But if you don't then this is fully portable in that you can plug it in most computer and instantly run Ubuntu. If you install proprietary driver then of course you would have problems with machines which have  different graphic cards.

---

### Post by dcoaster on 2011-04-11
I appreciate the thoughts and ideas. I definitely will be doing a full install, but in the mean time, I'm wondering if anyone has been able to use two monitors through HDMI with the open source driver?

If so, what steps do I need to follow in order to enable it? When I go to the Display settings, it only "sees" one monitor (laptop screen) and not the external. Also, I've tried looking for an xorg.conf file, but have not found one in it's typical location. I believe that file is where I would check to see if it recognizes another monitor.

---

### Post by bcbc on 2011-04-11
> **beew said:**
> WUBI is limiting and installing proprietary drivers is probably more complicated than if you would in a real install, and it is not difficult to make a real install.

You can install in an external hard drive if your computer supports booting from usb hard drives.

Check out this tutorial.
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

You can use the same procedure for full install into an external hard  drive instead of a usb flash drive (runs much faster) That would give  you a real Ubuntu install with all the power and flexibility the OS has  to offer (including installing proprietary graphic drivers and so on)

This is for 10.04 but for 10.10 it is similar. Basically you boot into a live usb (or CD) and then install as usual except you install into the external drive instead of the internal one.

The main points are.

1) Choose manual install even if you use the entire hard drive, make sure you are installing into the correct drive. it would be something like sdc (sda is your internal drive, sdb would  be the live usb you use for installing,--if you use that instead of a  live cd for installing) But check carefully.
2) Using manual install you can control where the bootloader is going to be installed. Make sure it is installed in the external drive (the target, say sdc)
3) You should make two partitions, the mount point of the first one should be / (the root partition) ,  it should be 15 -20G (actually you could use less, but just to be safe) and then you should have a /home partition to store data and settings. It can be as big as you want. Both should be formatted as ext4.

P.S. As said this is a full and real install and you can install proprietary driver like you would normally. But if you don't then this is fully portable in that you can plug it in most computer and instantly run Ubuntu. If you install proprietary driver then of course you would have problems with machines which have  different graphic cards.
I think I already pointed out to you that it makes no difference whether you are using Wubi or not when it comes to installing graphics drivers. Please stop spreading misinformation.

---

### Post by Blasphemist on 2011-04-11
I'm on natty now but all the way back to koala when I first started using my external monitor it was plug and play. I don't have mine connected via HDMI though. The multiple monitors app in the software center is a gui for at least part of xrandr and lets you set resolution and position.

---

### Post by dcoaster on 2011-04-13
@Blasphemist: Do you have an idea as to why the monitor is not even being recognized even though it's plugged in? Multiple monitors app didn't see the monitor either.

I appreciate the help guys.

---

