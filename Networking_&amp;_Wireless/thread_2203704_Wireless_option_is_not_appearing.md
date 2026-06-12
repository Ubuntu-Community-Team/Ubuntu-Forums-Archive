---
title: "Wireless option is not appearing"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by Vuris on 2014-02-04
I'm new to Ubuntu, and have been scouring the net for guides to help me get my wireless up and running. I'm currently running it on a desktop and I have a few adaptors (a net gear, a blue tooth, and another one like the blue tooth.) So for the sake of efficiency, I'll be giving what information I can. Any help would be loved.


```
vuris@vuris-desktop:~$ lsusb
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 04ca:3006 Lite-On Technology Corp. 
Bus 005 Device 002: ID 093a:2521 Pixart Imaging, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vuris@vuris-desktop:~$ 
```

When I click on the wireless button in the right hand corner of my screen, has about three options. Wired Network which is greyed out, the word disconnected below it, and VPN Connections.
Any help would be loved.:oops:

---

### Post by varunendra on 2014-02-06
Welcome to the forums Vuris !

It seems the following is your wireless dongle -
> **Vuris said:**
> ```
vuris@vuris-desktop:~$ lsusb
Bus 005 Device 003: ID **04ca:3006** Lite-On Technology Corp.
```

This is a relatively new chip and the driver for it is not available in older kernels.

So, what is your version of Ubuntu and the kernel in it? To answer this, and some related other settings, please post back the outputs of the following commands (while the wireless adapter is plugged in) -
```
lsb_release -d
uname -mr
sudo lshw -numeric -C network
nm-tool
rfkill list
dmesg | grep ath9k
```

The last command may not return any output, that is okay.

---

