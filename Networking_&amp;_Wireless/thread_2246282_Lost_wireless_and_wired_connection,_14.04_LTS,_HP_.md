---
title: "Lost wireless and wired connection, 14.04 LTS, HP 6735b"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by conor-tracey on 2014-09-29
Hi,
returning home I discover all connection lost.
no wireless networks appear in drop down list from top menu icon.
wired and wireless connections appear in 'edit connections' menu.

> ~$ lspci -vvnn | grep 14e4

gives me:

> 02:00.0 Ethernet controller [0200]: Broadcom Corporation Netlink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)

No sign of any wireless card :(

on reboot I get message 'you are now disconnected' as menu bar builds. Ubuntu runs fine, just no internet.

no response when I plug in an Ethernet cable to try and get a wired connection.


have read many posts about whole wireless issue, my wireless would usually drop out after an hour or two and require reconnecting using drop down menu from icon.


have tried various commands to turn on power to Ethernet card, 'echo on sudo tee says/class etc etc.' I get the response 'on'.


really desperate to fix since no internet, no email, no work possible and family on my case.


no updating or downloading possible (obviously).


please help, if possible...


I can use terminal commands if guided, but will need to transfer any files or updates from a work machine and try them out each evening since no other computer available at home.


thanks in advance.


conor

---

### Post by conor-tracey on 2014-09-29
SOLVED:

> rfkill list all

then

> rfkill unblock all

did the trick!

this thread provided the answer, after a whole evening of trawling the forums on an ipad mini!

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

...in the 'Debugging' section.

thank you, oh great forum.

Conor

---

