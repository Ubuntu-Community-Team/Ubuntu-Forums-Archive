---
title: "[SOLVED] Wireless connect but does not browse the internet"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by bigbrovar on 2008-11-14
I have a problem. i am the system admin for a school. and the student use mainly ubuntu laptops. however of recent i discovered that some students cant browse the internet even though it connects to the network (at least ifconfig show it has an ip address) but i cant ping anything .. not even the firewall ip .. until i run dhclients ... now if thses were my laptop. i dont have a problem running dhclient to the world come to an end. am not comfortable telling these student many of whom already have a phobia for linux to open terminal and run dhclient evertime that they want to connect to the internet. please does anyone have the same problem. is this a bug?

the wireless card we use is Intel PRO/Wireless 3945ABG (which is very freedom friendly) please any help would be appreciated and would be helping in keeping linux on this laptops. thanks in adance.

PS.. this does not happen when on wireless

---

### Post by bigbrovar on 2008-11-14
well i think i solved it by changing to the latest kernel Linux version 2.6.24-21-generic from Linux version 2.6.24-19-generic and telling grub to boot the latest kernel by default. by editing menu.lst . now when i reboot the computer it connect to the wireless network bu default with any geeky codes. up me :)

---

