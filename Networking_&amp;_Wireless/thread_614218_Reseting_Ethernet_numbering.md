---
title: "Reseting Ethernet numbering?"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by blakegrover on 2007-11-15
Hi,

We are creating machines and sending out to different work locations and to install ubuntu we just copy a sata master hd to a blank hd and then send it on it's merry way.  Every now and then we have to make a change to the machines and we have to take a current hd that had the changes made to it and copy it over the master hd to make it the new master hd for new machines.  

We have one problem though.  Let's say the mast hd has the onboard wired nic card as eth0 and the wireless card as ath0.  After copying the hd to another and booting the new machine the kernel sees oh two different network cards and assigns them eth1 and ath1.  Not a big problem, but after doing this the numbers are getting bigger, we are at around eth7 and ath7 and we would like to know how to reset the numbering scheme and after rebooting the machine having the interfaces start back at 0.

If anyone knows how to do this I would appreciate your help.

Thanks
Blake

---

### Post by elctb on 2007-11-15
I'm not sure if this will do what you want, but take a look at the user space command "nameif".

---

### Post by blakegrover on 2007-11-16
I might do that but I would need to have the mac addresses setup in a file telling the machine what eth number they should be.  Is there any way just to erase all previous nic cards detected somewhere?

---

### Post by elctb on 2007-11-16
You can try this. It might do what you want. 

If you're using udev (you can find out by checking if udevd is running on your system), you can do the following:

. Add a new file to the udev rules (/etc/udev/rules.d/010_netinterfaces.rules)
. Edit 010_netinterfaces.rules and add the following rules:
  KERNEL==&#8221;eth*&#8221;, SYSFS{address}==&#8221;00:12:34:fe:dc:ba&#8221;, NAME=&#8221;eth0&#8243;
  KERNEL==&#8221;eth*&#8221;, SYSFS{address}==&#8221;00:56:78:98:76:54&#8243;, NAME=&#8221;eth1&#8243;

  Note that the hexadecimal digits in the MAC address should be in lowercase. Also, make sure you use your MAC address and the interface name you want. If there are more interfaces, you can add more rules.

. Change the interface names in the file /etc/network/interfaces to the new names.
. Reboot your computer and verify the interface names are what you want.

Don't forget to check the man page for udev.

---

