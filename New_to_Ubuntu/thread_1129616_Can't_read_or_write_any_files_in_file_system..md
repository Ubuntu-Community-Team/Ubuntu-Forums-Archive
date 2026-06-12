---
title: "Can't read or write any files in file system."
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Ujjay on 2009-04-18
Hello I was trying to change permission of an external hard drive and in the process must have messed my file system up. I can no longer view files in my file system folder. Home folder is fine, I still have access to all my old documents, however I would still like to view the file system. Here are some pictures:

[http://img152.imageshack.us/img152/8283/screenshotm.png](http://img152.imageshack.us/img152/8283/screenshotm.png)

[http://img245.imageshack.us/img245/219/screenshot1e.png](http://img245.imageshack.us/img245/219/screenshot1e.png)

---

### Post by cariboo on 2009-04-18
Whats happens when you open a terminal and type:

```
cd /
```

then

```
ls -l
```

do you get any output.

What command did you use to change permissions? If you used a terminal just type:

```
history
```

Jim

---

### Post by llamabr on 2009-04-18
What did you do?  And what do you mean by file system folder?

---

### Post by Ujjay on 2009-04-18
Hello and thank you for your reply. Well let me give you background information. I couldn't access my 80gig maxtor drive with ubuntu on it, it was corrupted. I couldn't access files so I tried desperatly to get permission to get my files. Eventually I did, but a a cost. I screwed around with su, sudo, chmod 777, chgrp, chown, nautilus and others. My linux still works but...

My ubuntu won't boot unless my maxtor is connected as slave. Without the maxtor in, my POST screen says "please insert boot media". Maxtor now says me (ujjay) is part of its owner, but my file system doesn't.

Here are my responses:

cd / 

(No change)

ls -l

Permission denied

    1  desktop effects
    2  3d
    3  desktop
    4  sudo dpkg-reconfigure -phigh xserver-xorg
    5  vesa
    6  compiz
    7  firefox-p
    8  firefox -ProfileManager
    9  ./firefox -profilemanager
   10  program directory
   11  /firefox -profilemanager
   12  ./firefox -profilemanager
   13  execute cd
   14  program directory
   15  ./azureus
   16  /azureus
   17  su
   18  export PATH=/path/to/java/bin:$PATH
   19  cd azureus
   20  ./AZUREUS
   21  cp Azureus_(version)_linux-(platform).tar.bz2 /directory/to/install/in/.
   22  tar -xjf Azureus_(version)_linux-(platform).tar.bz2
   23  sudo
   24  cd
   25  cd/usr/java
   26  as/usr/local
   27  su
   28  sudo passwd
   29  su
   30  sudo displayconfig-gtk
   31  sudo apt-get install xserver-xorg-input-evdev
   32  cat /proc/bus/input/devices
   33  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
   34  sudo gedit /etc/X11/xorg.conf
   35  gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
   36  gconftool-2 –type int –set /apps/compiz/general/screen0/options/number_of_desktops 1
   37  sudo apt-get install desktop-effects
   38  gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
   39  gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
   40  sudo apt-get install compizconfig-settings-manager
   41  usr/share/games/
   42  usr
   43  usr/share
   44  * I sudo apt-get install freeciv
   45  * sudo apt-get install freeciv
   46  sudo apt-get install smc 
   47  d
   48  sudo apt-get install smc
   49  apt-get moo
   50  apt-get smc
   51  apt-get install smc
   52  sudo apt-get install smc
   53  strip
   54  touch
   55  sudo uninstall smc
   56  sudo apt get uninstall smc
   57  sudo apt-get uninstall smc
   58  sudo apt-get remove smc
   59  su
   60  sudo unmount /dev/sda2 
   61  sudo mkdir /mnt/windows
   62  sudo mount /dev/sda2 /mnt/windows
   63  su
   64  sudo mount -t ntfs-3g /dev/sda2 /mount/point -o ro,force,gid=100
   65  sudo fdisk -l 
   66  sudo mount /dev/sda1
   67  sudo mount /dev/sda2
   68  mount - ntfs-3g /dev/ sda2 /media/PRESARION -o force
   69  root
   70  su
   71  xev
   72  cat /proc/bus/input/devices
   73  sudo gedit /etc/X11/xorg.conf
   74  sudo apt-get install xvkbd xbindkeys
   75  gedit ~/.xbindkeysrc
   76  xbindkeys
   77  xbindkeys
   78  sudo apt-get install checkinstall build-essential libusb-dev
   79  sudo logitech_applet -s 800 -e
   80  sudo gedit /etc/init.d/local
   81  sudo chmod 755 /etc/init.d/local
   82  sudo update-rc.d local defaults
   83  sudo apt-get update && sudo apt-get install btnx
   84  apt-get update; apt-get install k3b +
   85  apt-get update; apt-get install k3b 
   86  root
   87  su
   88  cat /etc/network/interfaces
   89  ifconfig -a
   90  su
   91  /lib/modules/your-kernel-version/build/.config
   92  CONFIG_INPUT=y
   93  FIG_INPUT_MOUSEDEV=y
   94  FIG_INPUT_EVDEV=m
   95  FIG_USB=m
   96  y
   97  CONFIG_INPUT=y
   98  FIG_INPUT_MOUSEDEV=y
   99  FIG_INPUT_EVDEV=m
  100  FIG_USB=m
  101  FIG_USB_UHCI_HCD=m
  102  y
  103  CONFIG_INPUT=m
  104  FIG_INPUT_KEYBDEV=m
  105  FIG_INPUT_MOUSEDEV=m
  106  FIG_INPUT_EVDEV=m
  107  FIG_USB=m
  108  FIG_USB_UHCI=m(or similar)
  109  stall
  110  stall
  111  /lib/modules/your-kernel-version/misc/
  112  su
  113  chmod 777 /mount/point
  114  chmod 777 /mount/sdb
  115  sudo fdisk -lu
  116  su
  117  sudo chmodd 777 / -r
  118  su
  119  df -h
  120  dd if =/dev/sda1 of=dev/sdc1su
  121  su
  122  sudo nautilus
  123  su
  124  gksu nautilus
  125  /etc/fstab 
  126  su
  127  /etc/fstab
  128  su
  129  /etc/fstab 
  130  gksudo gedit /etc/fstab
  131  /etc/fstab
  132  gksudo nautilus 
  133  su
  134  cd /
  135  ls -l
  136  history

Thanks

---

### Post by Ujjay on 2009-04-18
> **llamabr said:**
> What did you do?  And what do you mean by file system folder?

I screwed around with chgrp, chmod and chown and now I can't boot without my mator as slave. This is really bad. By file system, I mean when you go to computer-file system, or go from home folder up. Essentially my ubuntu installation, and information and stuffs.

---

### Post by Ujjay on 2009-04-19
Hey, I am just considering reinstalling ubuntu over my partition. Will this boot (since my ubuntu won't boot without the maxtor as slave), will it boot without the maxtor, and will it effect my windows parition?

---

