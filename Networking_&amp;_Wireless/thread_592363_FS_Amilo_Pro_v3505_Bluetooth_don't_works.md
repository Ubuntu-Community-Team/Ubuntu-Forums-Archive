---
title: "FS Amilo Pro v3505 Bluetooth don't works"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by za12 on 2007-10-26
Hello. Help me,

Who collided with it, help to solve a problem laptop Fujitsu-Siemens Amilo Pro v3505.

Has established on it UBUNTU 7.10, all works except for Integrated Bluetooth

network driver ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1

1. Wi-fi is Ok;
2.Bluetooth don't works.

Who collided with it, help to solve a problem

---

### Post by markmaus on 2007-10-26
I have a similar problem with my Fujitsu P7120 laptop running Gutsy and Atheros.  Wifi works fine.  My Logitech bluetooth mouse seldom connects when using the Bluetooth Manager interface.  But when I open a terminal and type  "hidd --server --search" as root (without the quotes) it will connect 95% of the time.  If anyone knows how to configure a bluetooth mouse to stick, so that it just comes up automatically when I boot, please respond.  Thanks in advance.

---

### Post by za12 on 2007-10-26
All works, if I shall include Wi-fi and Bluetooth from under Windows Vista. After &#1087;&#1077;&#1088;&#1077;&#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080; I load Ubuntu and all works. And how to make so that it was not necessary to include all from under Vist

---

### Post by markmaus on 2007-10-26
I am happy to hear you got it to work.  Although I don't understand how you did it.

---

### Post by za12 on 2007-10-26
From under ubuntu 7.10 does not join bluetooth, it works only if is started from windows vista

---

### Post by markmaus on 2007-10-27
Success!  Running Ubuntu 7.10, go to System/Preferences/Bluetooth Preferences. Make sure your bluetooth mouse is set as a trusted device and the Mode of Operation is set to Visible and Connectable for Other Devices. Then reboot and make sure that you are moving the mouse around when you get to the end of the orange progress bar that displays during the boot up process.  Works every time for me.

---

### Post by za12 on 2007-10-29
U see, the question is how to activate the BT adapter.
It easilly gets to run out of Windows interface and that makes me think that I do not have some software or do not know some commands on how to activate it.
Ubuntu doesn't see the adapter.
Laptop function keys do not work under Linux, so if I start it from windows and reboot i can access it from Linux as well.....
Is there any way to solve this problem ASAP?

Thanks a lot =)

---

### Post by za12 on 2007-10-29
???? :(

---

### Post by hugoeng on 2007-12-11
I have a similar problem with my Amilo Pro 3205. According to the Fujitsu support site, the bluetooth drivers arent available for download, only an updater. I dont know but this might be the problem.
As I havent got hold of the install cd yet  and has viped the harddrive no bluetooth is available in either Windows XP or Ubuntu.
I have bluetooth enabled in BIOS but lsusb and hcitool scan shows no adapters.

Edit: Hmm, pressing Fan + Esc worked too.. Damn Im a noob.

---

