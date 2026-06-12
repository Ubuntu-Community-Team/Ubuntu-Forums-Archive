---
title: "Wireless Adapter No Longer Recognized After Update"
date: 2023-08-06
forum: Networking &amp; Wireless
---

### Post by judahwolf on 2023-08-06
I just did a standard kernel update and now suddenly my wireless does not work any more, with an error "no wireless adapter recognized".

Here were things tried:

```
zev@zev-HP-Laptop-15-dy1xxx:~$ sudo lshw -C network[sudo] password for zev: 
  *-network UNCLAIMED       
       description: Network controller
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:80500000-8050ffff

```

So it can see the RTL8821CE adapter here, but it won't engage. I tried doing the steps to re-install the driver and got this:

```
zev@zev-HP-Laptop-15-dy1xxx:~/rtl8821ce$ sudo ./dkms-install.shAbout to run dkms install steps...
Error! DKMS tree already contains: rtl8821ce-v5.5.2_34066.20200325
You cannot add the same module/version combo more than once.


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area...
'make' -j8 KVER=6.2.0-26-generic.......(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8821ce: v5.5.2_34066.20200325 not found
Error! Bad return status for module build on kernel: 6.2.0-26-generic (x86_64)
Consult /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/make.log for more information.


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area...
'make' -j8 KVER=6.2.0-26-generic.......(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8821ce: v5.5.2_34066.20200325 not found
Error! Bad return status for module build on kernel: 6.2.0-26-generic (x86_64)
Consult /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/make.log for more information.
Finished running dkms install steps.

```

To no effect. I'm not really sure what to do next. It is pretty annoying when just doing a regular old "apt dist-upgrade" breaks wifi.

[COLOR=#232629][FONT=-apple-system][FONT=inherit]The wireless diagnosis script gives this:[/FONT]
[FONT=inherit][https://pastebin.ubuntu.com/p/KY9cTt7YZD/](https://pastebin.ubuntu.com/p/KY9cTt7YZD/)[/FONT]


[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by ajgreeny on 2023-08-06
I assume you are running Ubuntu 22.04 with the hwe kernel series which updated a few days ago and has caused some problems.

For the moment try booting to the previous kernel from the **grub menu -Advanced Options** which will show all available kernels on your system.

In future please give us all the details of your hardware when needing help of this sort as it makes answering much easier.
You can either use command ```
inxi -Fzx
``` or run the system-info script (see my signature below) both of which will give us a lot of useful information.

---

### Post by jeremy31 on 2023-08-06
I would guess the source code from github didn't support the 6.2 kernel when the user downloaded it.
My guess is that they will need to uninstall the current version and completely remove it from dkms, possibly manually remove the /usr/src/rtl8821ce-v5.5.2_34066.20200325 directory then go into the rtl8821ce directory in home folder, open in terminal and run a git pull to download the recent changes and then try the install script

---

