---
title: "problems with wireless router"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by sketchme on 2011-02-26
I am having a problem with my new wireless router. It says its Linux compatible with the drivers. Ive unzipped them on the computer but don't know how to install in the command line.   Im currently running dual system with windows 7 but I dont think this is part of the problem.

---

### Post by sketchme on 2011-02-26
Ok I have the readme page frommy driver I have for it can you guys tell me what to do for it. If you need more from it just ask.  Build Instructions:   ====================  1> $tar -xvzf DPB_RT3070_Linux_STA_x.x.x.x.tgz     go to "./DPB_RT3070_Linux_STA_x.x.x.x" directory.      2> In Makefile 	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX" 	 define the linux kernel source include file path LINUX_SRC 	 modify to meet your need.  3> In os/linux/config.mk  	define the GCC and LD of the target machine 	define the compiler flags CFLAGS 	modify to meet your need. 	** Build for being controlled by NetworkManager or wpa_supplicant wext functions 	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. 	   => #>cd wpa_supplicant-x.x 	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d 	** Build for being controlled by WpaSupplicant with Ralink Driver 	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'. 	   => #>cd wpa_supplicant-0.5.7 	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d  4> $make 	# compile driver source code 	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event" 	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c  5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat      6> load driver, go to "os/linux/" directory.     #[kernel 2.4]     #    $/sbin/insmod rt3070sta.o     #    $/sbin/ifconfig ra0 inet YOUR_IP up              #[kernel 2.6]     #    $/sbin/insmod rt3070sta.ko     #    $/sbin/ifconfig ra0 inet YOUR_IP up  7> unload driver         $/sbin/ifconfig ra0 down 	$/sbin/rmmod rt3070sta

---

### Post by sketchme on 2011-02-26
I forgot in the original post that the network adapter I used is ASUS 802.11n.  ok I used the terminal and found out that my wireless router is not even recognized on Ubuntu. It only shows my Ethernet connection. I know the power is on  the network adapter because Im using it now on windows 7. I hope this helps when some one resopnds

---

### Post by josephmills on 2011-02-26
OK  try this first Go to System>Addmin>additional drivers  and see if you driver is there if not. Go to your terminal and type in ifconfig  copy and past that to the forum and also Ispci copy and paste that also.

---

### Post by sketchme on 2011-02-26
ok here is iconfig  :~$ ifconfig eth0      Link encap:Ethernet  HWaddr bc:ae:c5:36:8c:8d             UP BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           Interrupt:19 Base address:0x8c00   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:16 errors:0 dropped:0 overruns:0 frame:0           TX packets:16 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by sketchme on 2011-02-26
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13) 00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13) 00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13) 00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13) 00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13) 00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13) 00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13) 00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13) 00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13) 00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller 00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) 00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller 00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller 00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller 01:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9123 PCIe SATA 6.0 Gb/s controller (rev 11) 02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) 03:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series] 03:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series] 05:00.0 SATA controller: JMicron Technology Corp. JMB362 AHCI Controller (rev 10) 07:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10) 07:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05) ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05) ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05) ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05) ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05) ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05) ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05) ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05) ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05) ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05) ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05) ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05) ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05) ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05) ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05) ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05) ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05) ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05) ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)

---

### Post by josephmills on 2011-02-26
try this shut down the computer  unplug everything I mean everything from your tower manually hard reset the router. Plug everything back in. start up ubuntu and go to the terminal and type in lspci again and look to see if your wireless card is there now. If you already know your wireless card please tell us what it is. Also your wireless is working fine on your windoz partition?

---

### Post by sketchme on 2011-02-26
> **josephmills said:**
> try this shut down the computer  unplug everything I mean everything from your tower manually hard reset the router. Plug everything back in. start up ubuntu and go to the terminal and type in lspci again and look to see if your wireless card is there now. If you already know your wireless card please tell us what it is. Also your wireless is working fine on your windoz partition?

 Im going to try that. My wireless router on my windows partition is working fine. My adapter is called ASUS 802.11n Network adapter.

---

### Post by josephmills on 2011-02-26
> **sketchme said:**
> Im going to try that. My wireless router on my windows partition is working fine. My adapter is called ASUS 802.11n Network adapter.


ok I need just a little more info after you do what I told you to do go to termanial and type in lspci  this will tell us the hard ware that the kernel is seeing. if the kernel is not seeing your wireless card (like last time )we will know where to go from there.

---

### Post by 3rdalbum on 2011-02-26
The problem is not the router. The router communicates with the devices on the network in a completely OS-neutral way.

The problem is the wireless networking card, which by the looks of it is based around the RT3070 driver. Ubuntu actually already has a driver for this card, but there's a little bug that causes an inappropriate driver to be loaded for the card instead.

There's a workaround:

Edit the /etc/modprobe.d/blacklist.conf file by hitting Alt-F2 and typing this:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

This opens a text editor. Put this at the end of the file:

```
blacklist rt2800usb
```

Save your changes and close. Shut down the computer fully, and start it up again. Your wireless should work now.

**DO NOT attempt to install any drivers until you have tried my suggestion!**

---

### Post by sketchme on 2011-02-26
Ok I tried it... I couldnt figure out were you wanted me to put the first part of the code but I did put the botom on at the bottem and it didnt seem to work.   > **3rdalbum said:**
> The problem is not the router. The router communicates with the devices on the network in a completely OS-neutral way.

The problem is the wireless networking card, which by the looks of it is based around the RT3070 driver. Ubuntu actually already has a driver for this card, but there's a little bug that causes an inappropriate driver to be loaded for the card instead.

There's a workaround:

Edit the /etc/modprobe.d/blacklist.conf file by hitting Alt-F2 and typing this:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```This opens a text editor. Put this at the end of the file:

```
blacklist rt2800usb
```Save your changes and close. Shut down the computer fully, and start it up again. Your wireless should work now.

**DO NOT attempt to install any drivers until you have tried my suggestion!**

---

### Post by sketchme on 2011-02-26
I also tried lspci and I still couldn't find the router in it

---

### Post by 3rdalbum on 2011-02-26
> **sketchme said:**
> Ok I tried it... I couldnt figure out were you wanted me to put the first part of the code but I did put the botom on at the bottem and it didnt seem to work.

Did you put the blacklist line into the blacklist.conf file? If you typed "blacklist rt2800usb" into the terminal, then you have done it wrong and you need to re-read what I wrote.

---

### Post by 3rdalbum on 2011-02-26
> **sketchme said:**
> I also tried lspci and I still couldn't find the router in it

You won't find your router there. You are trying to connect wirelessly, is that correct? If so then your router itself will not appear in lsusb, lshw, or lspci. Your wireless card, however, might appear in lsusb.

---

### Post by sketchme on 2011-03-01
This is what gksudo gedit /etc/modprobe.d/blacklist.conf did I change it right. Also I know its not a router.I was just really tierd when I typed it.  # This file lists those modules which we don't want to be loaded by  # alias expansion, usually so some other driver will be loaded for the  # device instead.   # evbug is a debug tool that should be loaded explicitly  blacklist evbug   # these drivers are very simple, the HID drivers are usually preferred  blacklist usbmouse  blacklist usbkbd   # replaced by e100  blacklist eepro100   # replaced by tulip  blacklist de4x5   # causes no end of confusion by creating unexpected network interfaces  blacklist eth1394   # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much  # hardware on its own (Ubuntu bug #2011, #6810)  blacklist snd_intel8x0m   # Conflicts with dvb driver (which is better for handling this device)  blacklist snd_aw2   # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)  blacklist i2c_i801   # replaced by p54pci  blacklist prism54   # replaced by b43 and ssb.  blacklist bcm43xx   # most apps now use garmin usb driver directly (Ubuntu: #114565)  blacklist garmin_gps   # replaced by asus-laptop (Ubuntu: #184721)  blacklist asus_acpi   # low-quality, just noise when being used for sound playback, causes  # hangs at desktop session start (Ubuntu: #246969)  blacklist snd_pcsp   # ugly and loud noise, getting on everyone's nerves; this should be done by a  # nice pulseaudio bing (Ubuntu: #77010)  blacklist pcspkr   # EDAC driver for amd76x clashes with the agp driver preventing the aperture  # from being initialised (Ubuntu: #297750). Blacklist so that the driver  # continues to build and is installable for the few cases where its  # really needed.   blacklist amd76x_edac  blacklist rt2800usb

---

