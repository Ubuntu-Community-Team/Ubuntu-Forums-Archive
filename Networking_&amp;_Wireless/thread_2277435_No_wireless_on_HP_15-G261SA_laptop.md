---
title: "No wireless on HP 15-G261SA laptop"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by t0p on 2015-05-08
Well, it's finally happened to me.  After many years of Ubuntu-ing, I've bought a laptop that won't give me wireless in Ubuntu!  I have wireless when using Windows 8.1, but I stick in my Ubuntu 14.04 live usb and... no wireless. :(  

I've done some gooogling, and I haven't yet found a guide.  Does anyone know how to make wireless on the HP 15-G261SA?  A simple step-by-step guide would be grrreat (I'm no wizard, more like a Mickey Mouse).

Also, how do I discover what wireless chipset my HP 15-G261SA uses?  The Windows 8.1 Start screen is a chaotic mix of icons and pictures, no seeming rhyme and reason... I'm afraid I'm really regretting this purchase...

So, any nice ppl wanna help me out?  Undying gratitude etc...

---

### Post by Bucky Ball on 2015-05-09
*Thread moved to **Networking & Wireless**.*

Boot from live media, Try Ubuntu, open a terminal, input:

```
sudo lshw -C network
```

Post the output. Not all wireless is going to work in the live mode. Probably needs third-party drivers which you can install when the OS is installed.

On a live boot with an ethernet cable, can you get online ok? If so, check Additional Drivers.

---

### Post by t0p on 2015-05-22
```
ubuntu@ubuntu:~$ sudo lshw -C network  *-network               
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:36 memory:f0a00000-f0a07fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: 5c:b9:01:3f:a7:3d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:78 ioport:2000(size=256) memory:f0900000-f0900fff memory:f0800000-f0803fff
ubuntu@ubuntu:~$ 

```

From that I assume the wireless chipset is **BCM43142 802.11b/g/n**.

I do not have wired internet access.  To get on the net I expect I'll have to buy a usb 3G dongle... more expense... sigh.

Is there anywhere from where I could download the necessary drivers, using my Windows 8.1, and then slip them into Ubuntu?  Or some other way of achieving this without having to buy more hardware?

Cheers.

---

### Post by t0p on 2015-05-22
After some more googling I found [this]("https://thedubiousdisc.wordpress.com/2013/10/13/making-bcm43142-wireless-driver-work-on-debian/").  It's for Debian, but it might be good for Ubuntu too.  Haven't had a chance to check it out yet (no wired access) but when I get a chance I'll post back the results.

---

### Post by Hadaka on 2015-05-22
Hi, your link would not be the best choice for ubuntu.
your diver is built into the kernel already. When you get
your wired connection,open a terminal..ctl/alt/t and do..
```
sudo apt-get update
```
let this run to update all your systems goodies..
then your driver..
```
sudo apt-get install bcmwl-kernel-source 
```
you can also...no internet required...do this..
```
http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568
```

---

### Post by t0p on 2015-10-20
**Thank you Hadaka and Bucky Ball**.  I must confess, I have not yet tried your suggestions, as I can't figure out how to make a nice dual-boot Windows 8.1/Ubuntu 14.04.3.  Too much Windows-speak in tutorials (I have used Ubuntu for many years, but have next-to-no experience of Windows Oses).  Very sad: I have a shiny "new" computer and can't use it (well, I *could* use it in theory, but I'm sick of all the "OMG viruses and malwares if you don't update AV pop-ups), and I have only rudimentary idea of what they do to us non-Windowers...  and UEFI: why replace BIOS?  It did me good on my computers.  The upgrade to UEFI should have been properly compared with BIOS, and the replacement should have been (for careful home-users anyway) completely optional.

---

