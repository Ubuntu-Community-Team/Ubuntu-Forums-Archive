---
title: "How to find hardware specifications in Ubuntu?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by zeroandone on 2009-12-29
How can I find the hardware specifications of my computer?

---

### Post by lisati on 2009-12-29
From the command line:

**lspci** lists the PCI devices in your machine
**lsusb** lists USB devices
**cat /proc/cpuinfo** shows you info about your cpu.
A long one is **dmidecode**

---

### Post by baruch60610 on 2009-12-29
I'm not sure exactly what you're looking for.  One place to start is to go to the terminal (using gnome-terminal if you're in Gnome, or konsole if you're in KDE), and typing 'sudo lshw'.  lshw is a command to list your hardware.

HTH.

---

### Post by Mahngiel on 2009-12-29
you can download a nice app that shows everything, from the kernel info to your processor speeds and motherboard.

'sudo apt-get install sysv-rc-conf'

---

### Post by lykwydchykyn on 2009-12-29
lshw-gtk is a nice gui for lshw.

---

### Post by zeroandone on 2009-12-29
What I need is something like Device Manager in Windows. A graphic interface shows the complete hardware information of my computer.

I will give lshw-gtk a try. I remember that Ubuntu used to have such a UI under System->Preferences->Hardware Information, but now it is gone. I am using Lucid Lynx Alpha 1.

Thanks,

Jeffrey

---

### Post by sandyd on 2009-12-29
> **zeroandone said:**
> What I need is something like Device Manager in Windows. A graphic interface shows the complete hardware information of my computer.

I will give lshw-gtk a try. I remember that Ubuntu used to have such a UI under System->Preferences->Hardware Information, but now it is gone. I am using Lucid Lynx Alpha 1.

Thanks,

Jeffrey

this is why its called "alpha" software -its not finished yet. however, the menu link may appear again -once the development has finished

---

### Post by zeroandone on 2009-12-31
> **carlee said:**
> this is why its called "alpha" software -its not finished yet. however, the menu link may appear again -once the development has finished
I think the menu link is remove even in 9.10.

---

### Post by JimInLakeland on 2009-12-31
Go into "Ubuntu Software Center," and search for "Device Manager." It is quite similar to the Windows Device Manager.

Go there and install it. Here is an example of the output:

[IMG]http://www.jimbogames.com/images/dm.png[/IMG]

---

### Post by philinux on 2009-12-31
```
sudo apt-get install hardinfo
```


Menu item appears in Apps>system tools.

---

### Post by Cheesemill on 2009-12-31
```
sudo lshw -html > /tmp/lshw.html && firefox /tmp/lshw.html &
```

:)

---

### Post by zeroandone on 2009-12-31
> **JimInLakeland said:**
> Go into "Ubuntu Software Center," and search for "Device Manager." It is quite similar to the Windows Device Manager.

Go there and install it. Here is an example of the output:

[IMG]http://www.jimbogames.com/images/dm.png[/IMG]
Cool. Thanks a lot.

---

### Post by zeroandone on 2009-12-31
> **philinux said:**
> ```
sudo apt-get install hardinfo
```


Menu item appears in Apps>system tools.
Man, this one is even better. It shows tons of information about my system, and even performs benchmark test. I love it. Thanks.:popcorn:

---

### Post by JimInLakeland on 2009-12-31
> **zeroandone said:**
> Man, this one is even better. It shows tons of information about my system, and even performs benchmark test. I love it. Thanks.:popcorn:

Agreed!

---

### Post by JimInLakeland on 2009-12-31
> **philinux said:**
> ```
sudo apt-get install hardinfo
```
menu item appears in apps>system tools.

+1

---

