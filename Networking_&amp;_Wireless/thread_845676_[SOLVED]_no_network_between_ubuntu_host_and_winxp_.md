---
title: "[SOLVED] no network between ubuntu host and winxp guest"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by imjscn on 2008-06-30
my host ubuntu connect to internet through ADSL, setup by pppoeconfg. 
Now I installed Vmware Player, use Nat for network. Also installed Vmware Tools through extracting windows.iso file from Workstation.

Guest Winxp is running smoothly except no internet/network. Ethernet tab is connected(Nat),  ipconfig returns nothing.

Host ubuntu doesn't recognize anything.

I installed Samba and followed russ's tutorial to set up things, but the result is the same.

How can I let host and guest notice each other?

---

### Post by superprash2003 on 2008-06-30
in your vmware settings, have you set the network adapter to bridged mode..??

---

### Post by imjscn on 2008-06-30
no, I didn't. because I use EasyVM to make the machine and I choosed Nat. 

Now I tried to click bridge, it doesn't give me any message either.

In the winxp device manager, I see a yellow question mark at the Ethernet Controller.

---

### Post by superprash2003 on 2008-07-01
that could well be the problem.. you need to look for drivers i guess!!

---

### Post by imjscn on 2008-07-01
hi guys, good news...I just figured out...in my VM, I had default EasyVM's settings including Nat of intelpro1000, now I changed it to Nat of VMnet. It works.
The thing is--intelpro1000 works for vista, not for XP, although EasyVM suggest default settings. 
No, not the drivers, before I solved the problem, I tried to install Dell's drivers, broadcom can install, but graphic card get rejected by VMware. and the installed broadcom didn't work out things.

---

