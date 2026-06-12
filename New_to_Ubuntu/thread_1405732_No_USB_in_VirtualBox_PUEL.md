---
title: "No USB in VirtualBox PUEL"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by dmaxel on 2010-02-13
Hi everyone,

I have a little problem with my VirtualBox (PUEL version, newest version, on Karmic). I am trying to use a VM running XP so that I am able to play Flight Simulator 2004 (I know there are some alternatives but I am dependent on FS2004). One of the things I need working on it is my joystick. I went into the settings for the VM, added a USB Device Filter from the list provided when adding one for the joystick (as well as some others), and started the VM. However, even when fully loaded, when I right-click the USB icon at the bottom, I am unable to enable any USB devices, as they are all greyed out. I tried Googling for this problem, but nothing. Any help on this?

---

### Post by bumanie on 2010-02-13
As far as I know you have to use the commercial version of virtualbox to get usb support. You are able to use it at home for free.

---

### Post by falconindy on 2010-02-13
Add yourself to the vboxusers group:

```
sudo gpasswd -a <your_username> vboxusers
```

Log out, log in. Profit.

---

### Post by dmaxel on 2010-02-13
Haha, wow, I feel stupid now. I had problems by accidentally mixing the OSE and PUEL versions together, and forgot to add myself to the group again after completely uninstalling everything and reinstalling the PUEL version. Thanks a lot.

Prize for helping me at my stupidity: :popcorn:

---

