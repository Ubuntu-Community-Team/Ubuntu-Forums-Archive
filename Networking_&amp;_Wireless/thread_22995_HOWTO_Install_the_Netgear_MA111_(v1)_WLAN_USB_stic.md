---
title: "HOWTO: Install the Netgear MA111 (v1) WLAN USB stick - Hoary (Warty)"
date: 2005-03-30
forum: Networking &amp; Wireless
---

### Post by smoeke on 2005-03-30
There are 2 possibilities:

I) Kernel 2.6.8.1-4 and 2.6.8.1-5 have a working prism2_usb kernel module for the MA111. Newer and older kernels have a version of prism2_usb which fails to start up the MA111. It might be tricky to install the new (or old kernels) without an internet connection, since the warty distribution on cd has the kernel 2.6.8.1-3. If you install the right kernels (-4, -5)  and reboot, there should be 'Wireless connection' shown in the 'Networking' - administration tool.

II) Use the ndiswrapper module. This is already included in the ubuntu distribution.

0) get the ndiswrapper utils with ```
sudo apt-get install ndiswrapper-utils
``` 
1) add the prism2_usb module to /etc/hotplug/blacklist so that it won't be loaded at startup
   ```
sudo gedit /etc/hotplug/blacklist
```
   just add a line containing 'prism2_usb' at the end of the file
2) download the Windows Netgear MA111 driver. The 2.5 beta driver is known to work well: [ftp://downloads.netgear.com/files/ma111_2_5beta.zip](ftp://downloads.netgear.com/files/ma111_2_5beta.zip)
3) unzip it somewhere with ```
unzip ma111_2_5beta.zip
```
4) enter the directory ```
cd MA111_2.5Beta/Drivers/WinXP/
```
5) install the driver with ```
sudo ndiswrapper -i NETMA111.INF
```
6) check if all is okay with ```
sudo ndiswrapper -l
```
7) load the ndiswrapper module with 'sudo modprobe ndiswrapper'
8) if you now start the 'Networking' administration tool, you should see an entry 'Wireless connection' (wlan0), change the properties according to your wlan settings and make it active.
9) if it works make the ndiswrapper stuff permanent with ```
sudo ndiswrapper -m
```
10) I also had to add a line to /etc/modules
   ```
sudo gedit /etc/modules
```
   add a line containing 'ndiswrapper' - the module is now loaded automatically at startup
11) for some reason I always have to make the connection active after a reboot in the 'Networking'-administration tool. If someone knows the answer I would appreciate it :)

HTH,
Werner

---

### Post by vrajmohan on 2005-04-14
Try adding the following to /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
        wireless_mode managed

--Vraj Mohan

---

### Post by smoeke on 2005-04-15
[QUOTE=vrajmohan]Try adding the following to /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
        wireless_mode managed

--Vraj Mohan[/QUOTE]

Thank you for the hint - I'll try it (after I reinstalled the Ubuntu distribution, since my harddisk crashed :( )

Regards,
Werner

---

### Post by luc1972 on 2005-08-26
Through lots of blood, sweat and tears (minaly tears) I got my Netgear MA111 recognised by my pc and working only for the keyboard to "freeze" shortly afterwards.  I remember seeing similar posts about this when trying to set it up, but can't find them now.  Anyone else had the same problem or know the solution?

---

### Post by luc1972 on 2005-09-02
[QUOTE=luc1972]Through lots of blood, sweat and tears (minaly tears) I got my Netgear MA111 recognised by my pc and working only for the keyboard to "freeze" shortly afterwards.  I remember seeing similar posts about this when trying to set it up, but can't find them now.  Anyone else had the same problem or know the solution?[/QUOTE]

Anyone? Please?

---

### Post by az on 2005-09-02
[QUOTE=luc1972]Anyone? Please?[/QUOTE]
I had that happen.  It drives you nuts!  The solution was to either try using a more recent version of ndiswrapper or changing hardware.

The thing worked flawlessly on some older hardware (200Mhz pentium or 400 MHz) but not on a 733 Mhz system!

---

### Post by Marko Vidberg on 2005-09-05
I have a laptop with no ethernet card, only a Netgear MA111.  These instructions are good if you can do "apt-get", but since I have no Internet in the first place, I can't use these instructions.  I do have another computer connected to the net and I can burn a CD with the required software.  Can somebody guide me as to what files I'd need to put on the CD to make my MA111 work?

---

### Post by Ninja Slayer on 2005-12-28
I followed the guide up to step 7 with no problems, but when I go to the Networking administration tool (step 8), the wireless connection is not listed there.  Any help would be greatly appreciated.

---

### Post by charims on 2006-01-09
same problem here, but i think its related to a usb issue, i am brand new to linux, but on the test-machine that i installed ubuntu on, my ma111 worked using this guide. My other machine, won't recognize usb like this one does. I noticed when i insert the usb stick, and get the ndiswrapper list, it says that the driver is installed, and the hardware is there. But when i put my memory stick in, the system doesnt recognize it, though on the test computer it did. Therefore, i think there isnt a correct driver installed for my usb.

Tell me what u think

Thanks,
Charims

---

### Post by Ninja Slayer on 2006-01-11
I actually think I found my problem.  Stupid mistake... very stupid.  I was using 5.04, not 4.10.

---

### Post by iainm2 on 2006-02-13
I have a Dell Latitude Cpt and installed the MA111 with no problems by following the above instructions. Thank you for a clear concise "how to". I always plug the MA111 in before starting the PC and have found that the wireless network is usually started automatically. Hope this gives encouragement to anyone else thinking of using this wireless solution as it is a cheap way to get wireless working. 
For info, I have a Netgear DG834G wireless router using MAC filtering and WEP.

---

### Post by jimonade on 2006-06-20
[QUOTE=luc1972]Through lots of blood, sweat and tears (minaly tears) I got my Netgear MA111 recognised by my pc and working only for the keyboard to "freeze" shortly afterwards.  I remember seeing similar posts about this when trying to set it up, but can't find them now.  Anyone else had the same problem or know the solution?[/QUOTE]

i am having the same problem with linux-wlan-ng with ma111 killing keyboard control and eventually crashing the system.

the problem also occurred (but less often) on gentoo.

on a fresh boot, connecting to my router through the ma111 has a 50/50 chance of causing this problem.

i've found relatively little info on this problem online.

any ideas?

---

### Post by maxnik on 2008-01-12
thank you for the HOWTO.
I was able to get my Netgear MA111v1 to work in Ubuntu 7.10 Gutsy.
There were couple things I did kinda differently.
1.I used Synaptics Package Manager to install **ndiswrapper**.
2.I blacklisted prism2_usb, but it was in /etc/modprobe.d folder

thank you.
i'll post if I remember anything eles.

---

