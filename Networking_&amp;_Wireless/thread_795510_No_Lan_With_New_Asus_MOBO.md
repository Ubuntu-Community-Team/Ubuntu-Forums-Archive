---
title: "No Lan With New Asus MOBO"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by shakabra on 2008-05-15
I just built my first computer.  Everything went great, except I can't connect to my modem or router.  I installed an M2N-SLI MOBO from ASUS.  The ethernet driver is "forcedeth".  I have read about some bugs with this driver but none of the fixes have solved my problem.  I haven't tried the board with windows yet.  The led lights on the ethernet port are amber no green lights.  Has anyone had experience with this issue.  Any solution would be much appreciated.

---

### Post by chili555 on 2008-05-15
I was reading this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836) and the last post seems to be your same lil mobo. I suggest you do *lspci -v* and make sure you have an nVidia Corporation MCP55 Ethernet (rev a2). If not, stop and we'll look elsewhere. I was encouraged by this possible workaround:> 

This worked for me

Add the following line to /etc/modprobe.d/options

options forcedeth msi=0 msix=0

Then rebuild initramfs like this

sudo update-initramfs -u

---snip---

Reboot.

NOTE: if the update-initramfs bit goes wrong it could stop your system from booting - don't blame me - make sure you know how to fix it first.
I think that scary stuff at the end simply means type the command exactly, *exactly* as written after you have checked it three times and sworn to name your next child Linus. Proceed at your own risk! Please let us know so the searchers can see what worked or not.

---

### Post by shakabra on 2008-05-16
Yeah I saw that too, but it didn't help.  I bought an ethernet card for $15 and everything is hunky dory now.  I had called the the ASUS tech rep for any help.  They even had a special help line for linux users.  The tech rep just had me refresh my IP address.  When that didn't help he suggested i install windows.  Yeah right! spend $15 to fix this or $150+.  I told him to have a nice day.  Thanks for your help anyway!

---

