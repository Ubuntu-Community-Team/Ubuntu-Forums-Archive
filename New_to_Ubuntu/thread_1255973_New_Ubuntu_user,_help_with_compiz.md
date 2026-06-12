---
title: "New Ubuntu user, help with compiz"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Gargintua on 2009-09-02
Hey, i am new to ubuntu forums as well as ubuntu its self. I have ubuntu 9.04 installed and i also downloaded compiz fusion version 8.2 using 'add/remove programs'. it was working all fine for 1 day before i updated it. 

First the fusion icon stopped working so i  reinstalled it, still no fix. then i tried searching 'compiz' and deleting everything shown before installing it again.

and this time the 'compiz config settings manager decidded to stop working (it also stops the min, max, exit buttons on each window).

I really don't know what to do and i'm conscider reinstalling ubuntu for the 2nd time.

I have been googling/looking through forums for a whole day now but having trouble understanding the solution because i am new. any help will be gladly appreciated.

thnx, nick.

---

### Post by theozzlives on 2009-09-02
what kind of video do you have? If you don't know go to Applications > Accessories > terminal. type lspci, and post the contents.

To install compiz all you need are compiz-core, compiz-fusion, and compizconfig-settings-manager.

---

### Post by nhasian on 2009-09-02
compiz comes install by default with ubuntu.  you dont need to add it.  you do however need to add the configuration manager if you want to tweak the settings like change the minimize or close window settings.  you can add the compizconfig-settings-manager by copy & pasting this line into a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

check in system->Administration->Hardware Drivers and see if you need to enable one for your video card.

also look in system->preferences->appearance and in the Visual Effects tab make sure its set to Extra.

---

### Post by Gargintua on 2009-09-02
[FONT=monospace]I typed in 'lspci' and this is what came up

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

now i know that copiz is actually installed because of the wobbly windows and cube but i can't change anything because the compiz fusion icon as well as the compizconfig settings manager still dont launch. everythings installed though and when i click on compizconfig settings manager u can see it in the 'tabs' and it says 'starting' but then it never loads the settings manager. 
[/FONT]

---

### Post by 3rdalbum on 2009-09-02
> **Gargintua said:**
> Hey, i am new to ubuntu forums as well as ubuntu its self. I have ubuntu 9.04 installed and i also downloaded compiz fusion version 8.2 using 'add/remove programs'. it was working all fine for 1 day before i updated it. 

First the fusion icon stopped working so i  reinstalled it, still no fix. then i tried searching 'compiz' and deleting everything shown before installing it again.

and this time the 'compiz config settings manager decidded to stop working (it also stops the min, max, exit buttons on each window).

I really don't know what to do and i'm conscider reinstalling ubuntu for the 2nd time.

I have been googling/looking through forums for a whole day now but having trouble understanding the solution because i am new. any help will be gladly appreciated.

thnx, nick.

1. Compiz comes preinstalled on Ubuntu, and they are up to version 0.9 not 8.2; so I have no idea what you installed.

2. Software that you download generally doesn't get corrupted on Linux, so reinstalling it is usually a waste of time because it doesn't solve any problems.

---

### Post by Gargintua on 2009-09-02
here is a opensuse post with the same problem as me

[http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-desktop-environments/384059-compiz-fusion-compizconfig-settings-manager-problems.html](http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-desktop-environments/384059-compiz-fusion-compizconfig-settings-manager-problems.html)

---

### Post by theozzlives on 2009-09-02
Go to System > Administration > Hardware Drivers and make sure your Video Driver is activated.

---

