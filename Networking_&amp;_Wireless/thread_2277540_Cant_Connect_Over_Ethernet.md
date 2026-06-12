---
title: "Cant Connect Over Ethernet"
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by typos1 on 2015-05-09
I m trying to set up my new pc. I can get WiFi but not wired connection. It uses a Qualcom atheros AR928x wireless card, which also handle ethernet, from what I can work out. 

I ve spent ages googling it and read loads of posts but nothing I do seems to work. I ve never had to do this before because I ve always just plugged the cable in and it works.

Also if I plug the cable in when the pc is on it will freeze and I ll have to reboot, which is strange.

Some possibly useful terminal outputs :


```

typos@typos-desktop:~$ gksu gedit /etc/network/interfaces
(gedit:3573): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
typos@typosj-desktop:~$ gksu gedit /etc/network/interfaces
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
typos@typos-desktop:~$ sudo service network-manager restart
[sudo] password for typos: 
typos@typos~$ sudo service network-manager restart
typos@typos-desktop:~$ sudo restart network-manager
restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
typos@typos-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
typos@typos-desktop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:4d:1b:34:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-16-generic firmware=N/A ip=192.168.0.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fea00000-fea0ffff 
typos@typos-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:************  Mask:************
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304436 (304.4 KB)  TX bytes:304436 (304.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:4d:1b:34:da  
          inet addr:************  Bcast************  Mask:************
          inet6 addr: fe80::226:4dff:fe1b:34da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6076974 (6.0 MB)  TX bytes:520872 (520.8 KB)
typos@typos-desktop:~$ netstat -rn &#8211;
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         ***********    0.0.0.0         UG        0 0          0 wlan0
**********     0.0.0.0         **********     U         0 0          0 wlan0
**********     0.0.0.0         *************   U         0 0          0 wlan0

```

Thanks

EDIT: literally after hitting "start new thread" software updater said I had some updates and one is "DHCP client for automatically obtaining an IP address", maybe this will sort it ? Maybe its as a result of running one of the commands I just ran in the terminal ?

EDIT2: Made no difference, still cant connect.

---

### Post by SeijiSensei on 2015-05-09
It can also handle Ethernet? I've never seen any device like that.  Plus Linux doesn't see an Ethernet interface, just the wifi one.  Maybe it's some driver problem, but here's [someone in another thread]("http://ubuntuforums.org/showthread.php?t=2203079") with the same Atheros device.  His Ethernet connection uses a separate Realtek adapter.

---

### Post by typos1 on 2015-05-10
Well it says "capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless" in the terminal after typing "sudo lshw -C network" so I was thinking it could.

I cant see anything else that has ethernet capabilities listed in the output.

---

### Post by SeijiSensei on 2015-05-11
Does the device have an Ethernet jack?  I just don't see any Ethernet hardware in the lspci list at all.

---

### Post by typos1 on 2015-05-11
Yes it does, I took the cover off and found that it has a TRXcom TRC82442NL (China M1302) ethernet adaptor, searching "TRC82442NL linux" and "TRC82442NL ubuntu" brings up no results found in google :-(

---

### Post by SeijiSensei on 2015-05-11
Did it come with Windows?  If it has a Windows driver, you can use [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") to make it work with Linux.

---

### Post by typos1 on 2015-05-11
No it was OS free

---

### Post by SeijiSensei on 2015-05-11
Sounds like you'll probably need a [USB ethernet adapter]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&Description=usb%20to%20ethernet%20adapter&bop=And&N=8000&page=1") if you really want to make this work.

---

### Post by typos1 on 2015-05-11
I already have one from about 10 years ago and I have thought about using it, but as I understand it it will be slower than a proper ethernet adaptor, I cant find any windows drivers either. 

I think the answer is to send the stupid thing back - I ve spent a week trying to set it up and I cant get ethernet and the on board (AMD 6520G) APU graphics are appalling - I m not talking about gaming either, I m talkng about the way it renders the desktop with the proprietary drivers from AMD, its bad man, really bad, far worse than my 8 year old graphics card, even though the spcecs are actually pretty similar and I have 8Gb RAM on this new pc, leaving, like 7.3 Gb for the CPU. 

I m not getting an ethernet adaptor for a brand new pc. Its going back !

---

### Post by typos1 on 2015-05-11
Its soldered to the board and connected via PCB, would it still show up under an "lspci" command ?

---

### Post by SeijiSensei on 2015-05-12
> **typos1 said:**
> Its soldered to the board and connected via PCB, would it still show up under an "lspci" command ?

Yes.  It will be using the PCI bus.

One possibility that you can check right away is that the adapter needs to activated in the BIOS for some reason understood only by the manufacturer.

It does sound like getting a different machine might be the best solution.

---

### Post by typos1 on 2015-05-12
Yes, I have gone into the BIOS to look for something to turn it on, (although I cant figure out why a seller would want to turn it off before shipping). The seller says its a RealTek RTL8111E card, but I cant see it anywhere, a google revelas some problems using it and ubuntu, I dont know why it doesnt show up when I type "lspci".

---

