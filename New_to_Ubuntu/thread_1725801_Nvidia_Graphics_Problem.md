---
title: "Nvidia Graphics Problem"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by shubhbansal on 2011-04-10
Hey

I'm running Ubuntu 10.10 on a Sony VAIO with an NVIDIA Graphics Card.

I recently updated to the latest Nvidia drivers through System>Administration>Additional Drivers. 

Immediately after the update, there was a problem. When I rebooted into ubuntu, I'd get up to the Ubuntu Loading Screen, 2 dots would load, and then the entire screen would turn purple, and nothing more would happen. I "fixed" this by booting into recovery mode and reconfiguring Xorg settings to Default.

Aside-I should mention that the problem didn't start here. When I was installing ubuntu through a live USB, after the initial menu (where i selected Default Installation) I'd get a blank screen. To correct this I added "nomodeset" to the "quiet splash" line in the settings editor (as suggested by someone on the forum). After installing Ubuntu, I had to manually add "nomodeset" upon each boot, until I updated the drivers and set Xorg to default after which, oddly, I didn't have to.

Next, I checked out (System>Admin..>Nvidia X Server Settings) and got this message:
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.The output of nvidia-xconfig is

> WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'
And doing this just causes the purple screen error again on reboot.

Here's the output to lspci

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce G210M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
04:00.0 SD Host controller: Ricoh Co Ltd Device e822
04:00.1 System peripheral: Ricoh Co Ltd Device e230
04:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
04:00.4 SD Host controller: Ricoh Co Ltd Device e822
I can't enable Desktop effects, I'm getting choppy video, web pages are slightly blurry in places (as compared to windows) and I'd just like to use my Nvidia Card.
Can anyone help me with this?

Thanks.

---

### Post by TeoBigusGeekus on 2011-04-10
```
ERROR: Unable to write to directory '/etc/X11'.
```

Silly question I know, but have you run nvidia-xconfig with sudo?

---

### Post by shubhbansal on 2011-04-10
> **TeoBigusGeekus said:**
> ```
ERROR: Unable to write to directory '/etc/X11'.
```Silly question I know, but have you run nvidia-xconfig with sudo?

I did run it with sudo. I posted the wrong output earlier, edited the post...

---

### Post by shubhbansal on 2011-04-12
Anyone?

---

### Post by josephmills on 2011-04-12
ok I am real new to all of this but when you installed the driver was it there more then one driver available did you pick the bleeding edge one? try the other one if this is the case. hope this helps but like I said I am new to all of this.

---

### Post by wep940 on 2011-04-12
Do you have an xorg.conf file currently?  If so, post it back here.  I seem to remember that you have to run something like xorg-config or some such thing to actually create a xorg.conf file now.  After that, perhaps your nvidia config would run okay.

---

### Post by K_45 on 2011-04-12
Would this be a laptop with both an Intel chip and an Nvidia chip and you can switch between them? If it is, you cannot install any drivers as it will kill your display. I don't think there is any solution yet for this. I have a similar laptop.

---

### Post by shubhbansal on 2011-04-12
> ok I am real new to all of this but when you installed the driver was it  there more then one driver available did you pick the bleeding edge  one? try the other one if this is the case. hope this helps but like I  said I am new to all of this.     I installed it through System>Admin>Additional Drivers and there was only one option "NVIDIA accelerated graphics driver (version current)"

>          Do you have an xorg.conf file currently?  If so, post it back here.  I  seem to remember that you have to run something like xorg-config or  some such thing to actually create a xorg.conf file now.  After that,  perhaps your nvidia config would run okay.     I don't have one(although I have lots of xorg.conf.backup-xxxx and one xorg.conf.failsafe), and whenever I create one through nvidia-xconfig my computer reboots to a blank screen. Are you suggesting I should try just "sudo xconfig"?

>          Would this be a laptop with both an Intel chip and an Nvidia chip and  you can switch between them? If it is, you cannot install any drivers as  it will kill your display. I don't think there is any solution yet for  this. I have a similar laptop.     I don't think so... the output of lspci (visible in my first post) indicates just one chip. (nVidia Corporation GT218 [GeForce G210M] (rev a2))

---

### Post by K_45 on 2011-04-12
Try running:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then have a look here if that doesn't do it:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

which has some info on Xorg.

---

