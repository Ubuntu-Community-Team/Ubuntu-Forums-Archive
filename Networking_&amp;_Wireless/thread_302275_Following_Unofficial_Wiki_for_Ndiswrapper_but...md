---
title: "Following Unofficial Wiki for Ndiswrapper but.."
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by Recked on 2006-11-18
just below is the output from my attempts to get my Netgear WPN511 cardbus nic to work with Edgy. 

Are there any wireless experts out there that can explain to this feeble brain what the issue is exactly?

thanks a lot

dlaptop@dlaptop:~$ lsmod | grep acx
dlaptop@dlaptop:~$ sudo rmmod acx
Password:
ERROR: Module acx does not exist in /proc/modules
dlaptop@dlaptop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-bin libcairo-ruby libgtk1.2 libatk1-ruby libgnome32 gnome-libs-data
  libglib2-ruby libart2 libgnorbagtk0 libpango1-ruby gdk-imlib1 pump ruby1.8
  libgdk-pixbuf2-ruby ruby libgnomeui32 libdb3 libcairo-ruby1.8
  libgtk1.2-common imlib-base xsu liborbit0 gdk-imlib11 libgnomesupport0
  libgtk2-ruby libzvt2 libruby1.8 libgnorba27
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.1
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/47.4kB of archives.
After unpacking 250kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 93693 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.18-1ubuntu2_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.1.
Unpacking ndiswrapper-utils-1.1 (from .../ndiswrapper-utils-1.1_1.1-5_i386.deb) ...
Selecting previously deselected package ndiswrapper-utils.
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.1-5_all.deb) ...
Setting up ndiswrapper-common (1.18-1ubuntu2) ...
Setting up ndiswrapper-utils-1.1 (1.1-5) ...

Setting up ndiswrapper-utils (1.1-5) ...
dlaptop@dlaptop:~$ sudo ndiswrapper -i /dlaptop/netpn511.infInstalling netpn511
cp: cannot stat `/dlaptop/netpn511.inf': No such file or directory
dlaptop@dlaptop:~$ sudo ndiswrapper -i /home/netpn511.inf
netpn511 is already installed. Use -e to remove it
dlaptop@dlaptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
netpn511        invalid driver!
dlaptop@dlaptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
netpn511        invalid driver!
dlaptop@dlaptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
dlaptop@dlaptop:~$

---

### Post by cantormath on 2006-11-18
honestly, you are better off using another card....
Ndiswrapper sucks
you might want to try using automatix2 to install ndiswrapper.

---

### Post by Recked on 2006-11-18
The thing is that when I installed Edgy from the Alternate cd the Netgear nic worked just fine. I didn't even use my wired network and at least during the installation the wireless nic worked without problem. It came up asking me if wanted to use wired, the built in Intel wireless or the Netgear (listed as Atheros during install). I picked Atheros and everything was fine until I booted into the newly installed system then then both green lights stopped flashing as they had and now I can't seem to get it to work.

I'll keep plugging away

thanks

---

### Post by Recked on 2006-11-18
Got the card working with both lights now flashing thanks for your help Cantormath....

now if only i could connect to my wireless network!!!

](*,) ](*,) 

WPAsupplicant is installed so I will try now from this point

---

### Post by cantormath on 2006-11-18
fantastic.....

---

### Post by Recked on 2006-11-18
Everything is working now EXCEPT each time I reboot/shutdown ndiswrapper does not appear to "remember" the nic card. When I open ndiswrapper after a reboot etc. it says the card is there, but only one light is flashing and there is no internet connectivity. I have to delete the .inf file and reinstall it and as soon as I do I am able to log into my network wirelessly.

Any suggestions?

thanks

---

