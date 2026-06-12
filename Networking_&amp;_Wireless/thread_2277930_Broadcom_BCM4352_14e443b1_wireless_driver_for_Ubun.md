---
title: "Broadcom BCM4352 14e4:43b1 wireless driver for Ubuntu 12.04, Kernel 3.13"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by devon6 on 2015-05-12
Hi all, 

I've got troubles getting wireless to run on Ubuntu 12.04.3, Kernel 3.13. The hardware is a Dell XPS 13. I've tried solutions such as installing bcmwl-kernel-source and b43-firmware but to no avail my wireless still doesn't work. The hardware switch for wireless is enabled on the keyboard and in the BIOS settings.

I looked around for compatible drivers or solutions but haven't tried one that works yet.

I would greatly appreciate if anyone has any knowledge or insight on getting the wireless to work for my Dell XPS 13. Thank you

---

### Post by Pilot6 on 2015-05-12
Please give output of

lspci -knn | grep Net -A2
rfkill list

---

### Post by Pilot6 on 2015-05-12
Ad there are solutions like this
[http://askubuntu.com/q/432933/167850](http://askubuntu.com/q/432933/167850)

But if you upgrade to 14.04, it should work out-of-the-box.

---

### Post by devon6 on 2015-05-13
Hi,

 Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]
    Kernel driver in use: wl
turtlebot@turtlebot-XPS-13-9343:~$ rfkill list
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
turtlebot@turtlebot-XPS-13-9343:~$ 



Is the output of those commands. I've tried that solution Pilot6 but it didn't work. Upgrading to 14.04 is out of the picture since the software I'm dependent on builds off of 12.04 Precise

---

### Post by devon6 on 2015-05-13
Strange. It seemed to work after I installed the most recent version of bcmwl-kernel-source found here [https://launchpad.net/ubuntu/trusty/amd64/bcmwl-kernel-source/6.30.223.248+bdcom-0ubuntu0.1](https://launchpad.net/ubuntu/trusty/amd64/bcmwl-kernel-source/6.30.223.248+bdcom-0ubuntu0.1).

The other versions of bcmwl-kernel-source that I installed via debs didn't fix the problem.

Thanks guys for the help!

---

