---
title: "trying to install file extracted from tar.gz"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by RochJer on 2011-06-28
I am trying to install file which is microcode for Intel Wireless 5100 AGN - filename is iwlwifi-5000-5.ucode but could not find a way to get wireless driver to be installed in ubuntu 11.04. I am doing this because I cant even get wireless connected with password/key. 

What can I do ?

---

### Post by Bachstelze on 2011-06-28
Do you know where the driver expects the firmware to be? When you run the [font=monospace]dmesg[/font] command, you should have an error message somewhere that tells you. Then just copy the firmware file to that location.

---

### Post by garvinrick4 on 2011-06-28
The iwlagn driver for intel cards does not stay connected in "N" capacity if router is set
only for "N" and not mixed with "G". It will if you use 3.0 kernel, has been fixed so you
need 3 all.deb, headers and image downloaded and installed link below:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc2-oneiric/")
[http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal](http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal)
Works in natty:
If you do not have 3.0 kernel need to make a config file:
```
sudo gedit /etc/modprobe.d/iwlagn.conf
```and insert this line and save.
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Times New Roman][SIZE=3]## The iwlagn driver is a kernel driver do not need anything else.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][SIZE=3]#You do have to make sure router is set right to wep or wpa and such for accepting password:[/SIZE][/FONT][/COLOR]

## Cannot get 3.0 rc4 kernel to work in Natty at this time just the 3.0 rc2, I find anyway.


[COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]

---

### Post by garvinrick4 on 2011-06-28
Post 2 would like to see this:
rick@rick-HP:~$ dmesg | grep iwlagn
```
[   23.513913] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   23.513917] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   23.514016] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.514025] iwlagn 0000:02:00.0: setting latency timer to 64
[   23.514057] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   23.532514] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   23.532516] iwlagn 0000:02:00.0: Device SKU: 0X9
[   23.532518] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   23.532918] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   23.533002] iwlagn 0000:02:00.0: irq 45 for MSI/MSI-X
[   23.832472] iwlagn 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138
[   36.847951] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 3
[   51.345412] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 8
[   58.050539] iwlagn 0000:02:00.0: Aggregation not enabled for tid 0 because load = 4
[   61.194012] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = c0:c1:c0:c6:0a:ec tid = 0
[ 1061.970120] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = c0:c1:c0:c6:0a:ec tid = 1
[ 2216.740097] iwlagn 0000:02:00.0: iwlagn_tx_agg_start on ra = c0:c1:c0:c6:0a:ec tid = 6
rick@rick-HP:~$ 

``````

```

---

### Post by RochJer on 2011-06-28
Ok here is the info you requested

[CODE]

jeremy@jeremy-Inspiron-1750:~$ dmesg | grep iwlagn
[   14.779520] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.779524] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   14.779636] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.779645] iwlagn 0000:0c:00.0: setting latency timer to 64
[   14.779679] iwlagn 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   14.801524] iwlagn 0000:0c:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   14.801527] iwlagn 0000:0c:00.0: Device SKU: 0Xb
[   14.802357] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.802442] iwlagn 0000:0c:00.0: irq 47 for MSI/MSI-X
[   14.815481] iwlagn 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[  229.642148] iwlagn 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[  229.642182] iwlagn 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fe004)
[  229.642190] iwlagn 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  229.642200] iwlagn 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[  229.735688] iwlagn 0000:0c:00.0: RF_KILL bit toggled to enable radio.
jeremy@jeremy-Inspiron-1750:~$

---

### Post by garvinrick4 on 2011-06-28
So did you check your setup with encryption type (AES) and or wep or wpa, wpa2 whatever
you use.

---

### Post by RochJer on 2011-06-29
Something must have happened - I installed kernel 3.0 like you suggested me to do and then I checked the network connections available, and all wireless connections are now gone, and no options to select my wireless connection. 

Sigh... wireless in 11.04 is pain in the butt. What options do I have ? Should I downgrade to 10.04 LTS ?

---

### Post by garvinrick4 on 2011-06-29
This will turn radio signal on.
```
sudo ifconfig wlan0 up
```Make sure your wireless is enabled with network applet in upper right.

This will reboot network manager copy and paste one at a time.
```

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

``````
rfkill list

```If say yes:
```
rfkill unblock all
```###I run the same driver "iwlagn" and it works has to be something in setup, I no it is real frustrating:
This will show it is in the kernels:
```
locate iwlagn
```
You did download and install like below? From second link I gave you:

1.) Download the debs from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc2-oneiric/")
 There are three packages need to install in this order: **linux-headers-*-all.deb**, **linux-headers-*-generic-*.deb**, and finally **linux-image-*.deb**.

---

### Post by RochJer on 2011-06-29
> **garvinrick4 said:**
> This will turn radio signal on. It didn't work out for me. 
```
sudo ifconfig wlan0 up
```Make sure your wireless is enabled with network applet in upper right. I checked and my wireless device is not enabled - I have done rfkill commands and the blocks are off. 

This will reboot network manager copy and paste one at a time.
```

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

``````
rfkill list

```If say yes:
```
rfkill unblock all
```###I run the same driver "iwlagn" and it works has to be something in setup, I no it is real frustrating:
This will show it is in the kernels:
```
locate iwlagn
```
You did download and install like below? From second link I gave you:

1.) Download the debs from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc2-oneiric/")
 There are three packages need to install in this order: **linux-headers-*-all.deb**, **linux-headers-*-generic-*.deb**, and finally **linux-image-*.deb**.

Done with all the installation and it's now installed - I double checked and it's all there. 

I have tried network manager stop/start commands. 

I did what you instructed me to do. I still do not see the wireless device, only my wired connection. I think I got the router and password stuff fixed, all I need to do is get the wireless device on network list which is not appearing at all.

---

### Post by garvinrick4 on 2011-06-29
> I think I got the router and password stuff fixed, all I need to do is  get the wireless device on network list which is not appearing at all.
Are the other networks around you showing there SSID's?

Does this show yours?
```
iwlist scan
```
What does this show below?? Is Network Manager and wireless say true.
```
gedit /var/lib/NetworkManager/NetworkManager.state
```
What did
```
locate iwlagn
```
 it say? Show your driver in the kernel?
When you ran below:
```
rfkill list 
```
what did it say?

Need to know what the code said so I know where you are at, post some of the results
copy and paste them here. You should be working will be something simple when we see it.
What does this say:
```
sudo lshw -C network
```

---

### Post by RochJer on 2011-06-30
[B]iwlist scan
[/B]
lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.





**gedit /var/lib/NetworkManager/NetworkManager.state**

[main]

NetworkingEnabled=true

WirelessEnabled=true

WWANEnabled=true



**locate iwlagn**

/etc/modprobe.d/iwlagn.conf

/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko

/lib/modules/3.0.0-0300rc2-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko

/usr/src/linux-headers-2.6.38-8-generic/include/config/iwlagn.h

/usr/src/linux-headers-3.0.0-0300rc2-generic/include/config/iwlagn.h



**rfkill list**

0: dell-wifi: Wireless LAN

	Soft blocked: no

	Hard blocked: no



**sudo lshw -C network **

  *-network UNCLAIMED     

       description: Network controller

       product: WiFi Link 5100

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:0c:00.0

       version: 00

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list

       configuration: latency=0

       resources: memory:f69fe000-f69fffff

  *-network

       description: Ethernet interface

       product: 88E8040 PCI-E Fast Ethernet Controller

       vendor: Marvell Technology Group Ltd.

       physical id: 0

       bus info: pci@0000:09:00.0

       logical name: eth0

       version: 13

       serial: a4:ba:db:95:ed:f7

       size: 100Mbit/s

       capacity: 100Mbit/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.71 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s

       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)

---

### Post by garvinrick4 on 2011-06-30
Unclaimed means no driver attached:

Open a terminal and start the module iwlagn:
```
sudo modprobe iwlagn
```

Does it now show a wlan0 most likely now:
```
iwconfig
```

---

### Post by RochJer on 2011-06-30
[B]sudo modprobe iwlagn
[/B]
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-0300rc2-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

[B]iwconfig
[/B]
lo        no wireless extensions.



eth0      no wireless extensions.

---

### Post by garvinrick4 on 2011-06-30
These are to see whats with your driver "iwlagn" post results please:

```
dmseg | grep iwlagn
```

```
lspci -nnk | grep -iA2 network
```

---

### Post by garvinrick4 on 2011-06-30
I have asked a user by the name of chili555 to help out with your problem. He is the best
I have seen in these forums at network cards and there drivers.

---

### Post by chili555 on 2011-06-30
Who? Me??? > FATAL: Error inserting iwlagn (/lib/modules/3.0.0-0300rc2-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)I hate the sound of that. Did you do this step?> Works in natty:
If you do not have 3.0 kernel need to make a config file:
Code:

sudo gedit /etc/modprobe.d/iwlagn.conf

and insert this line and save.
options iwlagn 11n_disable50=1 11n_disable=1

I wonder if those parameters are still valid in kernel version 3. Please run and post:```
modinfo iwlagn | grep parm:
```I suspect one of those two parameters is no longer available in 3.0.

I am a bit suspicious of installing an rc kernel; rc (release candidate) is unproven and probably unstable.

---

### Post by RochJer on 2011-06-30
Thank you Chili555 and garvinrick4 for the assistance. I will now try the steps that chili555 provided. 

The iwlagn.conf options line is already there - I checked in sudo gedit. 
[B]
modinfo iwlagn | grep parm:[/B]
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (bool)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)

---

### Post by garvinrick4 on 2011-06-30
>  
I am a bit suspicious of installing an rc kernel; rc (release candidate) is unproven and probably unstable.

I am running this kernel with iwlagn driver in this kernel and the "N" is working in 11.04.
In 11.10 iwlagn has worked in "N" since get-go.
Have installed at least 50 maybe closer to 100 installs on this system with iwlagn driver and
never had a problem with any Ubuntu install right out of box. I am perplexed at why OP
is having so much trouble. At start I believe was just a router and card set-up with encryption
wrong but now why module will not load I do not no why. OP does have other kernels most likely. 
Do not run anything below 11.04 now because router has to be set back to "G" and have to use the "iwlagn.conf" as you mentioned to remove N capabilities in 10.10 and below.

---

### Post by chili555 on 2011-06-30
As I suspected, this parameter no longer applies in 3.0xx-rc:> options iwlagn [COLOR="Red"]**11n_disable50=1**[/COLOR] 11n_disable=1Remove it and try again:```
sudo modprobe iwlagn
iwconfig
```If it still complains, try rebooting. Any improvement?

If we get it connected, we'll try to do N speeds if you wish.

---

### Post by garvinrick4 on 2011-06-30
chili555 with 3.0 kernel does not need the /etc/modprobe.d/iwlagn.conf file anymore.

---

### Post by chili555 on 2011-06-30
> **garvinrick4 said:**
> chili555 with 3.0 kernel does not need the /etc/modprobe.d/iwlagn.conf file anymore.I think that's probably correct but being a fraidy-cat, I'd like to fix one thing at a time. We can sudo rm it in an instant.

---

### Post by RochJer on 2011-06-30
**sudo modprobe iwlagn**

FATAL: Error inserting iwlagn (/lib/modules/3.0.0-0300rc2-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2011-06-30
Please do:```
sudo rm /etc/modprobe.d/iwlagn.conf
sudo modprobe iwlagn
dmesg | grep iwl
```If we're still stuck, I'm going to blame 3.0-xx-rc.

---

### Post by RochJer on 2011-06-30
Okay I did try the steps and checked the network applet on upper right - wireless appeared and I did try to get in wireless, it's now connected. Finally! I believe the issue is resolved. 

Much thanks !

---

### Post by chili555 on 2011-06-30
Please use thread tools at the top and mark Solved.

Glad it's working. Have fun!

---

### Post by garvinrick4 on 2011-06-30
Thanks chili555 for answering my message to help out.

---

