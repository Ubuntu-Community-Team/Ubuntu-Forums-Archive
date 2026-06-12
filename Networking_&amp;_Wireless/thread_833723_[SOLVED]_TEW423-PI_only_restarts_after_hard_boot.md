---
title: "[SOLVED] TEW423-PI only restarts after hard boot"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by coolbrook on 2008-06-18
Anyone else notice this?

I find that my wireless doesn't work if I restart the system from Ubuntu or if I use the physical reset button on my computer.

I need to restart by doing a system shutdown in order for my wireless to work when I boot.  Is there a command I can run to get this wireless PCI card up and running again after a restart or a better fix to resolve this problem?

---

### Post by coolbrook on 2008-06-20
bump

---

### Post by coolbrook on 2008-06-23
Anyone?  Bueller?

---

### Post by caljohnsmith on 2008-06-25
I don't know what your problem is, but I have a TEW-423PI also and have had no problems with rebooting. If you give more info, maybe we can troubleshoot what is going on and at least try to find a workaround or possibly a fix. Try looking at the output of "dmesg" for starters after reboot vs. shutdown/boot. I assume you are using ndiswrapper? When your wireless doesn't work, what is the output of ifconfig and iwconfig? Does "lsmod" show ndiswrapper is loaded?

---

### Post by coolbrook on 2008-11-02
I have the dmesg output, but the problem appears to be resolved with the Intrepid upgrade (clean install)

---

