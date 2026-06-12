---
title: "Intermittent network connectivity"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2006-07-24
I just installed Kubuntu Dapper 6.06, and now my internet connectivity goes in and out. It only comes back when I reboot, and not consistently. I reboot 2 times and it works, other then it stops. Sometimes I reboot 5 or 6 times, then it starts to work again, then it eventually stops.

My computer is set to get an IP from DHCP, which it does everytime even when I cannot access the internet. If I run dhclient from the console, it still has the problem. I can still talk to my gateway and ping it. However I cannot ping anything. The other computers on the network have no problem with the internet.

System Spec's:
> 
Motherboard: EPOX EP-9NPA+Ultra NF4 ULTRA RT

Video Card: Geforce 7200 GT 256MB DDR PCI Express x16 Video Card 
	Type VGA XFX|
	Model PVT45GUDF3

Sound: Built-in Sound on EPOX board - NVidia CK084

CPU: AMD Athlon 64 X2 4200+ Manchester 2000MHz FSB Socket 939 Dual Core
	Processor Model ADA4200BVBOX

RAM: CORSAIR XMS 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) Unbuffered System
	Memory Model CMX1024-3200C2PT
	Model #:CMX1024-3200C2PT

Distro: Ubuntu/Kubuntu 6.06, KDE 3.5.2.
Kernel: 2.6.15-25-686-smp

Keyboard: Standard 104-PC key english
Mouse: USB Optical Microsoft Mouse (the really common kind)


---

### Post by mips on 2006-07-24
None of the above info is applicable to your problem, maybe stuff like LAN card etc would help.

My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

