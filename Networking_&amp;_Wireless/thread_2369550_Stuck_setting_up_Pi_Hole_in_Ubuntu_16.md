---
title: "Stuck setting up Pi Hole in Ubuntu 16"
date: 2017-08-24
forum: Networking &amp; Wireless
---

### Post by sanjusimon on 2017-08-24
Hi, as per this post ( [https://arstechnica.com/civis/viewtopic.php?f=17&t=1379399](https://arstechnica.com/civis/viewtopic.php?f=17&t=1379399) ) I have installed the latest Curl. Beyond that I have no clue what's going wrong. The post uses Debian 9 though. 
Ubuntu is installed on a Virtual Machine (Hyper V) with my Realtek WiFi adapter  as a network switch. 
I type
 nano /etc/network/interfaces
And I type 
    auto eth0
    iface eth0 inet static
        address 192.168.1. 100
        netmask 255.255.255.0
        gateway 192.168.1.1

But nothing seems to happen. Where am I seem to go wrong? And as per the post, after these commands I should reboot. But is this via any command? If so what?

My router is at 192.269.1.1
Thanks

---

### Post by TheFu on 2017-08-24
192.269.1.1 is not a valid IPv4 address.

Details matter, greatly.

---

### Post by sanjusimon on 2017-08-24
Sorry it's a typo. My router is at 192.168.1.1

---

### Post by wyliecoyoteuk on 2017-08-29
You need to save the file.
CTRL+O, enter, then CTRL+X
followed by sudo reboot


[https://wiki.gentoo.org/wiki/Nano/Basics_Guide](https://wiki.gentoo.org/wiki/Nano/Basics_Guide)

---

### Post by TheFu on 2017-08-29
Whenever any config file is modified, it is almost always required that the processes dependent on it be either reloaded or restarted or told to reload (-HUP signal).  Rebooting is almost never required.

But ... under some situations it is easier to reboot, if that is possible.  Most of my systems cannot be easily rebooted on a whim.

---

### Post by wyliecoyoteuk on 2017-08-29
I quite agree, but the OP seems to be following a tutorial to install Pi Hole on a VM.
It would seem that he does not understand nano or the command line.
I was merely adding the missing instructions.

---

