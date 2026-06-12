---
title: "Gigabyte GN-WI05GS"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by beu on 2007-02-09
I've got a new laptop :lolflag: with a Gibabyte GN-WI05GS Wifi controler and it seems to be unsupported by now. I've looked for information in madwifi but is not listed there, and i can't find it listed in lspci output

Any help will be appreciate. Thanks

---

### Post by beu on 2007-02-15
The module that controls this Gigabyte GN-WI05GS Wifi chip is rt73 but, on ubuntu edgy, I can't make it work. Instead, I have used ndiswrapper installing the packet with the same name. I have followed this steps. Remember to install the [FONT="Courier New"]ndiswrapper[/FONT] packet:
```
$ sudo ndiswrapper -i /path/to/the/winodows/driver/driver_name.inf
```
After this, verify the hardware is present:
```
$ sudo ndiswrapper -l
```
Now, try to load the ndiswrapper module:
```
$ sudo modprobe ndiswrapper
```
Verify if the module has load successfully:
```
$ sudo lsmod|grep ndiswrapper
```
It should be in the output.

Make module alias:
```
$ sudo ndiswrapper -m
```

Verify the file [FONT="Courier New"]/etc/modules[/FONT] include [FONT="Courier New"]ndiswrapper[/FONT] at the bottom of the file:
```
$ sudo vi /etc/modules
```
And in other case insert it there. We make this in order to be loaded automatically at system boot.

Now you can set it up with the network icon in the system menu. I went through some troubles and i had to configure it manually. [FONT="Courier New"]network-manager[/FONT] didn't work OK for me.

With Ubuntu feisty the module loads automatically on installation, but in order to make it work properly, and I had to set it up manually disabling the roaming mode. Again, [FONT="Courier New"]network-manager[/FONT] didn't work OK.

---

