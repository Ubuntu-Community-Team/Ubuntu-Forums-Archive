---
title: "Wireless internet - can't find any networks"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by evillan on 2008-08-26
I've been using ubuntu for some time now, but I never got around to play with the wireless internet until now. 

I understand a list of the available wireless networks should pop up when I click the network-admin icon, right?

This is what it looks like for me
[IMG]http://img504.imageshack.us/my.php?image=wire2no7.png[/IMG]

I clicked the icon with the two connected computers (to the outer left).

Then I unlocked and went through "Properties", still no result though.

What should I do?

---

### Post by tangibleorange on 2008-08-26
hello. what wireless card do you have? when you click the network icon on the top panel, is the 'enable wireless' box checked?
could you also post the output of:

```
lshw -C network
```

---

### Post by evillan on 2008-08-26
> **tangibleorange said:**
> hello. what wireless card do you have? when you click the network icon on the top panel, is the 'enable wireless' box checked?
could you also post the output of:

```
lshw -C network
```

I'm not sure what you mean by the first question. Here's a screen shot:
[IMG]http://img179.imageshack.us/my.php?image=wire3da0.png[/IMG]

And here's the output of 
> 
xxx:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:b7:f6:67
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:1f:68:b8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.2.101 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes


As you can see, I have a PRO/Wireless 3945ABG Network Connection card. I should work out-of-the-box.

---

### Post by Blackcabs on 2008-08-26
> **tangibleorange said:**
> hello. what wireless card do you have? when you click the network icon on the top panel, is the 'enable wireless' box checked?
could you also post the output of:

```
lshw -C network
```

What evillan means is,, RIGHT CLICK on the 2tv's icon and it will show you 2 options for networking. One is for wired network & the other is for wireless network, make sure the wireless option is ticked then you should see some networks

Hope this helps :)

---

### Post by evillan on 2008-08-27
> **Blackcabs said:**
> What evillan means is,, RIGHT CLICK on the 2tv's icon and it will show you 2 options for networking. One is for wired network & the other is for wireless network, make sure the wireless option is ticked then you should see some networks

Hope this helps :)



The hosting site is down, here are the screen shots again

[IMG]http://img504.imageshack.us/my.php?image=wire2no7.png[/IMG]

[IMG]http://img179.imageshack.us/my.php?image=wire3da0.png[/IMG]

If I right-click the two-connected-computers icon, a menu with the following options appear
> 
Launch
Properties
Remove from panel
Move
Lock to panel

---

### Post by tangibleorange on 2008-08-27
ah ok i think you are using a different network icon to the one i'm thinking of. what happens if you open up a terminal and type:

```
nm-applet
```
because a new icon should appear and then you should be able to right-click on that and see the options we're talking about.

BTW, I still can't see the screenshots...

---

### Post by evillan on 2008-08-27
nm-applet is not on my system. (Nothing happens when I write "nm-applet" or "sudo nm-applet", and I can't find the program in aptitude).

Here's some urls to the screen shots. They're hopefully working now!

[http://img179.imageshack.us/my.php?image=wire3da0.png]("http://img179.imageshack.us/my.php?image=wire3da0.png")

[http://img504.imageshack.us/my.php?image=wire2no7.png]("http://img504.imageshack.us/my.php?image=wire2no7.png")

---

### Post by tangibleorange on 2008-08-27
ok. i can see them now. that's odd - nm-applet should be installed by default - did you remove it manually?

what version of ubuntu are you running? if you're not sure, this command should tell you:

```
lsb_release -a
```

---

### Post by evillan on 2008-08-27
I use ubuntu 8.04.

I don't think I deleted the nm-applet, but it is obviously not there, so *something* went wrong. Is there any way to reinstall it?

---

### Post by tangibleorange on 2008-08-27
> **evillan said:**
> I use ubuntu 8.04.

I don't think I deleted the nm-applet, but it is obviously not there, so *something* went wrong. Is there any way to reinstall it?

yeah it's very easy to reinstall. simply go to a terminal and type:
```
sudo apt-get install network-manager network-manager-gnome
```

and then press Alt+F2 to get a command box, and then type 'nm-applet' (no quotes). this should make the applet appear. you can then play around with the settings of that. make sure roaming mode is turned off in the other network settings window (the one you posted a screenshot of) before you boot up the applet.

also, while you're at the terminal, could you post the output of:

```
cat /etc/network/interfaces
```

---

### Post by evillan on 2008-08-27
Ok, so I reinstalled the network-manager(-gnome), but nothing happens when I type nm-applet (not in Alt+F2 nor bash). The programs are installed according to aptitude.

The output of ```

xxx:~$cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp

```

---

### Post by Blackcabs on 2008-08-27
[B]If I right-click the two-connected-computers icon, a menu with the following options appear
Quote:
Launch
Properties
Remove from panel
Move
Lock to panel [/B]


I dont mean to state the obvious but did you try clicking on LAUNCH

---

### Post by evillan on 2008-08-28
> **Blackcabs said:**
> [B]If I right-click the two-connected-computers icon, a menu with the following options appear
Quote:
Launch
Properties
Remove from panel
Move
Lock to panel [/B]


I dont mean to state the obvious but did you try clicking on LAUNCH

I have tried that and posted a screen shot (linked to it before):[IMG]http://img179.imageshack.us/img179/8071/wire3da0.png[/IMG]

Also, the output of 
> 
xxx:~$ iwlist  scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results


---

### Post by tangibleorange on 2008-08-28
ok if you go to the restricted drivers manager (System -> Administration -> Hardware Drivers), is there a driver enabled for your card?

i don't understand why network-manager doesn't work... you're sure both network-manager and network-manager-gnome are installed? (check in Synaptic Package Manager).

---

### Post by Blackcabs on 2008-08-28
> **tangibleorange said:**
> ok if you go to the restricted drivers manager (System -> Administration -> Hardware Drivers), is there a driver enabled for your card?

i don't understand why network-manager doesn't work... you're sure both network-manager and network-manager-gnome are installed? (check in Synaptic Package Manager).

I think tangibleorange is pointing you in the right direction, but if you cant find your driver in the list you should open a terminal and type

modprobe ipw3945 this should load the correct module for your card,, to double check that it has loaded type 

sudo lsmod  and scroll down the list looking for ipw3945

---

### Post by tangibleorange on 2008-08-28
yeah a version of the lsmod command that will list only the relevant parts:

```
lsmod | grep ipw3945
```

---

### Post by evillan on 2008-08-28
I think you've found the problem:

> 
xxx:~$ modprobe ipw3945
FATAL: Module ipw3945 not found.
sh: /sbin/ipw3945d-2.6.24-19-generic: not found
FATAL: Error running install command for ipw3945


And in System->Administration->Hardware driver:
> No proprietary drivers are in use on this system. 

And "lsmod | grep ipw3945" doesn't output anything.

So, how do I install the driver?

---

### Post by Blackcabs on 2008-08-28
> **evillan said:**
> I think you've found the problem:



And in System->Administration->Hardware driver:


And "lsmod | grep ipw3945" doesn't output anything.

So, how do I install the driver?

Very good question,, there are  2 drivers that you can chose from. The ipw3945 driver should have come preinstalled,,the second driver is called iwl3945 go to this link [http://www.linuxwireless.org/en/users/Download](http://www.linuxwireless.org/en/users/Download) and there is loads of information on what to do.This is the driver that i use on my laptop which has the same card as yours.I wish i could say that its as easy as "apt-get" but i dont think it is. I will have a deeper look into how you can get the driver that should already have been there ?.and get back to you, in the mean time have a look at the site

---

### Post by Blackcabs on 2008-08-28
Ok evillan lets try this.. open system/admin/synaptic-packet-manager click on search and type [linux-restricted-modules-2.6.24-19-generic] and look to see if these modules are installed,, if they are the check box will be coloured green, if not it will be clear, and hopfully this will be the case...Even if it is coloured right click on the check box and chose the reinstallation option. let me know how you get on and if so we can go another route.But im pretty sure this will sort your probs

---

### Post by evillan on 2008-08-29
So I installed it:


```

xxx:~$ aptitude show linux-restricted-modules-2.6.24-19-generic 
Package: linux-restricted-modules-2.6.24-19-generic
New: yes
State: installed
Automatically installed: yes
Version: 2.6.24.13-19.45
Priority: optional
Section: restricted/misc
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 48,8M
Depends: linux-image-2.6.24-19-generic, linux-restricted-modules-common (>= 2.6.24), module-init-tools, nvidia-kernel-common
Suggests: avm-fritz-firmware-2.6.24-19, nvidia-glx | nvidia-glx-legacy | nvidia-glx-new
Provides: nvidia-kernel-169.12, nvidia-kernel-71.86.04, nvidia-kernel-96.43.05
Description: Non-free Linux 2.6.24 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.24 on x86/x86_64. 
 
 Currently the following modules are included: 
 * madwifi (Atheros) 
 * fglrx (ATI) 
 * nvidia 
 * fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN) 
 * fcdsl, fcdslusba, fcusb, fwlanusb, fxusb (AVM ISDN x86 only) 
   
 These modules are "restricted" because they are not available under a completely Free licence.

```

But when I "modprobe ipw3945":
```

xxx:~$ modprobe ipw3945
FATAL: Module ipw3945 not found.
sh: /sbin/ipw3945d-2.6.24-19-generic: not found
FATAL: Error running install command for ipw3945

```

And 
```
xxx:~$  ls /sbin/ipw*
/sbin/ipw3945d-2.6.20-15-generic  /sbin/ipw3945d-2.6.20-16-generic  /sbin/ipw3945d-2.6.22-14-generic

```

I tried to restart my computer - still not working.

---

### Post by Blackcabs on 2008-08-29
> **evillan said:**
> So I installed it:


```

xxx:~$ aptitude show linux-restricted-modules-2.6.24-19-generic 
Package: linux-restricted-modules-2.6.24-19-generic
New: yes
State: installed
Automatically installed: yes
Version: 2.6.24.13-19.45
Priority: optional
Section: restricted/misc
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 48,8M
Depends: linux-image-2.6.24-19-generic, linux-restricted-modules-common (>= 2.6.24), module-init-tools, nvidia-kernel-common
Suggests: avm-fritz-firmware-2.6.24-19, nvidia-glx | nvidia-glx-legacy | nvidia-glx-new
Provides: nvidia-kernel-169.12, nvidia-kernel-71.86.04, nvidia-kernel-96.43.05
Description: Non-free Linux 2.6.24 modules on x86/x86_64
 This package provides restricted modules for Linux version 2.6.24 on x86/x86_64. 
 
 Currently the following modules are included: 
 * madwifi (Atheros) 
 * fglrx (ATI) 
 * nvidia 
 * fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN) 
 * fcdsl, fcdslusba, fcusb, fwlanusb, fxusb (AVM ISDN x86 only) 
   
 These modules are "restricted" because they are not available under a completely Free licence.

```

But when I "modprobe ipw3945":
```

xxx:~$ modprobe ipw3945
FATAL: Module ipw3945 not found.
sh: /sbin/ipw3945d-2.6.24-19-generic: not found
FATAL: Error running install command for ipw3945

```

And 
```
xxx:~$  ls /sbin/ipw*
/sbin/ipw3945d-2.6.20-15-generic  /sbin/ipw3945d-2.6.20-16-generic  /sbin/ipw3945d-2.6.22-14-generic

```

I tried to restart my computer - still not working.

Ok dont worrie.. looking through your output there,, can you tell me exactly what kernal you are running,, it tells you when you start your machine, because you need to running at least 2.6.24-16 for these modules to be supported, and preferably 2.6.24-19. Or open synaptic again and search linux-image-2.6.24-19-generic

---

### Post by Blackcabs on 2008-08-29
Ok evillan i've had a look and the modules that you need are definately included in the above packages, so you must be running an older version of the kernal, if this is not the case then we can can download the driver directly and install it.I have all the links and will walk you through it, i understand that this is a bit of a headache, but dont stress "We can do this".
Thanks Paul

---

### Post by tangibleorange on 2008-08-29
use:

```
uname -r
```

to determine your kernel version. you can also use this command:
```

sudo aptitude install linux-restricted-modules-`uname -r`
```
to install the correct package for your kernel.

---

### Post by Blackcabs on 2008-08-29
you beat me to it tangibleorange i was just about to edit my last post.. Thanks for helping with this, i think evillan is running an older kernal,, what do you think

---

### Post by tangibleorange on 2008-08-29
> **Blackcabs said:**
> you beat me to it tangibleorange i was just about to edit my last post.. Thanks for helping with this, i think evillan is running an older kernal,, what do you think

hehe. it look like it but i've no idea about the actual modules contained in the linux-restricted-modules package - if he's running hardy, he shouldn't have a kernel of earlier than 2.6.24-16, and the ipw driver should appear in the Restricted Drivers Manager... Hopefully the commands might shed some light on it :)

---

### Post by Blackcabs on 2008-08-29
I know what you are saying " but something is missing" i have asked for conformaton on what modules are definatly inclued in the above packages. I mean there on my machine so why aren't they on his ???? When you look at code that was thrown out it its referring to 2.6.20-15

---

### Post by evillan on 2008-08-30
> **tangibleorange said:**
> use:

```
uname -r
```

to determine your kernel version. you can also use this command:
```

sudo aptitude install linux-restricted-modules-`uname -r`
```
to install the correct package for your kernel.

I use ubuntu 8.04, so
```

xxx:~$ uname -r
2.6.24-19-generic

```


and
```

xxx:~$ sudo aptitude install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done    
```
... since I already installed it.

---

### Post by tangibleorange on 2008-08-30
try the ipw3945d module:

```
sudo modprobe ipw3945d
```

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Blackcabs on 2008-08-30
Ok evillan lets just install it directly,,Follow these commands

1 /lib/modules/`uname -r`/build
2 [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)  dont use wget as it wont work Hot links are removed

3 Unpack with archive manager somewhere in your home folder but not important or use tar jxvf compat-wireless-$(date -I).tar.bz2

4 cd into the same directory that you unpacked to and dont forget the date that has now been added to the end IE ""home/compat-wireless-$ 2008-08-31""

5 then type make
6 then type sudo make install
7 then type sudo make unload
8 then type sudo make load 
9 then type sudo modprobe iwl3945
10 then type sudo depmod -ae
 Follow all of this and then reboot and you should be good to go :-\"

Let us know how you got on,This is were the drivers should reside on your system /lib/modules/2.6.24-19-generic/ubuntu/wireless .if you cant find this directory at all then look in synaptic again for linux-Ubuntu-modules-2.6.24-19-generic to see first.

---

### Post by evillan on 2008-08-31
> **tangibleorange said:**
> try the ipw3945d module:

```
sudo modprobe ipw3945d
```

Nope:
```
xxx:~$ sudo modprobe ipw3945d
FATAL: Module ipw3945d not found.

```

---

### Post by evillan on 2008-08-31
> **Blackcabs said:**
> Ok evillan lets just install it directly,,Follow these commands

1 /lib/modules/`uname -r`/build
2 [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)  dont use wget as it wont work Hot links are removed

3 Unpack with archive manager somewhere in your home folder but not important or use tar jxvf compat-wireless-$(date -I).tar.bz2

4 cd into the same directory that you unpacked to and dont forget the date that has now been added to the end IE ""home/compat-wireless-$ 2008-08-31""

5 then type make
6 then type sudo make install
7 then type sudo make unload
8 then type sudo make load 
9 then type sudo modprobe iwl3945
10 then type sudo depmod -ae
 Follow all of this and then reboot and you should be good to go :-\"

Let us know how you got on,This is were the drivers should reside on your system /lib/modules/2.6.24-19-generic/ubuntu/wireless

Ok, so I followed your instructions and everything appeared to work fine until
```
xxx$ sudo modprobe iwl3945
WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

This is the output of dmesg:```
[ 2028.393174] rt2400pci: Unknown symbol rt2x00pci_suspend
[ 2028.393227] rt2400pci: Unknown symbol rt2x00mac_config_interface
[ 2028.393279] rt2400pci: Unknown symbol rt2x00pci_remove
[ 2028.393331] rt2400pci: Unknown symbol rt2x00mac_remove_interface
[ 2028.393383] rt2400pci: Unknown symbol rt2x00mac_config
[ 2028.393435] rt2400pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.393488] rt2400pci: Unknown symbol rt2x00queue_get_queue
[ 2028.393540] rt2400pci: Unknown symbol rt2x00mac_conf_tx
[ 2028.393623] rt2400pci: Unknown symbol rt2x00mac_start
[ 2028.393674] rt2400pci: Unknown symbol rt2x00pci_txdone
[ 2028.393727] rt2400pci: Unknown symbol rt2x00mac_stop
[ 2028.393781] rt2400pci: Unknown symbol rt2x00mac_configure_filter
[ 2028.393833] rt2400pci: Unknown symbol rt2x00mac_tx
[ 2028.393885] rt2400pci: Unknown symbol rt2x00pci_resume
[ 2028.393951] rt2400pci: Unknown symbol rt2x00pci_probe
[ 2028.394003] rt2400pci: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.394079] rt2400pci: Unknown symbol rt2x00pci_rxdone
[ 2028.394131] rt2400pci: Unknown symbol rt2x00lib_beacondone
[ 2028.394186] rt2400pci: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.394238] rt2400pci: Unknown symbol rt2x00pci_write_tx_data
[ 2028.415214] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.415221] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.415225] Pid: 19700, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.415235]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.415255]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.415265]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.415270]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.415277]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.415284]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.415292]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.415298]  [<c028374f>] class_register+0x9f/0x140
[ 2028.415309]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.415318]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.415357]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.415374]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.415393]  =======================
[ 2028.415398] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.415404] Pid: 19700, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.415409]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.415417]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.415426]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.415433]  [<c028374f>] class_register+0x9f/0x140
[ 2028.415444]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.415453]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.415488]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.415504]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.415521]  =======================
[ 2028.430546] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.430685] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.431164] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.431268] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.431496] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.431953] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.432112] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.432482] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.432608] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.433859] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.433963] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.434016] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.434071] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.434124] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.434210] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.434356] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.434431] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.434487] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.434538] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.434642] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.434851] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.435415] rt2x00pci: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.435468] rt2x00pci: Unknown symbol rt2x00lib_suspend
[ 2028.435521] rt2x00pci: Unknown symbol rt2x00lib_probe_dev
[ 2028.435589] rt2x00pci: Unknown symbol rt2x_ieee80211_get_hdrlen
[ 2028.435700] rt2x00pci: Unknown symbol rt2x00lib_rxdone
[ 2028.435752] rt2x00pci: Unknown symbol rt2x00queue_get_entry
[ 2028.435825] rt2x00pci: Unknown symbol rt2x00lib_remove_dev
[ 2028.435915] rt2x00pci: Unknown symbol rt2x00lib_txdone
[ 2028.435969] rt2x00pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.436069] rt2x00pci: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.436137] rt2x00pci: Unknown symbol rt2x00lib_resume
[ 2028.436188] rt2x00pci: Unknown symbol rt2x00queue_index_inc
[ 2028.436261] rt2x00pci: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.436784] rt2500pci: Unknown symbol rt2x00mac_add_interface
[ 2028.436837] rt2500pci: Unknown symbol rt2x00mac_get_stats
[ 2028.436905] rt2500pci: Unknown symbol rt2x00pci_initialize
[ 2028.436973] rt2500pci: Unknown symbol rt2x00pci_uninitialize
[ 2028.437025] rt2500pci: Unknown symbol rt2x00queue_get_entry
[ 2028.437078] rt2500pci: Unknown symbol rt2x00pci_suspend
[ 2028.437130] rt2500pci: Unknown symbol rt2x00mac_config_interface
[ 2028.437182] rt2500pci: Unknown symbol rt2x00pci_remove
[ 2028.437234] rt2500pci: Unknown symbol rt2x00mac_remove_interface
[ 2028.437287] rt2500pci: Unknown symbol rt2x00mac_config
[ 2028.437339] rt2500pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.437391] rt2500pci: Unknown symbol rt2x00queue_get_queue
[ 2028.437443] rt2500pci: Unknown symbol rt2x00mac_conf_tx
[ 2028.437527] rt2500pci: Unknown symbol rt2x00mac_start
[ 2028.437579] rt2500pci: Unknown symbol rt2x00pci_txdone
[ 2028.437638] rt2500pci: Unknown symbol rt2x00mac_stop
[ 2028.437712] rt2500pci: Unknown symbol rt2x00mac_configure_filter
[ 2028.437764] rt2500pci: Unknown symbol rt2x00mac_tx
[ 2028.437816] rt2500pci: Unknown symbol rt2x00pci_resume
[ 2028.437882] rt2500pci: Unknown symbol rt2x00pci_probe
[ 2028.437934] rt2500pci: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.438003] rt2500pci: Unknown symbol rt2x00pci_rxdone
[ 2028.438056] rt2500pci: Unknown symbol rt2x00lib_beacondone
[ 2028.438111] rt2500pci: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.438163] rt2500pci: Unknown symbol rt2x00pci_write_tx_data
[ 2028.467685] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.467695] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.467699] Pid: 19707, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.467726]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.467748]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.467764]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.467772]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.467780]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.467788]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.467798]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.467807]  [<c028374f>] class_register+0x9f/0x140
[ 2028.467822]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.467834]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.467880]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.467901]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.467923]  =======================
[ 2028.467928] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.467934] Pid: 19707, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.467941]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.467951]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.467961]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.467969]  [<c028374f>] class_register+0x9f/0x140
[ 2028.467982]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.467992]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.468029]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.468046]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.468064]  =======================
[ 2028.474347] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.474480] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.474959] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.475062] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.475290] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.475746] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.475895] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.476264] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.476390] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.477284] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.477387] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.477440] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.477496] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.477549] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.477644] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.477790] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.477864] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.477922] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.477974] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.478079] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.478288] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.478969] rt2x00pci: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.479023] rt2x00pci: Unknown symbol rt2x00lib_suspend
[ 2028.479075] rt2x00pci: Unknown symbol rt2x00lib_probe_dev
[ 2028.479144] rt2x00pci: Unknown symbol rt2x_ieee80211_get_hdrlen
[ 2028.479255] rt2x00pci: Unknown symbol rt2x00lib_rxdone
[ 2028.479308] rt2x00pci: Unknown symbol rt2x00queue_get_entry
[ 2028.479380] rt2x00pci: Unknown symbol rt2x00lib_remove_dev
[ 2028.479470] rt2x00pci: Unknown symbol rt2x00lib_txdone
[ 2028.479524] rt2x00pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.479624] rt2x00pci: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.479692] rt2x00pci: Unknown symbol rt2x00lib_resume
[ 2028.479744] rt2x00pci: Unknown symbol rt2x00queue_index_inc
[ 2028.479817] rt2x00pci: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.481947] rt61pci: Unknown symbol rt2x00mac_add_interface
[ 2028.482035] rt61pci: Unknown symbol rt2x00mac_get_stats
[ 2028.482103] rt61pci: Unknown symbol rt2x00pci_initialize
[ 2028.482231] rt61pci: Unknown symbol rt2x00pci_uninitialize
[ 2028.482284] rt61pci: Unknown symbol rt2x00queue_get_entry
[ 2028.482351] rt61pci: Unknown symbol rt2x00pci_suspend
[ 2028.482403] rt61pci: Unknown symbol rt2x00mac_config_interface
[ 2028.482456] rt61pci: Unknown symbol rt2x00pci_remove
[ 2028.482508] rt61pci: Unknown symbol rt2x00mac_remove_interface
[ 2028.482560] rt61pci: Unknown symbol rt2x00mac_config
[ 2028.482613] rt61pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.482666] rt61pci: Unknown symbol rt2x00queue_get_queue
[ 2028.482718] rt61pci: Unknown symbol rt2x00mac_conf_tx
[ 2028.482802] rt61pci: Unknown symbol rt2x00mac_start
[ 2028.482855] rt61pci: Unknown symbol rt2x00pci_txdone
[ 2028.482906] rt61pci: Unknown symbol rt2x00mac_stop
[ 2028.482961] rt61pci: Unknown symbol rt2x00mac_configure_filter
[ 2028.483014] rt61pci: Unknown symbol rt2x00mac_tx
[ 2028.483066] rt61pci: Unknown symbol rt2x00pci_resume
[ 2028.483132] rt61pci: Unknown symbol rt2x00pci_probe
[ 2028.483184] rt61pci: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.483285] rt61pci: Unknown symbol rt2x00pci_rxdone
[ 2028.483340] rt61pci: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.483392] rt61pci: Unknown symbol rt2x00pci_write_tx_data
[ 2028.502845] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.502851] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.502856] Pid: 19717, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.502867]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.502888]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.502899]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.502905]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.502912]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.502918]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.502926]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.502931]  [<c028374f>] class_register+0x9f/0x140
[ 2028.502943]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.502950]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.502987]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.503002]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.503019]  =======================
[ 2028.503022] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.503027] Pid: 19717, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.503031]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.503037]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.503044]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.503049]  [<c028374f>] class_register+0x9f/0x140
[ 2028.503058]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.503065]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.503098]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.503111]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.503126]  =======================
[ 2028.516815] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.516951] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.517434] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.517537] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.517769] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.518229] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.518384] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.518765] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.518894] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.519883] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.519998] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.520052] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.520108] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.520160] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.520247] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.520393] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.520467] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.520524] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.520576] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.520681] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.520891] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.521606] rt2x00usb: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.521659] rt2x00usb: Unknown symbol rt2x00lib_suspend
[ 2028.521712] rt2x00usb: Unknown symbol rt2x00lib_probe_dev
[ 2028.521919] rt2x00usb: Unknown symbol rt2x00lib_rxdone
[ 2028.521972] rt2x00usb: Unknown symbol rt2x00queue_get_entry
[ 2028.522147] rt2x00usb: Unknown symbol rt2x00lib_remove_dev
[ 2028.522220] rt2x00usb: Unknown symbol rt2x00lib_txdone
[ 2028.522272] rt2x00usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.522382] rt2x00usb: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.522438] rt2x00usb: Unknown symbol rt2x00lib_resume
[ 2028.522539] rt2x00usb: Unknown symbol rt2x00queue_index_inc
[ 2028.522592] rt2x00usb: Unknown symbol rt2x_ieee80211_get_hdrlen_from_skb
[ 2028.522670] rt2x00usb: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.523222] rt2500usb: Unknown symbol rt2x00mac_add_interface
[ 2028.523276] rt2500usb: Unknown symbol rt2x00mac_get_stats
[ 2028.523329] rt2500usb: Unknown symbol rt2x00usb_init_rxentry
[ 2028.523432] rt2500usb: Unknown symbol rt2x00usb_disable_radio
[ 2028.523484] rt2500usb: Unknown symbol rt2x00usb_init_txentry
[ 2028.523537] rt2500usb: Unknown symbol rt2x00usb_vendor_request_buff
[ 2028.523678] rt2500usb: Unknown symbol rt2x00usb_write_tx_data
[ 2028.523730] rt2500usb: Unknown symbol rt2x00mac_config_interface
[ 2028.523783] rt2500usb: Unknown symbol rt2x00mac_remove_interface
[ 2028.523835] rt2500usb: Unknown symbol rt2x00usb_vendor_request
[ 2028.523888] rt2500usb: Unknown symbol rt2x00usb_probe
[ 2028.523954] rt2500usb: Unknown symbol rt2x00mac_config
[ 2028.524006] rt2500usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.524063] rt2500usb: Unknown symbol rt2x00usb_suspend
[ 2028.524115] rt2500usb: Unknown symbol rt2x00mac_conf_tx
[ 2028.524167] rt2500usb: Unknown symbol rt2x00mac_start
[ 2028.524220] rt2500usb: Unknown symbol rt2x00mac_stop
[ 2028.524325] rt2500usb: Unknown symbol rt2x00mac_configure_filter
[ 2028.524377] rt2500usb: Unknown symbol rt2x00usb_disconnect
[ 2028.524430] rt2500usb: Unknown symbol rt2x00mac_tx
[ 2028.524499] rt2500usb: Unknown symbol rt2x00usb_vendor_req_buff_lock
[ 2028.524551] rt2500usb: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.524621] rt2500usb: Unknown symbol rt2x00usb_resume
[ 2028.524673] rt2500usb: Unknown symbol rt2x00usb_uninitialize
[ 2028.524726] rt2500usb: Unknown symbol rt2x00usb_initialize
[ 2028.524781] rt2500usb: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.544569] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.544575] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.544579] Pid: 19724, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.544592]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.544608]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.544619]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.544624]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.544631]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.544638]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.544646]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.544652]  [<c028374f>] class_register+0x9f/0x140
[ 2028.544664]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.544672]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.544711]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.544727]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.544745]  =======================
[ 2028.544748] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.544753] Pid: 19724, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.544757]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.544764]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.544772]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.544778]  [<c028374f>] class_register+0x9f/0x140
[ 2028.544788]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.544794]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.544828]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.544842]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.544856]  =======================
[ 2028.554636] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.554768] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.555245] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.555349] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.555577] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.556034] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.556182] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.556551] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.556677] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.557584] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.557687] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.557740] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.557795] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.557848] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.557934] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.558080] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.558155] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.558212] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.558265] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.558370] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.558579] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.559179] rt2x00usb: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.559233] rt2x00usb: Unknown symbol rt2x00lib_suspend
[ 2028.559285] rt2x00usb: Unknown symbol rt2x00lib_probe_dev
[ 2028.559493] rt2x00usb: Unknown symbol rt2x00lib_rxdone
[ 2028.559546] rt2x00usb: Unknown symbol rt2x00queue_get_entry
[ 2028.559721] rt2x00usb: Unknown symbol rt2x00lib_remove_dev
[ 2028.559794] rt2x00usb: Unknown symbol rt2x00lib_txdone
[ 2028.559847] rt2x00usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.559958] rt2x00usb: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.560014] rt2x00usb: Unknown symbol rt2x00lib_resume
[ 2028.560115] rt2x00usb: Unknown symbol rt2x00queue_index_inc
[ 2028.560168] rt2x00usb: Unknown symbol rt2x_ieee80211_get_hdrlen_from_skb
[ 2028.560246] rt2x00usb: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.560827] rt73usb: Unknown symbol rt2x00mac_add_interface
[ 2028.560912] rt73usb: Unknown symbol rt2x00mac_get_stats
[ 2028.560965] rt73usb: Unknown symbol rt2x00usb_init_rxentry
[ 2028.561068] rt73usb: Unknown symbol rt2x00usb_disable_radio
[ 2028.561127] rt73usb: Unknown symbol rt2x00usb_init_txentry
[ 2028.561178] rt73usb: Unknown symbol rt2x00usb_vendor_request_buff
[ 2028.561259] rt73usb: Unknown symbol rt2x00usb_write_tx_data
[ 2028.561311] rt73usb: Unknown symbol rt2x00mac_config_interface
[ 2028.561364] rt73usb: Unknown symbol rt2x00mac_remove_interface
[ 2028.561417] rt73usb: Unknown symbol rt2x00usb_vendor_request
[ 2028.561469] rt73usb: Unknown symbol rt2x00usb_probe
[ 2028.561521] rt73usb: Unknown symbol rt2x00mac_config
[ 2028.561574] rt73usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.561630] rt73usb: Unknown symbol rt2x00usb_suspend
[ 2028.561682] rt73usb: Unknown symbol rt2x00mac_conf_tx
[ 2028.561735] rt73usb: Unknown symbol rt2x00mac_start
[ 2028.561787] rt73usb: Unknown symbol rt2x00mac_stop
[ 2028.561891] rt73usb: Unknown symbol rt2x00mac_configure_filter
[ 2028.561944] rt73usb: Unknown symbol rt2x00usb_disconnect
[ 2028.561996] rt73usb: Unknown symbol rt2x00mac_tx
[ 2028.562066] rt73usb: Unknown symbol rt2x00usb_vendor_req_buff_lock
[ 2028.562118] rt73usb: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.562188] rt73usb: Unknown symbol rt2x00usb_resume
[ 2028.562272] rt73usb: Unknown symbol rt2x00usb_uninitialize
[ 2028.562324] rt73usb: Unknown symbol rt2x00usb_initialize
[ 2028.562385] rt73usb: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.577597] usbcore: registered new interface driver cdc_ether
[ 2028.579730] usbcore: registered new interface driver rndis_host
[ 2028.582005] usbcore: registered new interface driver rndis_wlan
[ 2028.595072] Atmel at76x USB Wireless LAN Driver 0.17 loading
[ 2028.595137] usbcore: registered new interface driver at76_usb
[ 2030.867027] Broadcom 43xx driver loaded [ Features: PMLR, Firmware-ID: FW13 ]
[ 2030.889861] Broadcom 43xx-legacy driver loaded [ Features: PID, Firmware-ID: FW10 ]
[ 2048.729929] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2048.729947] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2048.730032] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2048.730037] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2048.731308] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2048.731313] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2048.732933] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2048.732938] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2048.736697] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2048.736877] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2048.737179] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2048.737401] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2048.737536] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2048.737847] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2048.737971] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2048.738300] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2048.738424] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2048.738675] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2048.738799] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2048.738938] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2048.739195] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2048.739381] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2048.739505] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2048.739844] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2048.740187] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2048.740317] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2048.740539] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2048.741033] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2048.741236] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2065.088256] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2065.088270] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2065.088355] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2065.088362] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2065.089631] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2065.089638] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2065.091268] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2065.091275] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2065.093466] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2065.093653] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2065.093959] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2065.094185] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2065.094321] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2065.094635] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2065.094760] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2065.095122] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2065.095249] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2065.095501] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2065.095629] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2065.095770] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2065.096070] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2065.096245] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2065.096371] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2065.096712] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2065.097056] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2065.097189] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2065.097410] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2065.097899] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2065.098102] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2076.137874] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2076.137887] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2076.137972] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2076.137977] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2076.139286] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2076.139293] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2076.140921] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2076.140928] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2076.143093] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2076.143272] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2076.143574] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2076.143796] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2076.143931] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2076.144242] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2076.144367] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2076.144696] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2076.144820] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2076.145072] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2076.145196] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2076.145336] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2076.145592] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2076.145766] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2076.145891] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2076.146230] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2076.146573] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2076.146717] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2076.146936] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2076.147425] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2076.147626] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2082.930484] atkbd.c: Unknown key pressed (translated set 2, code 0xe1 on isa0060/serio0).
[ 2082.930495] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.162936] usb 3-2: USB disconnect, address 2
[ 2083.194637] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[ 2083.194648] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.699241] atkbd.c: Unknown key pressed (translated set 2, code 0xe1 on isa0060/serio0).
[ 2083.699252] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.741367] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[ 2083.741377] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.817504] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 2083.845489] usb 3-2: configuration #1 chosen from 1 choice
[ 2086.100418] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2086.100434] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2086.100519] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2086.100526] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2086.101788] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2086.101795] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2086.103421] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2086.103428] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2086.105485] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2086.105669] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2086.105973] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2086.106198] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2086.106334] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2086.106647] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2086.106773] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2086.107103] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2086.107231] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2086.107483] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2086.107607] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2086.107758] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2086.108015] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2086.108189] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2086.108313] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2086.108653] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2086.108996] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2086.109126] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2086.109346] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2086.109834] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2086.110035] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues

```
I'll reboot the computer and see if it works afterwards.

---

### Post by tangibleorange on 2008-08-31
if it still doesn't work could you post the output of:

```
dmesg | grep iwl
```

---

### Post by evillan on 2008-08-31
> **tangibleorange said:**
> if it still doesn't work could you post the output of:

```
dmesg | grep iwl
```

I haven't rebooted it yet, I'll do it afterwards I've posted this:
```

xxx:~$ dmesg | grep iwl
[   38.381326] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   38.381331] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   38.381531] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   38.425251] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   47.616275] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   47.619689] Registered led device: iwl-phy0:RX
[   47.619731] Registered led device: iwl-phy0:TX
[ 1424.291188] Registered led device: iwl-phy0:RX
[ 1424.291208] Registered led device: iwl-phy0:TX
[ 1433.236240] Registered led device: iwl-phy0:RX
[ 1433.236260] Registered led device: iwl-phy0:TX
[ 1433.429763] Registered led device: iwl-phy0:RX
[ 1433.429783] Registered led device: iwl-phy0:TX
[ 2028.282879] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2028.282888] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2028.282924] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2028.282928] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2028.283487] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2028.283491] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2028.284185] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2028.284188] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2028.285198] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2028.285276] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2028.285406] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2028.285502] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2028.285559] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2028.285693] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2028.285746] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2028.285886] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2028.285940] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2028.286048] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2028.286102] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2028.286161] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2028.286270] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2028.286344] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2028.286398] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2028.286543] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2028.286691] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2028.286747] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2028.286841] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2028.287050] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2028.287137] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2028.296567] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2028.296575] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2028.296610] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2028.296612] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2028.297151] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2028.297153] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2028.297848] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2028.297850] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2028.300544] iwl4965: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2028.300624] iwl4965: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2028.300767] iwl4965: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2028.300862] iwl4965: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2028.300919] iwl4965: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2028.301053] iwl4965: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2028.301106] iwl4965: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2028.301246] iwl4965: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2028.301299] iwl4965: Unknown symbol iwlwifi_sta_info_put
[ 2028.301407] iwl4965: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2028.301459] iwl4965: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2028.301519] iwl4965: Unknown symbol iwlwifi_sta_info_get
[ 2028.301644] iwl4965: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2028.301718] iwl4965: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2028.301771] iwl4965: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2028.301916] iwl4965: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2028.302106] iwl4965: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2028.302161] iwl4965: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2028.302255] iwl4965: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2028.302491] iwl4965: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2028.302579] iwl4965: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2048.729929] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2048.729947] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2048.730032] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2048.730037] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2048.731308] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2048.731313] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2048.732933] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2048.732938] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2048.736697] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2048.736877] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2048.737179] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2048.737401] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2048.737536] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2048.737847] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2048.737971] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2048.738300] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2048.738424] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2048.738675] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2048.738799] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2048.738938] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2048.739195] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2048.739381] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2048.739505] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2048.739844] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2048.740187] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2048.740317] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2048.740539] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2048.741033] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2048.741236] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2065.088256] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2065.088270] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2065.088355] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2065.088362] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2065.089631] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2065.089638] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2065.091268] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2065.091275] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2065.093466] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2065.093653] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2065.093959] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2065.094185] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2065.094321] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2065.094635] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2065.094760] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2065.095122] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2065.095249] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2065.095501] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2065.095629] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2065.095770] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2065.096070] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2065.096245] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2065.096371] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2065.096712] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2065.097056] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2065.097189] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2065.097410] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2065.097899] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2065.098102] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2076.137874] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2076.137887] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2076.137972] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2076.137977] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2076.139286] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2076.139293] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2076.140921] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2076.140928] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2076.143093] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2076.143272] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2076.143574] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2076.143796] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2076.143931] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2076.144242] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2076.144367] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2076.144696] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2076.144820] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2076.145072] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2076.145196] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2076.145336] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2076.145592] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2076.145766] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2076.145891] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2076.146230] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2076.146573] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2076.146717] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2076.146936] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2076.147425] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2076.147626] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2086.100418] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2086.100434] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2086.100519] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2086.100526] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2086.101788] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2086.101795] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2086.103421] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2086.103428] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2086.105485] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2086.105669] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2086.105973] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2086.106198] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2086.106334] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2086.106647] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2086.106773] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2086.107103] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2086.107231] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2086.107483] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2086.107607] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2086.107758] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2086.108015] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2086.108189] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2086.108313] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2086.108653] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2086.108996] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2086.109126] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2086.109346] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2086.109834] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2086.110035] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues

```

It looks like it is detecting the wireless card?
Anyways, I'll return in a minute.

---

### Post by evillan on 2008-08-31
And after the reboot:

```

xxx:~$ dmesg | grep iwl
[   38.366575] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[   38.366581] iwlwifi_mac80211: Unknown symbol wiphy_register
[   38.366613] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[   38.366616] iwlwifi_mac80211: Unknown symbol wiphy_new
[   38.367153] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[   38.367156] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[   38.367848] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[   38.367851] iwlwifi_mac80211: Unknown symbol wiphy_free
[   38.439055] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[   38.439126] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[   38.439248] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[   38.439336] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[   38.439387] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[   38.439513] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[   38.439559] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   38.439693] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[   38.439739] iwl3945: Unknown symbol iwlwifi_sta_info_put
[   38.439840] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[   38.439886] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[   38.439938] iwl3945: Unknown symbol iwlwifi_sta_info_get
[   38.440041] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[   38.440108] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[   38.440154] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[   38.440292] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[   38.440432] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[   38.440480] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   38.440567] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[   38.440769] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[   38.440848] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues

```

---

### Post by Blackcabs on 2008-08-31
> **evillan said:**
> Ok, so I followed your instructions and everything appeared to work fine until
```
xxx$ sudo modprobe iwl3945
WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

This is the output of dmesg:```
[ 2028.393174] rt2400pci: Unknown symbol rt2x00pci_suspend
[ 2028.393227] rt2400pci: Unknown symbol rt2x00mac_config_interface
[ 2028.393279] rt2400pci: Unknown symbol rt2x00pci_remove
[ 2028.393331] rt2400pci: Unknown symbol rt2x00mac_remove_interface
[ 2028.393383] rt2400pci: Unknown symbol rt2x00mac_config
[ 2028.393435] rt2400pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.393488] rt2400pci: Unknown symbol rt2x00queue_get_queue
[ 2028.393540] rt2400pci: Unknown symbol rt2x00mac_conf_tx
[ 2028.393623] rt2400pci: Unknown symbol rt2x00mac_start
[ 2028.393674] rt2400pci: Unknown symbol rt2x00pci_txdone
[ 2028.393727] rt2400pci: Unknown symbol rt2x00mac_stop
[ 2028.393781] rt2400pci: Unknown symbol rt2x00mac_configure_filter
[ 2028.393833] rt2400pci: Unknown symbol rt2x00mac_tx
[ 2028.393885] rt2400pci: Unknown symbol rt2x00pci_resume
[ 2028.393951] rt2400pci: Unknown symbol rt2x00pci_probe
[ 2028.394003] rt2400pci: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.394079] rt2400pci: Unknown symbol rt2x00pci_rxdone
[ 2028.394131] rt2400pci: Unknown symbol rt2x00lib_beacondone
[ 2028.394186] rt2400pci: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.394238] rt2400pci: Unknown symbol rt2x00pci_write_tx_data
[ 2028.415214] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.415221] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.415225] Pid: 19700, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.415235]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.415255]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.415265]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.415270]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.415277]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.415284]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.415292]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.415298]  [<c028374f>] class_register+0x9f/0x140
[ 2028.415309]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.415318]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.415357]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.415374]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.415393]  =======================
[ 2028.415398] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.415404] Pid: 19700, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.415409]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.415417]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.415426]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.415433]  [<c028374f>] class_register+0x9f/0x140
[ 2028.415444]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.415453]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.415488]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.415504]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.415521]  =======================
[ 2028.430546] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.430685] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.431164] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.431268] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.431496] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.431953] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.432112] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.432482] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.432608] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.433859] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.433963] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.434016] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.434071] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.434124] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.434210] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.434356] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.434431] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.434487] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.434538] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.434642] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.434851] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.435415] rt2x00pci: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.435468] rt2x00pci: Unknown symbol rt2x00lib_suspend
[ 2028.435521] rt2x00pci: Unknown symbol rt2x00lib_probe_dev
[ 2028.435589] rt2x00pci: Unknown symbol rt2x_ieee80211_get_hdrlen
[ 2028.435700] rt2x00pci: Unknown symbol rt2x00lib_rxdone
[ 2028.435752] rt2x00pci: Unknown symbol rt2x00queue_get_entry
[ 2028.435825] rt2x00pci: Unknown symbol rt2x00lib_remove_dev
[ 2028.435915] rt2x00pci: Unknown symbol rt2x00lib_txdone
[ 2028.435969] rt2x00pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.436069] rt2x00pci: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.436137] rt2x00pci: Unknown symbol rt2x00lib_resume
[ 2028.436188] rt2x00pci: Unknown symbol rt2x00queue_index_inc
[ 2028.436261] rt2x00pci: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.436784] rt2500pci: Unknown symbol rt2x00mac_add_interface
[ 2028.436837] rt2500pci: Unknown symbol rt2x00mac_get_stats
[ 2028.436905] rt2500pci: Unknown symbol rt2x00pci_initialize
[ 2028.436973] rt2500pci: Unknown symbol rt2x00pci_uninitialize
[ 2028.437025] rt2500pci: Unknown symbol rt2x00queue_get_entry
[ 2028.437078] rt2500pci: Unknown symbol rt2x00pci_suspend
[ 2028.437130] rt2500pci: Unknown symbol rt2x00mac_config_interface
[ 2028.437182] rt2500pci: Unknown symbol rt2x00pci_remove
[ 2028.437234] rt2500pci: Unknown symbol rt2x00mac_remove_interface
[ 2028.437287] rt2500pci: Unknown symbol rt2x00mac_config
[ 2028.437339] rt2500pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.437391] rt2500pci: Unknown symbol rt2x00queue_get_queue
[ 2028.437443] rt2500pci: Unknown symbol rt2x00mac_conf_tx
[ 2028.437527] rt2500pci: Unknown symbol rt2x00mac_start
[ 2028.437579] rt2500pci: Unknown symbol rt2x00pci_txdone
[ 2028.437638] rt2500pci: Unknown symbol rt2x00mac_stop
[ 2028.437712] rt2500pci: Unknown symbol rt2x00mac_configure_filter
[ 2028.437764] rt2500pci: Unknown symbol rt2x00mac_tx
[ 2028.437816] rt2500pci: Unknown symbol rt2x00pci_resume
[ 2028.437882] rt2500pci: Unknown symbol rt2x00pci_probe
[ 2028.437934] rt2500pci: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.438003] rt2500pci: Unknown symbol rt2x00pci_rxdone
[ 2028.438056] rt2500pci: Unknown symbol rt2x00lib_beacondone
[ 2028.438111] rt2500pci: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.438163] rt2500pci: Unknown symbol rt2x00pci_write_tx_data
[ 2028.467685] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.467695] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.467699] Pid: 19707, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.467726]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.467748]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.467764]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.467772]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.467780]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.467788]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.467798]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.467807]  [<c028374f>] class_register+0x9f/0x140
[ 2028.467822]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.467834]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.467880]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.467901]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.467923]  =======================
[ 2028.467928] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.467934] Pid: 19707, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.467941]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.467951]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.467961]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.467969]  [<c028374f>] class_register+0x9f/0x140
[ 2028.467982]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.467992]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.468029]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.468046]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.468064]  =======================
[ 2028.474347] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.474480] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.474959] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.475062] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.475290] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.475746] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.475895] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.476264] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.476390] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.477284] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.477387] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.477440] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.477496] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.477549] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.477644] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.477790] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.477864] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.477922] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.477974] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.478079] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.478288] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.478969] rt2x00pci: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.479023] rt2x00pci: Unknown symbol rt2x00lib_suspend
[ 2028.479075] rt2x00pci: Unknown symbol rt2x00lib_probe_dev
[ 2028.479144] rt2x00pci: Unknown symbol rt2x_ieee80211_get_hdrlen
[ 2028.479255] rt2x00pci: Unknown symbol rt2x00lib_rxdone
[ 2028.479308] rt2x00pci: Unknown symbol rt2x00queue_get_entry
[ 2028.479380] rt2x00pci: Unknown symbol rt2x00lib_remove_dev
[ 2028.479470] rt2x00pci: Unknown symbol rt2x00lib_txdone
[ 2028.479524] rt2x00pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.479624] rt2x00pci: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.479692] rt2x00pci: Unknown symbol rt2x00lib_resume
[ 2028.479744] rt2x00pci: Unknown symbol rt2x00queue_index_inc
[ 2028.479817] rt2x00pci: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.481947] rt61pci: Unknown symbol rt2x00mac_add_interface
[ 2028.482035] rt61pci: Unknown symbol rt2x00mac_get_stats
[ 2028.482103] rt61pci: Unknown symbol rt2x00pci_initialize
[ 2028.482231] rt61pci: Unknown symbol rt2x00pci_uninitialize
[ 2028.482284] rt61pci: Unknown symbol rt2x00queue_get_entry
[ 2028.482351] rt61pci: Unknown symbol rt2x00pci_suspend
[ 2028.482403] rt61pci: Unknown symbol rt2x00mac_config_interface
[ 2028.482456] rt61pci: Unknown symbol rt2x00pci_remove
[ 2028.482508] rt61pci: Unknown symbol rt2x00mac_remove_interface
[ 2028.482560] rt61pci: Unknown symbol rt2x00mac_config
[ 2028.482613] rt61pci: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.482666] rt61pci: Unknown symbol rt2x00queue_get_queue
[ 2028.482718] rt61pci: Unknown symbol rt2x00mac_conf_tx
[ 2028.482802] rt61pci: Unknown symbol rt2x00mac_start
[ 2028.482855] rt61pci: Unknown symbol rt2x00pci_txdone
[ 2028.482906] rt61pci: Unknown symbol rt2x00mac_stop
[ 2028.482961] rt61pci: Unknown symbol rt2x00mac_configure_filter
[ 2028.483014] rt61pci: Unknown symbol rt2x00mac_tx
[ 2028.483066] rt61pci: Unknown symbol rt2x00pci_resume
[ 2028.483132] rt61pci: Unknown symbol rt2x00pci_probe
[ 2028.483184] rt61pci: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.483285] rt61pci: Unknown symbol rt2x00pci_rxdone
[ 2028.483340] rt61pci: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.483392] rt61pci: Unknown symbol rt2x00pci_write_tx_data
[ 2028.502845] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.502851] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.502856] Pid: 19717, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.502867]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.502888]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.502899]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.502905]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.502912]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.502918]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.502926]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.502931]  [<c028374f>] class_register+0x9f/0x140
[ 2028.502943]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.502950]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.502987]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.503002]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.503019]  =======================
[ 2028.503022] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.503027] Pid: 19717, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.503031]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.503037]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.503044]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.503049]  [<c028374f>] class_register+0x9f/0x140
[ 2028.503058]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.503065]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.503098]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.503111]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.503126]  =======================
[ 2028.516815] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.516951] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.517434] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.517537] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.517769] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.518229] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.518384] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.518765] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.518894] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.519883] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.519998] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.520052] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.520108] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.520160] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.520247] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.520393] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.520467] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.520524] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.520576] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.520681] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.520891] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.521606] rt2x00usb: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.521659] rt2x00usb: Unknown symbol rt2x00lib_suspend
[ 2028.521712] rt2x00usb: Unknown symbol rt2x00lib_probe_dev
[ 2028.521919] rt2x00usb: Unknown symbol rt2x00lib_rxdone
[ 2028.521972] rt2x00usb: Unknown symbol rt2x00queue_get_entry
[ 2028.522147] rt2x00usb: Unknown symbol rt2x00lib_remove_dev
[ 2028.522220] rt2x00usb: Unknown symbol rt2x00lib_txdone
[ 2028.522272] rt2x00usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.522382] rt2x00usb: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.522438] rt2x00usb: Unknown symbol rt2x00lib_resume
[ 2028.522539] rt2x00usb: Unknown symbol rt2x00queue_index_inc
[ 2028.522592] rt2x00usb: Unknown symbol rt2x_ieee80211_get_hdrlen_from_skb
[ 2028.522670] rt2x00usb: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.523222] rt2500usb: Unknown symbol rt2x00mac_add_interface
[ 2028.523276] rt2500usb: Unknown symbol rt2x00mac_get_stats
[ 2028.523329] rt2500usb: Unknown symbol rt2x00usb_init_rxentry
[ 2028.523432] rt2500usb: Unknown symbol rt2x00usb_disable_radio
[ 2028.523484] rt2500usb: Unknown symbol rt2x00usb_init_txentry
[ 2028.523537] rt2500usb: Unknown symbol rt2x00usb_vendor_request_buff
[ 2028.523678] rt2500usb: Unknown symbol rt2x00usb_write_tx_data
[ 2028.523730] rt2500usb: Unknown symbol rt2x00mac_config_interface
[ 2028.523783] rt2500usb: Unknown symbol rt2x00mac_remove_interface
[ 2028.523835] rt2500usb: Unknown symbol rt2x00usb_vendor_request
[ 2028.523888] rt2500usb: Unknown symbol rt2x00usb_probe
[ 2028.523954] rt2500usb: Unknown symbol rt2x00mac_config
[ 2028.524006] rt2500usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.524063] rt2500usb: Unknown symbol rt2x00usb_suspend
[ 2028.524115] rt2500usb: Unknown symbol rt2x00mac_conf_tx
[ 2028.524167] rt2500usb: Unknown symbol rt2x00mac_start
[ 2028.524220] rt2500usb: Unknown symbol rt2x00mac_stop
[ 2028.524325] rt2500usb: Unknown symbol rt2x00mac_configure_filter
[ 2028.524377] rt2500usb: Unknown symbol rt2x00usb_disconnect
[ 2028.524430] rt2500usb: Unknown symbol rt2x00mac_tx
[ 2028.524499] rt2500usb: Unknown symbol rt2x00usb_vendor_req_buff_lock
[ 2028.524551] rt2500usb: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.524621] rt2500usb: Unknown symbol rt2x00usb_resume
[ 2028.524673] rt2500usb: Unknown symbol rt2x00usb_uninitialize
[ 2028.524726] rt2500usb: Unknown symbol rt2x00usb_initialize
[ 2028.524781] rt2500usb: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.544569] sysfs: duplicate filename 'ieee80211' can not be created
[ 2028.544575] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[ 2028.544579] Pid: 19724, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.544592]  [<c01d74df>] sysfs_add_one+0x9f/0xe0
[ 2028.544608]  [<c01d7a18>] create_dir+0x48/0x90
[ 2028.544619]  [<c01d7a89>] sysfs_create_dir+0x29/0x50
[ 2028.544624]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.544631]  [<c0215993>] kobject_add+0x93/0x1b0
[ 2028.544638]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.544646]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.544652]  [<c028374f>] class_register+0x9f/0x140
[ 2028.544664]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.544672]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.544711]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.544727]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.544745]  =======================
[ 2028.544748] kobject_add failed for ieee80211 with -EEXIST, don't try to register things with the same name in the same directory.
[ 2028.544753] Pid: 19724, comm: modprobe Not tainted 2.6.24-19-generic #1
[ 2028.544757]  [<c0215a13>] kobject_add+0x113/0x1b0
[ 2028.544764]  [<c02154cf>] kobject_get+0xf/0x20
[ 2028.544772]  [<c0215ae1>] kset_register+0x21/0x50
[ 2028.544778]  [<c028374f>] class_register+0x9f/0x140
[ 2028.544788]  [<f9013146>] rt2x_cfg80211_init+0x6/0x60 [rt2x_cfg80211]
[ 2028.544794]  [<c01507c6>] sys_init_module+0x126/0x19c0
[ 2028.544828]  [<c018e960>] __kmalloc+0x0/0x110
[ 2028.544842]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2028.544856]  =======================
[ 2028.554636] rt2x_mac80211: Unknown symbol rt2x_wiphy_free
[ 2028.554768] rt2x_mac80211: Unknown symbol rt2x___ieee80211_get_channel
[ 2028.555245] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_init
[ 2028.555349] rt2x_mac80211: Unknown symbol rt2x_wiphy_register
[ 2028.555577] rt2x_mac80211: Unknown symbol rt2x_wiphy_new
[ 2028.556034] rt2x_mac80211: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.556182] rt2x_mac80211: Unknown symbol rt2x_ieee80211_radiotap_iterator_next
[ 2028.556551] rt2x_mac80211: Unknown symbol rt2x_wiphy_unregister
[ 2028.556677] rt2x_mac80211: Unknown symbol rt2x_ieee80211_frequency_to_channel
[ 2028.557584] rt2x00lib: Unknown symbol rt2x_ieee80211_iterate_active_interfaces
[ 2028.557687] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queues
[ 2028.557740] rt2x00lib: Unknown symbol rt2x_ieee80211_rts_get
[ 2028.557795] rt2x00lib: Unknown symbol rt2x_ieee80211_beacon_get
[ 2028.557848] rt2x00lib: Unknown symbol rt2x_ieee80211_ctstoself_get
[ 2028.557934] rt2x00lib: Unknown symbol rt2x_ieee80211_register_hw
[ 2028.558080] rt2x00lib: Unknown symbol rt2x_ieee80211_tx_status_irqsafe
[ 2028.558155] rt2x00lib: Unknown symbol rt2x_ieee80211_stop_queue
[ 2028.558212] rt2x00lib: Unknown symbol rt2x_ieee80211_start_queues
[ 2028.558265] rt2x00lib: Unknown symbol rt2x_ieee80211_channel_to_frequency
[ 2028.558370] rt2x00lib: Unknown symbol rt2x_ieee80211_rx_irqsafe
[ 2028.558579] rt2x00lib: Unknown symbol rt2x_ieee80211_unregister_hw
[ 2028.559179] rt2x00usb: Unknown symbol rt2x_ieee80211_wake_queue
[ 2028.559233] rt2x00usb: Unknown symbol rt2x00lib_suspend
[ 2028.559285] rt2x00usb: Unknown symbol rt2x00lib_probe_dev
[ 2028.559493] rt2x00usb: Unknown symbol rt2x00lib_rxdone
[ 2028.559546] rt2x00usb: Unknown symbol rt2x00queue_get_entry
[ 2028.559721] rt2x00usb: Unknown symbol rt2x00lib_remove_dev
[ 2028.559794] rt2x00usb: Unknown symbol rt2x00lib_txdone
[ 2028.559847] rt2x00usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.559958] rt2x00usb: Unknown symbol rt2x_ieee80211_free_hw
[ 2028.560014] rt2x00usb: Unknown symbol rt2x00lib_resume
[ 2028.560115] rt2x00usb: Unknown symbol rt2x00queue_index_inc
[ 2028.560168] rt2x00usb: Unknown symbol rt2x_ieee80211_get_hdrlen_from_skb
[ 2028.560246] rt2x00usb: Unknown symbol rt2x_ieee80211_alloc_hw
[ 2028.560827] rt73usb: Unknown symbol rt2x00mac_add_interface
[ 2028.560912] rt73usb: Unknown symbol rt2x00mac_get_stats
[ 2028.560965] rt73usb: Unknown symbol rt2x00usb_init_rxentry
[ 2028.561068] rt73usb: Unknown symbol rt2x00usb_disable_radio
[ 2028.561127] rt73usb: Unknown symbol rt2x00usb_init_txentry
[ 2028.561178] rt73usb: Unknown symbol rt2x00usb_vendor_request_buff
[ 2028.561259] rt73usb: Unknown symbol rt2x00usb_write_tx_data
[ 2028.561311] rt73usb: Unknown symbol rt2x00mac_config_interface
[ 2028.561364] rt73usb: Unknown symbol rt2x00mac_remove_interface
[ 2028.561417] rt73usb: Unknown symbol rt2x00usb_vendor_request
[ 2028.561469] rt73usb: Unknown symbol rt2x00usb_probe
[ 2028.561521] rt73usb: Unknown symbol rt2x00mac_config
[ 2028.561574] rt73usb: Unknown symbol rt2x00lib_write_tx_desc
[ 2028.561630] rt73usb: Unknown symbol rt2x00usb_suspend
[ 2028.561682] rt73usb: Unknown symbol rt2x00mac_conf_tx
[ 2028.561735] rt73usb: Unknown symbol rt2x00mac_start
[ 2028.561787] rt73usb: Unknown symbol rt2x00mac_stop
[ 2028.561891] rt73usb: Unknown symbol rt2x00mac_configure_filter
[ 2028.561944] rt73usb: Unknown symbol rt2x00usb_disconnect
[ 2028.561996] rt73usb: Unknown symbol rt2x00mac_tx
[ 2028.562066] rt73usb: Unknown symbol rt2x00usb_vendor_req_buff_lock
[ 2028.562118] rt73usb: Unknown symbol rt2x00mac_get_tx_stats
[ 2028.562188] rt73usb: Unknown symbol rt2x00usb_resume
[ 2028.562272] rt73usb: Unknown symbol rt2x00usb_uninitialize
[ 2028.562324] rt73usb: Unknown symbol rt2x00usb_initialize
[ 2028.562385] rt73usb: Unknown symbol rt2x00mac_bss_info_changed
[ 2028.577597] usbcore: registered new interface driver cdc_ether
[ 2028.579730] usbcore: registered new interface driver rndis_host
[ 2028.582005] usbcore: registered new interface driver rndis_wlan
[ 2028.595072] Atmel at76x USB Wireless LAN Driver 0.17 loading
[ 2028.595137] usbcore: registered new interface driver at76_usb
[ 2030.867027] Broadcom 43xx driver loaded [ Features: PMLR, Firmware-ID: FW13 ]
[ 2030.889861] Broadcom 43xx-legacy driver loaded [ Features: PID, Firmware-ID: FW10 ]
[ 2048.729929] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2048.729947] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2048.730032] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2048.730037] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2048.731308] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2048.731313] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2048.732933] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2048.732938] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2048.736697] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2048.736877] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2048.737179] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2048.737401] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2048.737536] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2048.737847] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2048.737971] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2048.738300] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2048.738424] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2048.738675] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2048.738799] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2048.738938] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2048.739195] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2048.739381] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2048.739505] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2048.739844] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2048.740187] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2048.740317] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2048.740539] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2048.741033] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2048.741236] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2065.088256] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2065.088270] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2065.088355] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2065.088362] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2065.089631] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2065.089638] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2065.091268] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2065.091275] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2065.093466] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2065.093653] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2065.093959] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2065.094185] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2065.094321] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2065.094635] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2065.094760] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2065.095122] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2065.095249] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2065.095501] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2065.095629] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2065.095770] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2065.096070] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2065.096245] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2065.096371] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2065.096712] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2065.097056] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2065.097189] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2065.097410] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2065.097899] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2065.098102] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2076.137874] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2076.137887] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2076.137972] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2076.137977] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2076.139286] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2076.139293] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2076.140921] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2076.140928] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2076.143093] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2076.143272] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2076.143574] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2076.143796] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2076.143931] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2076.144242] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2076.144367] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2076.144696] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2076.144820] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2076.145072] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2076.145196] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2076.145336] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2076.145592] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2076.145766] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2076.145891] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2076.146230] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2076.146573] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2076.146717] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2076.146936] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2076.147425] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2076.147626] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues
[ 2082.930484] atkbd.c: Unknown key pressed (translated set 2, code 0xe1 on isa0060/serio0).
[ 2082.930495] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.162936] usb 3-2: USB disconnect, address 2
[ 2083.194637] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[ 2083.194648] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.699241] atkbd.c: Unknown key pressed (translated set 2, code 0xe1 on isa0060/serio0).
[ 2083.699252] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.741367] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[ 2083.741377] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[ 2083.817504] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 2083.845489] usb 3-2: configuration #1 chosen from 1 choice
[ 2086.100418] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[ 2086.100434] iwlwifi_mac80211: Unknown symbol wiphy_register
[ 2086.100519] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[ 2086.100526] iwlwifi_mac80211: Unknown symbol wiphy_new
[ 2086.101788] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[ 2086.101795] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[ 2086.103421] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[ 2086.103428] iwlwifi_mac80211: Unknown symbol wiphy_free
[ 2086.105485] iwl3945: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[ 2086.105669] iwl3945: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[ 2086.105973] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[ 2086.106198] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[ 2086.106334] iwl3945: Unknown symbol iwlwifi___ieee80211_get_rx_led_name
[ 2086.106647] iwl3945: Unknown symbol iwlwifi_ieee80211_tx_status
[ 2086.106773] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[ 2086.107103] iwl3945: Unknown symbol iwlwifi_ieee80211_stop_queue
[ 2086.107231] iwl3945: Unknown symbol iwlwifi_sta_info_put
[ 2086.107483] iwl3945: Unknown symbol iwlwifi_ieee80211_free_hw
[ 2086.107607] iwl3945: Unknown symbol iwlwifi_ieee80211_beacon_get
[ 2086.107758] iwl3945: Unknown symbol iwlwifi_sta_info_get
[ 2086.108015] iwl3945: Unknown symbol iwlwifi_ieee80211_alloc_hw
[ 2086.108189] iwl3945: Unknown symbol iwlwifi___ieee80211_get_tx_led_name
[ 2086.108313] iwl3945: Unknown symbol iwlwifi_ieee80211_scan_completed
[ 2086.108653] iwl3945: Unknown symbol iwlwifi_ieee80211_register_hw
[ 2086.108996] iwl3945: Unknown symbol iwlwifi_ieee80211_wake_queue
[ 2086.109126] iwl3945: Unknown symbol iwlwifi_ieee80211_rate_control_register
[ 2086.109346] iwl3945: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[ 2086.109834] iwl3945: Unknown symbol iwlwifi_ieee80211_unregister_hw
[ 2086.110035] iwl3945: Unknown symbol iwlwifi_ieee80211_start_queues

```
I'll reboot the computer and see if it works afterwards.

Ok all of these errors are due to compat-wireless loading all the drivers that come in its package at the same time. When you typed "sudo make load did you not get the option to chose just the iwl3945 driver. Its no major as after a reboot it should just load the one for your card. Just a quick thought you dont have a small sliding button on your laptop that can disable the card do you ??? mine has one.

---

### Post by Blackcabs on 2008-08-31
Can you also post the output of lshw -C network again

---

### Post by evillan on 2008-08-31
> **Blackcabs said:**
> Ok all of these errors are due to compat-wireless loading all the drivers that come in its package at the same time. When you typed "sudo make load did you not get the option to chose just the iwl3945 driver. Its no major as after a reboot it should just load the one for your card. Just a quick thought you dont have a small sliding button on your laptop that can disable the card do you ??? mine has one.

Yes, my laptop does have a hot key to enable the wireless card. It is turned on (I just pressed it twice - off - on, and a pop up box appeared: "Device has been made discoverable"). So it is turned on.

However, the wireless internet does appear at "Network Settings" anymore:
[IMG]http://peecee.dk/uploads/082008/wire4.png[/IMG]
It's not on the iwlist either:
```
:~$ iwlist  scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

Anyways, the output of
```

xxx:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:1f:68:b8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.2.101 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

---

### Post by Blackcabs on 2008-08-31
The new interface will be called wlan0 and its master will be wmaster0....My laptop has 2 hot buttons 1 for bluetooth & 1 for wifi... that ""new device has been made discoverable"" is a bluetooth device not wifi
To make sure the kill switch is not activated use the command below

You can double check with this command  $ find /sys -type f -name 'rf_kill' -exec cat {} \;

0= radio on
1= radio off

If none of this works we can try sudo apt-get install linux-backports-modules-hardy-generic..or you could try to enable the mac manually

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

For network manager to detect your wifi the wired connection needs to be unpluged

Can you please post the output of lspci and can you make sure that your wired connection is unpluged before you do any of these things,,apparently networkmanager will not try to bring up your wifi if there is a wired connection already in place.
Also if you wish to return things to how they were before you installed iwl3945 cd into the directory and type make unload.

One other thing when your pc starts do you get a list of previous kernels to chose from and was your first install of Ubuntu 8.04 or did you start with an earlier version IE 7.10 then upgrade... My reason for asking is that apparently there is an issue with network manager in 8.04 if you have upgraded from an earlier version IE the one in 7.10..If you use wicd from this link [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) it should help.

---

### Post by evillan on 2008-09-04
> **Blackcabs said:**
> The new interface will be called wlan0 and its master will be wmaster0....My laptop has 2 hot buttons 1 for bluetooth & 1 for wifi... that ""new device has been made discoverable"" is a bluetooth device not wifi
To make sure the kill switch is not activated use the command below

You can double check with this command  $ find /sys -type f -name 'rf_kill' -exec cat {} \;

0= radio on
1= radio off

If none of this works we can try sudo apt-get install linux-backports-modules-hardy-generic..or you could try to enable the mac manually

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

For network manager to detect your wifi the wired connection needs to be unpluged

Can you please post the output of lspci and can you make sure that your wired connection is unpluged before you do any of these things,,apparently networkmanager will not try to bring up your wifi if there is a wired connection already in place.
Also if you wish to return things to how they were before you installed iwl3945 cd into the directory and type make unload.

One other thing when your pc starts do you get a list of previous kernels to chose from and was your first install of Ubuntu 8.04 or did you start with an earlier version IE 7.10 then upgrade... My reason for asking is that apparently there is an issue with network manager in 8.04 if you have upgraded from an earlier version IE the one in 7.10..If you use wicd from this link [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) it should help.

Hi, sorry I didn't answer, I've been a bit busy. The wireless internet is still not working. I did upgrade from 7.10 to 8.04! I'll look into that. 
This is the output of lspci with the wired internet connection unplugged:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

I only have one button for the bluetooth/wireless internet and I used to work before I installed the driver per your instructions. So I don't think that's the problem. I will uninstall the driver now, it does not seem to work.

Where do you find 
> Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)



I looked in System -> Adm and Pre, it's not there.

---

### Post by evillan on 2008-09-05
So I uninstalled the iwl3945 driver and now the wireless scan returns some results

```

xxx:~$ iwlist  scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:29
                    ESSID:"fido"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/100  Signal level=-73 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000020538967e49
          Cell 02 - Address: 00:18:39:C9:A3:31
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=85/100  Signal level=-48 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000109569186

```
However, the network-manager (nm-applet) is still not working. How do I connect to one of this wireless networks without the nm-applet?
I tried to remove the nm-applet and install it again, nothing happened:

```

xxx:~$  nm-applet &
[1] 29435
xxx:~$ 
** (nm-applet:29435): WARNING **: <WARN>  nma_dbus_device_properties_cb(): dbus returned an error.
  (org.freedesktop.NetworkManager.DeviceNotFound) The requested network device does not exist.



** (nm-applet:29435): WARNING **: <WARN>  nma_dbus_device_properties_cb(): dbus returned an error.
  (org.freedesktop.NetworkManager.DeviceNotFound) The requested network device does not exist.

```

Question: Do you have other versions of linux-restricted-modules installed? Because I have:
```

xxx:~$ aptitude search  linux-restricted-modules
p   linux-restricted-modules                                               - Generic Linux restricted modules.                                               
i A linux-restricted-modules-2.6.20-15-generic                             - Non-free Linux 2.6.20 modules on x86/x86_64                                     
i   linux-restricted-modules-2.6.20-16-generic                             - Non-free Linux 2.6.20 modules on x86/x86_64                                     
i   linux-restricted-modules-2.6.22-14-generic                             - Non-free Linux 2.6.22 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-16-386                                 - Non-free Linux 2.6.24 modules on 386                                            
p   linux-restricted-modules-2.6.24-16-generic                             - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-16-openvz                              - Non-free Linux 2.6.24 modules on OpenVZ Virtualization enabled kernel           
p   linux-restricted-modules-2.6.24-16-rt                                  - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-16-server                              - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-16-xen                                 - Non-free Linux 2.6.24 modules on Xen                                            
p   linux-restricted-modules-2.6.24-18-386                                 - Non-free Linux 2.6.24 modules on 386                                            
p   linux-restricted-modules-2.6.24-18-generic                             - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-18-openvz                              - Non-free Linux 2.6.24 modules on OpenVZ Virtualization enabled kernel           
p   linux-restricted-modules-2.6.24-18-rt                                  - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-18-server                              - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-18-xen                                 - Non-free Linux 2.6.24 modules on Xen                                            
p   linux-restricted-modules-2.6.24-19-386                                 - Non-free Linux 2.6.24 modules on 386                                            
i   linux-restricted-modules-2.6.24-19-generic                             - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-19-openvz                              - Non-free Linux 2.6.24 modules on OpenVZ Virtualization enabled kernel           
p   linux-restricted-modules-2.6.24-19-rt                                  - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-19-server                              - Non-free Linux 2.6.24 modules on x86/x86_64                                     
p   linux-restricted-modules-2.6.24-19-xen                                 - Non-free Linux 2.6.24 modules on Xen                                            
p   linux-restricted-modules-386                                           - Restricted Linux modules on 386.                                                
p   linux-restricted-modules-686                                           - Upgrade dummy package. Can be removed                                           
i A linux-restricted-modules-common                                        - Non-free Linux 2.6.24 modules helper script                                     
i A linux-restricted-modules-generic                                       - Restricted Linux modules for generic kernels                                    
p   linux-restricted-modules-k7                                            - Upgrade dummy package. Can be removed                                           
p   linux-restricted-modules-openvz                                        - Restricted Linux modules for openvz kernels                                     
p   linux-restricted-modules-rt                                            - Restricted Linux modules for rt kernels                                         
p   linux-restricted-modules-server                                        - Restricted Linux modules for server kernels                                     
p   linux-restricted-modules-xen                                           - Restricted Linux modules for xen kernels   
```

---

### Post by evillan on 2008-09-05
I installed wicd and it is finally working. 

Thank you for your help.

I still don't know what the problem with the nm-applet/driver/whatever was, but I guess that's okay.

---

### Post by Blackcabs on 2008-09-05
> **evillan said:**
> I installed wicd and it is finally working. 

Thank you for your help.

I still don't know what the problem with the nm-applet/driver/whatever was, but I guess that's okay.

Brilliant i am soooooo glad, that it finally worked out for you. Sorry it was so long winded,, but hey got there in the end..If you want to can you tick the THANKYOU box's in the posts for me.

Good luck for the future Blackcabs :guitar:

---

