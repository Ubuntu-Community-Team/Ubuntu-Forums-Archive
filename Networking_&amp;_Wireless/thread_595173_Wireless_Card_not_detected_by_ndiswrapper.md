---
title: "Wireless Card not detected by ndiswrapper"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Bigbird999 on 2007-10-28
I am a pretty stubborn guy,  total newb to LINUX, I am pretty sure that most would have packed it up and waited for another year or two for Ubuntu to get a bit more user friendly.  I am finding the  the learning curve to be absurdly steep:confused:, but I will persevere  because I am so stubborn.  

I have about 12 hours invested in getting my wireless card to work in gutsy.  I have followed the advice in about 6 different how to ndiswrapper threads.  I have finally got a driver installed that  gutysy recognizes, but I am stuck.

When I do a ndiswrapper -l command it tells me that the driver is installed, but it makes no mention of the hardware.  When I do a lshw -C network command, it recognizes my card, but there is no serial number (MAC address).  If I use the GUI and go to settings/administration/windows wireless drivers (can't remember exactly because I am in windoze now) it tell me that the driver is installed but there is no hardware present.

So how do I get it to detect the card so that I can finish the installation and configure the wireless connection.  My wired LAN worked out of the box, but If I can't get wireless running, my laptop is useless..\  Can somebody please point me in the right direction?

Thanks 

BB

---

### Post by infiniphonic on 2007-10-28
If you do indeed have Ndiswrapper and a valid windows driver installed try,

sudo modprobe ndiswrapper

to get it to activate.

Try,

Ndiswrapper -m to get it to start at boot time.

Hope this helps.

---

### Post by kevdog on 2007-10-28
Please post lshw -C network.  Seems like this output may be interesting.

---

### Post by Bigbird999 on 2007-10-28
Not sure how to do this but I saved the terminal as text and will paste it .  Doing this in windows so I saved the terminal session as a rtf doc in a shared partition and then opened it in windows and paste it here.  I know there must be a better way but I am not near a wired connection.  Anyway here is the session

ernie@LinuxLaptop:~$ lshw -C network

WARNING: you should run this program as super-user.

*-network UNCLAIMED     

       description: Ethernet controller

       product: 88w8335 [Libertas] 802.11b/g Wireless

       vendor: Marvell Technology Group Ltd.

       physical id: 0

       bus info: pci@0000:02:00.0

       version: 03

       width: 32 bits

       clock: 66MHz

       capabilities: cap_list

       configuration: latency=0

  *-network

       description: Ethernet interface

       physical id: 1

       logical name: eth0

       serial: 00:50:da:e3:cb:62

       capabilities: ethernet physical

       configuration: broadcast=yes driver=3c574_cs multicast=yes



ernie@LinuxLaptop:~$ ndiswrapper -v

utils version: 1.9

driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

version:        1.45

vermagic:       2.6.22-14-generic SMP mod_unload 586 



ernie@LinuxLaptop:~$ ndiswrapper -l

tnet1130 : driver installed

ernie@LinuxLaptop:~$ 





ernie@LinuxLaptop:~$ sudo modprobe ndiswrapper

[sudo] password for ernie:

ernie@LinuxLaptop:~$ Ndiswrapper -m

bash: Ndiswrapper: command not found

ernie@LinuxLaptop:~$ sudo ndiswrapper -m

module configuration already contains alias directive

Thanks in advance

BB

---

### Post by kevdog on 2007-10-28
Your getting an unclaimed, meaning a driver is not claiming the device.

*-network UNCLAIMED 

Do the modprobe statement as you did at the end of your post, then give the output of lshw -C network and lets see if ndiswrapper claimed the device.

Also see if the module actually loaded:
lsmod | grep ndis

---

### Post by Bigbird999 on 2007-10-29
When I installed Gutsy, I had the "no splash screen - slow boot issue that has plagued many.  I was able to fix it by following the steps in another thread.  That fixed the slow boot, then I tackled wireless and that got me here.  I can't find the thread now, but there was mention of the no splash fix breaking one user's wireless and the only way  he got it working again was to revert to the slow boot without a splash screen.    In addition, I was using the shotgun approach on this problem (Note to self, just change one thing at a time) and uninstalled network manager to install wicd, which didn't install properly,  so now I have neither.  I am going to do a fresh install and try to get wireless going before I fix the slow boot/splash issue.  I will post back when I complete this process.

Thanks for the help so far!

I'll be back!

BB

---

### Post by Bigbird999 on 2007-10-29
kevdog 
A fresh install without doing the no splash screen/slow boot fix and your network tutorial has got me going.  I haven't been able to get WPA configured but at least it is working in unsecured mode. 

[PHP]ernie@LinuxLaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 03
       serial: 00:18:e7:0f:fa:bc
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8335 driverversion=1.45+TRENDnet,08/22/2005,3.2.1.3 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:50:da:e3:cb:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=3c574_cs multicast=yes
ernie@LinuxLaptop:~$ lsmod | grep ndis
ndiswrapper           185240  0 
usbcore               138632  4 ndiswrapper,usbhid,uhci_hcd
[/PHP]
How do I connect without going through the whole command line thing the next time I log on?  Is it just going to automatically search and find an access point?  I am a terminalphobe and much prefer the GUI, I presume that there is some sort of GUI that does the same thing.

After I post this, I am going to log of and see what happens.  Later I will try the splash screen fix because it seems to me that everything, not just the boot, is slower than it was before.

Thanks

BB

---

### Post by Bigbird999 on 2007-10-29
OK booted in windows and then Gutsy.  Wireless connected automatically :) for both.  I don't like running unsecure wifi so I will have a go at getting it going before I maybe bust it fixing the slow boot.

More later


BB

---

### Post by kevdog on 2007-10-29
You need to install the wpasupplicant package to work with wpa.  Try then rebooting, and maybe with network manager it may work if you enable roaming mode.  wpa works no doubt, however sometimes its kind of buggy with nw manager.  I was using network manager for a long time, but then found wicd was a little bit more stable for me.  Others may find a different experience.

---

### Post by Bigbird999 on 2007-10-29
Installed wpa supplicant  but couldn't get it to connect by the terminal, Then when I rebooted I went to the nm applet (running beside the clock)  It saw my network and let me enter the pass phrase.  And I am connected with WPA:popcorn::guitar::).

Network manager is set as roaming enabled, when i unselect roaming, it gives me the opportunity to configure the connection and enter a passphrase.  I presume that the pasphrase in the wpasupplicant is being used and network manager should be kept in roaming mode.  But the passphrase I entered in the nm applet is what allowed me to connect.  Where does/did this mn applet come from?  Is it part of network manager or wpasupplicant or ????

Thanks for the help and the great tutorials.  I can't say I am comfortable but I am making progress a little at a time.

BB

---

### Post by kevdog on 2007-10-29
The applet is network manager -- 

If you select roaming mode, network manager is responsible for configuring network parameters.
If you do manual configuration, settings are stored or read in /etc/networking/interfaces.  This is useful if you want to set up static IP addresses or do other configurations

---

