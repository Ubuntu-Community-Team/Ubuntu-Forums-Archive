---
title: "Ubuntu on VMWare 6 on WinXP"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by manuelb on 2007-06-14
Hi all, i've got a problem with this setup: i've a brand new amd64 dell machine where i installed VMWare 6: i setup a virtual machine for installing Ubuntu and the installation went fine.
The problem is: i want to give a static ip address to the Ubuntu virtual machine, but there is no way to be able to obtain connectivity within two consecutive reboots :(
The behavior is silly: rebooting the machine, once in a while, i got the network working, rebooting another time i get no connectivity at all, but the fact is "ifconfig" still shows me my correct ip address as well as the default gateway route.
I also noticed that insisting with "sudo /etc/init.d/networking restart" sometimes does work, but not all the times and the "dmesg" output only show "interface up" or "interface down".

Any help would be appreciated!

Thank you,
Manuel

---

