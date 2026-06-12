---
title: "How to meet the minimum software reqs for driver install"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by killbydemons on 2008-12-24
I'm confused about the requirements mentioned in the [readme]("ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/README/README.txt") for some drivers I want to install.  How do I make sure I meet all these requirements before attempting to install the drivers?

---

### Post by zephyrcat on 2008-12-24
The easiest way is to look at the technical release notes for the version of Ubuntu you are using:

[http://www.ubuntu.com/getubuntu/releasenotes/810overview](http://www.ubuntu.com/getubuntu/releasenotes/810overview)

It looks like you should be fine.

Instead of installing the nVidia drivers from their website, though, I would go to System > Administration > Hardware Drivers. That will give you an automtic way of installing the nVidia drivers.

---

### Post by killbydemons on 2008-12-24
nah, I've tried that already and it doesn't work.  Nothing shows up in the Hardware Drivers window, and the ones I want to install can't be fetched by Envy.

---

### Post by zephyrcat on 2008-12-24
Try just going ahead with the install. It should work fine, since there is probably a kernel module for Ubuntu already compiled.

---

### Post by killbydemons on 2008-12-24
I've tried going ahead with the install already, I get an error message about "You appear to be running an X server; please exit X before installing...".

---

### Post by zephyrcat on 2008-12-24
Control + Alt + Backspace will quit X. Warning: There will be no GUI until you restart or type "startx" (without the quotes). Good luck and happy holidays!

---

### Post by igknighted on 2008-12-24
> **zephyrcat said:**
> Control + Alt + Backspace will quit X. Warning: There will be no GUI until you restart or type "startx" (without the quotes). Good luck and happy holidays!

Ctrl+alt+backspc will only restart X.  You need to hit ctrl+alt+f1 to switch to a text only terminal, then type the command 'sudo /etc/init.d/gdm stop'.  Replace gdm with kdm if you use kubuntu.  Now you have X stopped and can run the installer.

EDIT: make sure you have the build-essential and kernel-headers packages installed.

---

### Post by jerome1232 on 2008-12-24
> **killbydemons said:**
> I've tried going ahead with the install already, I get an error message about "You appear to be running an X server; please exit X before installing...".

Basicly make sure you have build-essential and you may need linux-source and linux-headers.

```
sudo apt-get update
sudo apt-get install build-essential linux-headers linux-source
```

Press ctrl+alt+f1, login
```
sudo /etc/init.d/gdm stop
cd /path/to/installer
sudo chmod +x NVIDIA(just press tab to auto complete the name)
./NVIDIA(again use tab to auto complete the name)
sudo nvidia-xconfig
sudo /etc/init.d/gdm start
```

Remember Linux is case sensitive.

---

