---
title: "How to enable my wireless card in 7.10, It is supported and driver loaded properly."
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by laith43d on 2008-03-31
Hello,

I use an (Intel pro/wireless 3945) wireless card. There is neither icon for the interface in the network manager nor entry in the /etc/network/interfaces.

when I run this command in the command line (sudo lsmod | grep ipw3945) it shows this output:

> laith@laith-laptop:~$ sudo lsmod | grep ipw3945
ipw3945               119840  1 
ieee80211              35656  1 ipw3945


So the driver and the module for the wireless card are loaded properly.

Also when I run this command (lshw -C network) it shows this output:

> laith@laith-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:3a:39:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=212.6.39.106 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes


As you can see there is no entry for a Logical name in the wireless card.

Also when I run this (iwconfig) it gives:

> laith@laith-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.



I've installed network selector package, and it shows me wireless disabled (a picture is attached).

Now what to do ?? Please help

thanx

---

### Post by laith43d on 2008-03-31
Please I am  in a trouble please help me as fast as you can !!!

thanx

---

### Post by lswest on 2008-03-31
looks to me like your wireless card isn't being assigned a logical name at boot-up.  (e.g. eth0, etc).  To do so you'd need to write a UDEV rule that specifies the name, the PCI bus (or MAC).  I'll post back in a minute or two with a basic UDEV rule which should accomplish the task.

okay, back.

Do this:
```
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.rules.backup
``` to back up the file (in case something goes wrong, restore it by doing the opposite, .rules.backup first, then .rules)
then open it with:
```
gksudo gedit /etc/udev/rules.d/70-persistent-net.rules
```
there you should get a text editor with the file.  at the end of the file make a comment, something like #wireless (name of the driver)
then add this:
> SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ID="0000:06:00.0", IMPORT="/sbin/rename_netiface %k eth1"

this will then add a rule which takes the PCI ID of your card (since there seems to be no mac address identified) and call the device "eth1"

Once you reboot the card should be there, as eth1.  If not, or if there are errors, just run ```
sudo cp /etc/udev/rules.d/70-persistent-net.rules.backup /etc/udev/rules.d/70-persistent-net.rules
``` to restore the file, and then rebooting should put you back to where you are now.  If this doesn't work, i'm not entirely sure what else you could do

as a last note: if the file that is opened is empty, and if you try to close it and it asks you to save, then the filename is wrong, and you will have to figure out what the name of the file is by doing ```
cd /etc/udev/rules.d/
ls
```
and choosing the file that is called [numbers]-persistent-net.rules

---

### Post by kevdog on 2008-03-31
Type dmesg and check for any errors associated with loading the driver and attempting association with your card.

---

### Post by lswest on 2008-03-31
That was my first reaction too Kevdog, but if you look at the output of lshw -C network, there is no MAC address or logical name listed for his wireless card, so i assume there is a missing UDEV rule, or an unrecognizable mac address.

---

### Post by kevdog on 2008-03-31
Yes but dmesg should tell you this if this is truly the case -- its just an error log.  Anything relevant associated with your card?

---

### Post by laith43d on 2008-04-01
Hello,
Thanks for your attention. 

At last I found the problem, it was a hardware issue, In fact I did not enable my wlan from the little button on my labtop. It was shutdown.

thanks..

---

