---
title: "Wired connection stopped working after ATI fglrx install"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by shandiddy on 2008-09-22
Hi,
I have been using Ubuntu for a few years. 6.06,7.10 recently I tried to install 8.04. Particularly Linux Mint 5 (elyssa 8.04). On a completely fresh install I followed this guide [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide) to install my ATI Radeon HD2400 AGP. It worked like a charm compiz in all its glory worked perfectly. My dual monitor setup worked perfect everything was awesome. But after I restarted my computer the computer would not get an IP address. Although the network icon said it was connected. I checked and the network device is still there. But it will not connect.
So I put in the liveCD and the internet works perfectly. I did a fresh install and repeated the installation and again the same thing happened. ATI drivers work, but the internet stops working.
Also, my Linux laptop or PC has ever frozen, but after installing this driver my computer freezes almost every session.
Thanks

Computer spec (as I can remember, if it helps)
Intel P4 1.6GHZ
Biostar MoBo with onboard NIC
Brand new WD HDD 80G
ATI Radeon HD2400 AGP

---

### Post by shandiddy on 2008-09-23
Update:

So I went and downloaded regular Ubuntu 8.04 lts.

I did exactly the same procedure on a fresh install. And exactly the same thing happened.  Everything works, but the network card stops connecting.  My wired Windows XP PC works perfectly so there's nothing wrong with the router.  
I installed these packages from .deb if anyone knows if any of these conflicts with the NIC.

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r

fglrx-amdcccle_8.532-0ubuntu1_i386.deb
fglrx-kernel-source_8.532-0ubuntu1_i386.deb
fglrx-modaliases_8.532-0ubuntu1_i386.deb
xorg-driver-fglrx_8.532-0ubuntu1_i386.deb
xorg-driver-fglrx-dev_8.532-0ubuntu1_i386.deb

those .deb files came from ati-driver-installer-8-9-x86.x86_64.run off of the ati.amd website.

I am very perplexed as to why the video card driver affects the NIC. My ATI video card works perfectly though. But no internet.

---

### Post by Iowan on 2008-09-23
Back to basics: post results of **ifconfig** (**iwconfig ** for wireless) and contents of **/etc/network/interfaces**.

---

### Post by shandiddy on 2008-09-24
Ok so I copied my Ifconfig and /etc/network/interfaces before and after I installed the ATI 8.9 driver.
**This is before I installed the ATI driver**

> Ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:b8:36:fe  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:95ff:feb8:36fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:809068 (790.1 KB)  TX bytes:81043 (79.1 KB)
          Interrupt:5 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69900 (68.2 KB)  TX bytes:69900 (68.2 KB)



/etc/network/interfaces
auto lo
iface lo inet loopback


**This is after I installed the ATI driver**

> Ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:b8:36:fe  
          inet6 addr: fe80::207:95ff:feb8:36fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:22 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xd400 

eth0:avahi Link encap:Ethernet  HWaddr 00:07:95:b8:36:fe  
          inet addr:169.254.9.40  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          Interrupt:5 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80548 (78.6 KB)  TX bytes:80548 (78.6 KB)



/etc/network/interfaces
auto lo
iface lo inet loopback

I do NOT have any WiFi connection on this computer. Thanks for your help. Greatly appreciated.

---

### Post by shandiddy on 2008-09-25
I have heard many problems with **eth0:avahi**.  It just suddenly showed up after I installed the ATI driver.

I tried this [http://omingo.zorngrid.com/]("http://omingo.zorngrid.com/") but it did not fix this problem.

---

### Post by shandiddy on 2008-09-27
does the **eth0:avahi** driver/service get installed with one of these packages ? **build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r**

Could i just not install one of these packages?

I have stopped the avahi-daemon....not helping.
I have stopped using the network-tools program...not helping.

Anyone help with this problem?

---

