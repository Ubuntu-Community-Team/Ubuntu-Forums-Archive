---
title: "Troube with video card"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by echo8172 on 2009-02-09
Alright guys Im a new user and very pleased with it, just wish I could use my graphics card for the other features.  I have a onboard intel gma 3100 and ubuntu doesnt have the driver for and I cant find it or even how to get it and install it.  If anyone has any idea how to get it and how to install it I would greatly appreciate it.  I Again Im a new user and trying to figure things out, love what u guys have done with it. oh and I have ubuntu 8


dmin@admin-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
03:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)

---

### Post by jbrown96 on 2009-02-09
The driver should be installed by default. Since it's not a closed-source driver, it doesn't appear in the Hardware Drivers Manager. Are you having a problem with the video card? Can you see the desktop?

---

### Post by echo8172 on 2009-02-09
Yeah I see the desktop and everything works good but I try to play games like warsow that come with synaptic and it says "your open gl doesnt support direct rendering" just thought I had to upgrade the driver, because I have played all this games on sucky windows. Just thought it didnt reconize my driver.  Again thank u for ur time..

---

### Post by jbrown96 on 2009-02-10
Your card doesn't support a recent version of opengl. It only has support for 1.5, which I doubt is enough. You probably need 2.0 or 2.1. From Intel's product [site]("http://http://www.intel.com/Products/Desktop/Chipsets/G33/G33-overview.htm")
> Intel® Graphics Media Accelerator 3100   	3D enhancements enable greater flexibility and scalability and improved realism with support for Microsoft DirectX* 9.0c Shader Model 2.0, OpenGL* 1.5. Intel® Graphics also support the highest levels of the Windows Vista* Aero experience.

There aren't any other Intel drivers; they are built into the kernel, so you have the best version, but they simply don't have the hardware.

---

