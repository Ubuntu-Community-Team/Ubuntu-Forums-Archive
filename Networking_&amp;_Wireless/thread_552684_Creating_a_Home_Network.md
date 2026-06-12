---
title: "Creating a Home Network"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by Ulysses on 2007-09-16
Hello

I have an IBM Thinkpad, Pentium 3, 733, with 512MB RAM running Ubuntu 6.06. It is connected with a Wireless G card to a Wireless B router (these are all hand-me-downs)
I have a Pentium 4, 2.88 gHZ, with 512 MB RAM running Ubuntu 7.10, connected on a gigabit LAN
I want to share files between the two machines on my home network and while I have read about Samba I can't make heads or tails on how I am supposed to use it to make it work
Who can point me in the right direction? Bear in mind, not the sharpest knife in the drawer, me ; so whoever is sending me instructions please be sure to type slowly so I understand you

Any and all help is greatly appreciated.

Regards,
RAR

---

### Post by newlinux on 2007-09-16
These are good places to start:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

Read those, and let us know where you have questions or run into problems.

---

### Post by louieb on 2007-09-16
Linux to Linux is pretty easy if you have the same user name(s) on both machines.
1st set up both machines to have a static IP I did that using the lan ip configuration tool on my Netgear router. 
Forget samba unless you have windows computers too. 
2nd install openssh-server on both machines. You can use synaptic or apt-get to do that.
3rd. open places>conect to server> choose ssh from the drop down box, then enter the ip address of the other pc. Your done. You should see the other machine in the places menu now.

---

### Post by Ulysses on 2007-10-03
Hey

Neglected to get back to the thread
That's bad form on my part ; sorry

But the last method? Absolutely rocked! I'll install Samba if I ever need to use my work computer with personal files (Windows 2000 on an old, old, Dell Inspirion)

Thanks a bunch, folks, for the great answers and good response

RAR

---

