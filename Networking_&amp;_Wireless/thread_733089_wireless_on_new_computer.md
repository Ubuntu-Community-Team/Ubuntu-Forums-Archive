---
title: "wireless on new computer"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by zezerbing on 2008-03-23
I have my computer running ubuntu on a dsl router and everything is fine. Mysons is running XP on a wireless and it's fine. But i tried to hook a wireless to my daughter computer and it won't connect to the internet. The wireless is flashing with the router and seems to be working. Using Keir Thomas's book as a guide,network settings show the wireless is active.I tried to set up with DHCP, then I set up connections with a static IP address.Neither work(i might have that info wrong) . I deactivated firestarter on my computer. I tried to reboot. I called my provider and they were not much help. The disc that came with the router won't start.I installed ubuntu from a disc on her new hard drive but I want to install Edubuntu as her system. Thanks.

---

### Post by Sam Lars on 2008-03-23
Post the output of
```
lspci
ifconfig
iwconfig
```
On the computer with non-working wireless.

---

### Post by zezerbing on 2008-03-29
First,thanks for the help. But it didn't work. I entered the info in the terminal and it configured, but it asked for more. i closed the terminal, restarted the computer. but nothing changed.

---

### Post by superprash2003 on 2008-03-29
go to the terminal type the above commands i.e.
lspci
ifconfig
iwconfig

type one at  a time, you will get an output, just copy the output from the terminal(highlight the output and right click and click on copy) then right click and click on paste here..
the reason we need the output of those commands is so that we better understand your setup and problem and help you further

---

