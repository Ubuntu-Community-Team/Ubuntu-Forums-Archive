---
title: "no network after driver update"
date: 2023-01-08
forum: Networking &amp; Wireless
---

### Post by onthemark123 on 2023-01-08
Linux version: Ubuntu 22.04.1 LTS

My computer was experiencing issues relating to its graphic card, the screen (output) would disconnect, often requiring PC restart to fix.
The Graphics Card is relatively new, under 12 months old. My troubleshooting led to me updating the driver:
[Software & Updates] --> [Additional Drivers] : from <NVIDIA driver metapackage from nvidia-driver-515 (proprietary)> to <NVIDIA driver metapackage from nvidia-driver-525 (proprietary, tested)>

Once the installation was complete and the PC rebooted, network was no longer available.
> $ lshw -C network 
yields that my two network options (Network controller, Ethernet controller) are each **UNCLAIMED**.
As I understand it, this means there is no driver attached to it.

After several hours trying to fix it through the command console (and google search), I was able to connect a mobile device to the Linux PC and reinstall the {Network Manager} and the {Network Manager Gnome} .deb 
However, I am now at an impasse....

< $ sudo systemctl status NetworkManager.service
Loaded, enabled, active. Looks mostly fine, I will type out the problems that I see:
> CGroup: /system.slice/NetworkManager.service
--897 /usr/sbin/NetworkManager --no-daemon

> [date] [PC] NetworkManager[897]: <info> [1673197547.7746] failed to open /run/network/ifstate
> [date] [PC] NetworkManager[897]: <info> [1673198988.1248] failed to open /run/network/ifstate

Having looked through the directory /run/ I find only an empty [network] folder. No "ifstate" file or folder. The [NetworkManager] folder is also without value.


Please let me know how I might be able to resolve this issue... How do I fix the lack of Network?
Let me know if any further details from the PC are required. Again, it has no network (or bluetooth) connectivity - but I can file transfer from a mobile device.
Very frustrating. Appreciate the help.


[FONT=Verdana]$ lspci -nnk l grep 0280 -A3[/FONT]
[FONT=Verdana]> 29:00.0 Network controller [0200]: Intel Corporation Wi-Fi 6 AX200 [8086:2723] (rev 1a)[/FONT]
[FONT=Verdana]> DeviceName: RTL8111E Giga LAN[/FONT]
[FONT=Verdana]> Subsystem: Intel Corporation Wi-Fi 6 AX200NGW [8086:0084][/FONT]
[FONT=Verdana]> 2A:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:8125] (rev 04)[/FONT]

[FONT=Verdana]$ sudo modprobe iwlwifi && sudo dmesg l grep iwl[/FONT]
[FONT=Verdana]> modprobe: ERROR: ../libkmod/libkmod-module.c838 kmod_module_insert_module() could not find module by name='iwlwifi'[/FONT]
[FONT=Verdana]> modprobe: ERROR: could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)[/FONT]

---

### Post by chili555 on 2023-01-08
What is the result of:

```
uname -r
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```

Can you boot into an earlier kernel version at the GRUB menu and do the networking devices work there?

---

### Post by onthemark123 on 2023-01-09
uname -r
> 5.15.0-57-generic


sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
> dpkg-query: package 'linux-modules-extra-5.15.0.57-generic' is not installed and no information is available
> Use dpkg --info (= dpkg-deb --info) to examine archive files.


No such file or directory

I can access the GRUB menu by either mashing Esc on boot, or holding shift. Something worked.
Please can you advise the code to "boot into an earlier kernel version" and regarding the network devices?

grub> net_dhcp
> error: no network card found.

---

### Post by chili555 on 2023-01-09
When you get to the GRUB menu, it will look something like this:

[IMG]https://www.omgubuntu.co.uk/wp-content/uploads/2012/09/grub2-in-ubuntu.jpg[/IMG]

Select 'Advanced Options' and you will see a list of available kernel versions, similar to this:

[IMG]https://www.howtogeek.com/wp-content/uploads/2010/05/sshot169.png?height=200p&trim=2,2,2,2[/IMG]Select any option *other than* 5.15.0-57. Highlight it with the arrow keys and press Enter. After your system boots up, tell us if the networking devices are working. If so, open a terminal and do:

```
sudo apt update
sudo apt install -y linux-modules-extra-5.15.0.57-generic
```Reboot normally; that is, without accessing the GRUB menu. You should be all set.

---

### Post by onthemark123 on 2023-01-09
Thank you! Truly grateful for your help; finally I can get back to work.
 
After a long time trying to access the GRUB menu (on boot, hold shift and meticulously mash Esc. Too much takes to a text menu, not enough and boot will continue to Ubuntu load screen (-> reboot).
Just right, and reach the screen as shown above.

I loaded the 5.15.0-56-generic.
Network works. All good.
Install updates.

Reboot.
Just to add, it is .... 5.15.0-57-generic
Hyphen, not period. 
When rebooted, PC loaded into -57 version
$ uname -r
> 5.15.0-57-generic

$ sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
> Status: install ok installed

[SOLVED].

---

