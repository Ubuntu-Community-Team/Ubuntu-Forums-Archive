---
title: "Blacklist"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by .:PiXi²:. on 2010-05-01
Hi
I've blacklisted a module to disable a device, but after rebooting, the device isn't disabled.
In the output of "lspci", the device still shows up, and in the output of "lsmod" the module still shows up.

Some details:
This is the device I want to disable:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Kernel driver in use: i915
	Kernel modules: i915

```
This is the line I've added to /etc/modprobe.d/blacklist.conf
```

blacklist i915

```

Please tell me what I'm doing wrong, thanks in advance.

---

### Post by Jon Monreal on 2010-05-02
Try adding the line
```
blacklist intel_agp
```
to the blacklist and then go to a terminal and type
```
sudo update-initramfs -u
```
and press enter.

Thanks.

---

### Post by .:PiXi²:. on 2010-05-02
I've added these lines to the blacklist.conf file:
```

blacklist intel-agp
blacklist agpgart-intel

```
Executed this:
```

sudo update-initramfs -u

```
Now the module (i915) doesn't get loaded, but the the device still shows up in the output of "lspci". Any further suggestions?

---

### Post by Jon Monreal on 2010-05-02
I'm not aware of any methods for removing a device from the output of "lspci". Is the fact that the card is recognized causing you problems?

---

### Post by .:PiXi²:. on 2010-05-02
Yes, because in Ubuntu it conflicts with my nVidia graphics card. When I install a driver for the nVidia graphics card, Ubuntu recognizes the Intel VGA controller first on startup and doesn't gives screen output.

---

### Post by Jon Monreal on 2010-05-03
Hello,

Could you check your BIOS and see if there is a way to disable the  onboard card from there? If there isn't, just say so.

Thanks.

---

### Post by .:PiXi²:. on 2010-05-04
There's no option in the BIOS to disable the device.
Is there another way in Ubuntu to disable of just let the kernel "ignore" a piece of hardware?

---

### Post by Jon Monreal on 2010-05-04
Do you know what model the motherboard is? Most should have the ability to disable an onboard card.

Also, you could try
```
dpkg-reconfigure xserver-xorg
```
to try to fix the output problem.

---

