---
title: "Intel wireless card not recognised on Dell Inspiron 9400 laptop"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Irishpolyglot on 2007-05-21
Hi everyone!!
Ubuntu is installed and so far looks good... but there's no wireless Internet . I'm on a DELL Inspiron 9400 with Ubuntu 7 64bit. It workes fine on the wired connection.
I have an Intel Next-Gen Wireless-N Mini-Card (for Intel Core 2 Duo Processors).
In the network settings I can only see Wired Connection and Modem Connection - no wireless like in tutorial images... so the drivers aren't there for this card.
I entered
> lspci | grep -i network"
and I got back
> 0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
I tried a couple of sites to investigate the problem and got on to "ndiswrapper", but when I go through the tutorials (tried 2 different versions) I just get error messages since they don't apply to my system. Maybe I need a clearer idea of how to use it...
Then I was advised to try > sudo aptitude install linux-restricted-modules-generic and I got back > Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
How can I install the drivers on this? I can't find anything online (or in this forum) related to my computer or the Intel wireless card. Any advice? I am quite new to all this... can't wait to get it working fully!! The last thing someone suggested was to "modprobe the kernel module for that card"... but I don't know how to do that.. Will it help? How should I go about it? Any other advice??
Thanks a mil for your help!!

---

### Post by Kobalt on 2007-05-21
Please don't double post. To bring back your original post, if you had no answers, the last thing to do is to double post. Once in a while you can *bump* your thread if you'd like though...

---

