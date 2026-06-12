---
title: "Cannot get wireless working for Atheros AR5007"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by botrain on 2008-10-03
Hello,

I'm quite new to ubuntu...I have almost everything figured out but my wireless. I have tried countless times to install madwifi different ways but nothing has worked. I have an Atheros AR5007 card running in my computer.

I have tried at least 5 different methods I found but none of them have worked! I have a wired connection but still no wireless...my wireless card isn't even being recognized by network manager.

---

### Post by botrain on 2008-10-03
Here's some more information on my system. I am running Hardy on my computer. It is the only OS installed.

After looking at this, maybe I'm not running the AR5007 after all? I don't know...I'm stumped...help please!


[PHP]00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/PHP]
  
[PHP]*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:48:3e:54
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0[/PHP]

---

### Post by azwar on 2008-10-03
there are several post for this issue, including mine. any way here some short note.

1. you should **install [B]build-essential** and avm-firmware[/B] from 
   the ubuntu cd
2. then go to restricted manager (ubuntu) or hardware driver (kubuntu),  
   then unmark the **_'Atheros Hardware Access Layer (HAL)'_**.
3. Restart your laptop.
4. download the madwifi driver at [B][U][http://snapshots.madwifi.org/special](http://snapshots.madwifi.org/special)
   /madwifi-nr-r3366+ar5007.tar.gz[/U][/B]
5. extract it eg. on your dektop. /home/user/desktop
6. go to the folder in terminal. cd /home/user/desktop/madwifi-
   nr-r3366+ar5007
7. type 'sudo su' and enter your password.
8. type '**make**'. and you should see he terminal printing the result until  it finished
9. type '**make install**'. you should see the terminal work and now patching
   the kernel.
10. finally type '**modprobe ath_pci**' to make atheros work during boot-up

now i think your atheros wifi can be use. tq.

---

### Post by botrain on 2008-10-03
Nope, that did not work...thank you for trying

Any other suggestions? This is getting to be frustrating

---

### Post by rbringh on 2008-10-03
Just what do you mean when you say "did not work"? Were there any errors during the process? Once this is done and you rebbot you should see a wireless icon on you main toolbar. From that point you need to select the wireless network you want to connect to. If you not have the wireless icon in place of the normal wired icon or do not see the wireless router listed than the driver dis not install properly. You may have had some error's in the install.

---

### Post by botrain on 2008-10-03
I can't seem to get it to change into the madwifi [PHP][/PHP]directory on my desktop

cd user/desktop/madwifi(blah, blah) isn't opening correctly

[PHP]no such file or directory[/PHP]

---

### Post by botrain on 2008-10-03
Any help getting into the madwifi directory error-free please?

---

### Post by acrichardt on 2008-10-03
I have an Atheros on my Toshiba and i had the same problem.  I have tried many methods, and in one instance i even lost my drivers.  I have tried this twice now and have had succes.  I followed it to the T, with the only change being where it mentions cd madwifi*r3862*, on my system the file was created as madwifi*r3861*.  Just pay attention how it untars.  

[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/) 

Give it a look.  I'm completely new to Linux and it was easy to follow.  Hope you get it working!

---

### Post by azwar on 2008-10-05
i think you have a problem navigating a folder in terminal. 

1. extract the madwifi tar where ever you like.

2. open the terminal, then type 'cd' and 'press spacebar' now you  
   drag the extracted madwifi folder to terminal and press enter'

3. now you are in the madwifi directory.

4. type 'sudo su' & password. type 'make', then 'make install' 
   finally 'modprobe ath_pci'. reboot your pc

5. just make sure that you have enable the network boot-up in the
   bios setting.

p/s= i'm too running atheros ar5007 on my laptop now. anyway just check your laptop manual whether its atheros ar5007 or ar5006 etc. if fails again, just use the ndiswrapper method to activate the wifi.

---

### Post by thewaytolite on 2009-01-06
These steps worked for me on my HP dv6707us

The device string displayed by lspci -v was as follows:

Code:

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

Code:

sudo apt-get install build-essential

The driver code will be downloaded with the subversion source code manager so I installed subversion:

Code:

sudo apt-get install subversion

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

Code:

cd ~

Created a directory:

Code:

mkdir madwifi

And changed to the new dirctory:

Code:

cd madwifi

Use subversion to download (checkout) a copy of the code:

Code:

svn co [http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

Code:

cd madwifi-hal-0.10.5.6

Run the make script to have the compiler build the driver:

Code:

make

Install the driver

Code:

sudo make install

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

Code:

sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

Code:

sudo modprobe ath_pci

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2

---

