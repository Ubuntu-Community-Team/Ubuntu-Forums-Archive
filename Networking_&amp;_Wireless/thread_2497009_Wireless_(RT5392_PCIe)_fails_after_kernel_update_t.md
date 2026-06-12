---
title: "Wireless (RT5392 PCIe) fails after kernel update to 6.5.0-28-generic"
date: 2024-04-19
forum: Networking &amp; Wireless
---

### Post by AndrewMcNZ on 2024-04-19
Hi There

After a recent kernel update from 6.5.0-27-generic to 6.5.0-28-generic, the wireless on my Ubuntu 22.04 system has stopped working.

Here is some brief information about the wireless adapter from [FONT=Courier New]lspci[/FONT]:
```
Network controller: Ralink corp. RT5392 PCIe Wireless Network Adapter
Subsystem: D-Link System Inc RT5392 PCIe Wireless Network Adapter
```

I have used the [FONT=Courier New]wireless-info[/FONT] script to get details of my system running both the old (6.5.0-27) and new (6.5.0-28) kernels.
wireless-info for kernel 6.5.0-27-generic
[https://pastebin.ubuntu.com/p/KB47X97Pd6/](https://pastebin.ubuntu.com/p/KB47X97Pd6/)

wireless-info for kernel 6.5.0-28-generic
[https://pastebin.ubuntu.com/p/3cDWQbJbcj/](https://pastebin.ubuntu.com/p/3cDWQbJbcj/)

Currently, I am using the 6.5.0-27-generic kernel as a short term solution to have working wireless.
Can anyone provide any advice, or point me to any information, on how to resolve this wireless issue with the 6.5.0-28-generic kernel?

Cheers
Andrew Mc

---

### Post by praseodym on 2024-04-20
Try 

sudo modprobe -v rt2800pci

and afterwards 

dmesg | grep rt2

linux-modules is installed for kernel 28?

---

### Post by AndrewMcNZ on 2024-04-20
The output from: [FONT=Courier New]sudo modprobe -v rt2800pci[/FONT]
```
modprobe: FATAL: Module rt2800pci not found in directory /lib/modules/6.5.0-28-generic

```

There was no output (or the output was blank) from: [FONT=Courier New]sudo dmesg | grep rt2[/FONT]

Yes, [FONT=Courier New]linux-modules[/FONT] is installed for 6.5.0-28-generic, but not [FONT=Courier New]linux-modules-extra[/FONT] as shown below.
The output from: [FONT=Courier New]apt list --installed | grep linux-modules[/FONT]
```
linux-modules-6.5.0-26-generic/jammy-updates,jammy-security,now 6.5.0-26.26~22.04.1 amd64 [installed,auto-removable]
linux-modules-6.5.0-27-generic/jammy-updates,jammy-security,now 6.5.0-27.28~22.04.1 amd64 [installed,automatic]
linux-modules-6.5.0-28-generic/jammy-updates,jammy-security,now 6.5.0-28.29~22.04.1 amd64 [installed,automatic]
linux-modules-extra-6.5.0-26-generic/jammy-updates,jammy-security,now 6.5.0-26.26~22.04.1 amd64 [installed,auto-removable]
linux-modules-extra-6.5.0-27-generic/jammy-updates,jammy-security,now 6.5.0-27.28~22.04.1 amd64 [installed,automatic]

```

---

### Post by praseodym on 2024-04-20
Boot into 27 and install 28-extra

---

### Post by AndrewMcNZ on 2024-04-20
Installing [FONT=Courier New]linux-modules-extra-6.5.0-28-generic[/FONT] solved the problem! 
Thank you so much for the help.

Incidentally, this has also fixed an issue I was having with drivers for my Nvidia graphics card.

---

### Post by alexromer on 2024-04-22
> **AndrewMcNZ said:**
> Installing [FONT=Courier New]linux-modules-extra-6.5.0-28-generic[/FONT] solved the problem! 
Thank you so much for the help.

Incidentally, this has also fixed an issue I was having with drivers for my Nvidia graphics card.

Hi Andrew, 
I was confronted yesterday with a similar problem (or just the same).
I had no WLAN and the mouse pad stopped working (mouse over USB worked)

Starting Ubuntu with the 27er kernel everything works again and I also have a Nvidia graphic card and the driver gets messed up basically with each update.

Could you please explain how did you manually update the kernel?
And after that did you just need to start Ubuntu as usual without having to select anything special?

I tried with APT and apparently nothing was updated:

alessandro@alessandro-Legion-Y540-17IRH-PG0:~$ sudo apt install linux-modules-extra-6.5.0-28-generic
[sudo] password for alessandro: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
**linux-modules-extra-6.5.0-28-generic is already the newest version (6.5.0-28.29~22.04.1).**
linux-modules-extra-6.5.0-28-generic set to manually installed.
The following packages were automatically installed and are no longer required:
  libllvm13 libllvm13:i386 libnvidia-egl-wayland1 libvulkan1:i386 libwayland-client0:i386
  mesa-vulkan-drivers:i386
Use 'sudo apt autoremove' to remove them.
**0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.**
alessandro@alessandro-Legion-Y540-17IRH-PG0:~$ 





Thanks in advance!

---

### Post by alexromer on 2024-04-22
Anyway after a restart it works properly (mouse, WLAN and even Nvidia driver) without selectin any special option.
Thanks again, I would just undertand it a bit better.

P.S.

With the Nvidia driver I had (again) to select  a different one because a few things didn´t work (light control, night mode and first of all the wake up after sleep).

---

