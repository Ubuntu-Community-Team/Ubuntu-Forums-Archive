---
title: "Help on Presario C712NR wireless"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by absolutnoob on 2007-12-07
Hi, I have installed Gusty on my Presario C712NR. I can get the wired network worked perfecctly, but not Broadcome wireless. I did read the related posts and documentations but unfortunately none of the instructions worked for me. :( I wonder if anyone could give me a walkthrough of how to set up the Ndiswrapper correctly. 

Here is my lspci for my wireless card:


> 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by buu700 on 2008-04-17
Hi. Sorry if this is a little late, but here: [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/203958/comments/23](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/203958/comments/23)

[QUOTE=buu700]To install the driver through ndiswrapper:

'sudo aptitude install cabextract ndisgtk'
Download the .exe file that installs the driver in Windows.
'cabextract [location of the .exe file]'
This will extract the drivers from the executable.

Now just run ndisgtk from either the main menu or with 'sudo ndisgtk' and browse to the .inf file that was extracted.
OR
'sudo ndiswrapper –i [location of the .inf file]'

'echo ndiswrapper | sudo tee -a /etc/modules && sudo modprobe ndiswrapper'[/QUOTE]

---

