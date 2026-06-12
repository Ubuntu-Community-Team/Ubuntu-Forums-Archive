---
title: "Ez Connect g 802.11g Wireless usb adapter (smc2862W-g eu) module"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by stefanborremans on 2005-10-16
I'm using an SMC wirless dongle (smc2862W-g eu) and would like to have it working on Ubuntu 5.10.

Which modules do I need to load it?

---

### Post by unrealdark on 2005-12-29
no one?
:(

---

### Post by Bigglez on 2006-09-29
Sorry. I also have a USB SMC wireless waste of space. No drivers that I can find. :(

---

### Post by Narkolas on 2007-01-24
I'm runing on Ubuntu 6.10 with that usb adapter, using ndiswrapper.

This is how i made it work:

1. Get the driver. I got mine from SMC Networks: [http://www.smc.com]("http://www.smc.com/files/AE%5C2862wV.2_V.3DR_UT.zip")

2. Unpack the driver somwhere like in home dir.

3. Install ndiswrapper (use terminal or synaptic package manager), and the windows driver through NDISWrapper
**Im using the terminal:**
sudo apt-get install ndiswrapper-utils-1.8
cd /where_you_unpacked_the_driver/ (if there's subfolder for OS go there, i used the WinXp folder)
sudo ndiswrapper -i SMC2862W.inf (This should be the name of the Windows INF file in the folder)
sudo ndiswrapper -l (shows if the driver is installed) Mine looks like this "smc2862w driver installed, hardware present"
sudo modprobe ndiswrapper (this inserts the module in the kernel)
sudo ndiswrapper -m (this creates a default entry for ndiswrapper in /etc/modprobe.d/)

4. Get the Network Manager package (is use gnome)
sudo apt-get install network-manager-gnome

5. Reboot

If all went well you should now have an additional applet in the top bar that displays the a list of WLANS in the area, or you can select add one (if ssid is hidden)

Hope that helps :)
Have Fun

---

### Post by Bigglez on 2007-02-05
Hey Narkolas - thanks for the drive-by-assist :) I will try your suggestion next time I am in the Linux + laptop zone.

Ciao.

---

