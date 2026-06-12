---
title: "Bluetooth Realtek 8761B does not work on 20.04.1 LTS, kernel 5.9.8-050908-generic,"
date: 2020-11-14
forum: Networking &amp; Wireless
---

### Post by thang-tt2711 on 2020-11-14
my laptop uses 20.04.1 LTS, just bought usb bluetooth adapter Realtek 8761b (actually [https://www.orico.cc/us/download.html?skeyword=BTA-508](https://www.orico.cc/us/download.html?skeyword=BTA-508), it does not have linux driver, I download and see in the release notes the chip set is  Realtek 8761B, Bluetooth 5.x)

 I read this link [https://ubuntuforums.org/showthread.php?t=2448259&page=2&](https://ubuntuforums.org/showthread.php?t=2448259&page=2&)
 
 
 then I installed Ubuntu Mainline Kernel Installer from [https://github.com/bkw777/mainline](https://github.com/bkw777/mainline), version 1.0.12 and upgrade my kernel to stable version, now it is
 
 
 uname -sr

 Linux 5.9.8-050908-generic

 
 
 Then downloaded the package from MPOW:
[https://mpow.s3-us-west-1.amazonaws....+for+Linux.tgz]("https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz")
Unpacked, copied and renamed the rtl8761b_fw and rtl8761b_config files inside /lib/firmware/rtl_bt, adding the ".bin" extension.  

 
 
 /lib/firmware/rtl_bt$ ll

 ….

 -rw-r--r--  1 root root    25 Thg 11 13 18:13 rtl8761b_config.bin

 -rw-r--r--  1 root root    25 Thg 11 13 18:13 rtl8761b_fw.bin

 
 
 I reboot my system, plug my realtek adapter in and checked

 
 
 run this command lsusb

 
 
 output

 
 
 Bus 001 Device 002: ID 8087:8000 Intel Corp.  

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

 Bus 002 Device 003: ID 1bcf:2985 Sunplus Innovation Technology Inc. Laptop Integrated Webcam HD

 Bus 002 Device 002: ID 0bda:8771 Realtek Semiconductor Corp. Bluetooth Radio

 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 
 
 run this command

 sudo dmesg |egrep -i bluetooth

 
 
 output

 [    1.174836] usb 2-2: Product: Bluetooth Radio

 [    3.688392] Bluetooth: Core ver 2.22

 [    3.688411] Bluetooth: HCI device and connection manager initialized

 [    3.688415] Bluetooth: HCI socket layer initialized

 [    3.688416] Bluetooth: L2CAP socket layer initialized

 [    3.688419] Bluetooth: SCO socket layer initialized

 [    3.753789] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761

 [    3.754356] Bluetooth: hci0: RTL: rom_version status=0 version=1

 [    3.754358] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin

 [    3.754659] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_config.bin

 [    3.754818] Bluetooth: hci0: RTL: extension section signature mismatch

 [    5.781570] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
 [    5.781573] Bluetooth: BNEP filters: protocol multicast
 [    5.781577] Bluetooth: BNEP socket layer initialized
 [ 1893.127743] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
 [ 1893.128673] Bluetooth: hci0: RTL: rom_version status=0 version=1
 [ 1893.128675] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin

 [ 1893.128679] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_config.bin

 [ 1893.128682] Bluetooth: hci0: RTL: extension section signature mismatch
 [11189.657493] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
 [11189.658483] Bluetooth: hci0: RTL: rom_version status=0 version=1

 [11189.658485] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_fw.bin

 [11189.658520] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761b_config.bin

 [11189.658537] Bluetooth: hci0: RTL: extension section signature mismatch
 
 
 run this command
 sudo blueman-manager
 
 
 output

   
 blueman-manager version 2.1.2 starting

 blueman-manager 17.09.35 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
 blueman-manager 17.09.35 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting
 
 
 so there is no bluetooth adapter, when I go to Settings, click on Bluetooth, click on the button to toggle Bluetooth to ON, nothing happens, if I clicked to OFF, there is bluetooth icon displayed in the top right corner of the screen with a red dot mean something error, click on that bluetooth icon, I see a pulldown menu with grey-out options: Set Up New Device, Send Files To Device, Recent Connections, Devices, Adapters

 other options are select-able : Turn Bluetooth On, Local Services, Plugin, Exit

 
 
 please help me to identify why bluetooth adapter does not work, thanks

---

### Post by geekor on 2020-12-10
Hi, it works for me using [your driver]("https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz"). Just run follow:
> 
cd 20200610_LINUX_BT_DRIVER/
sudo make install INTERFACE=all


Ubuntu 20.04.1 LTS, 5.4.0-56-generic. ORICO BTA-508 (RTL8761B)

(Replug your bt adapter after installing the driver :P )

---

### Post by Vladimir2k9 on 2021-03-20
[COLOR=#24292E][FONT=-apple-system]When attempt download file [/FONT][/COLOR][https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz](https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz)[COLOR=#24292E][FONT=-apple-system] got error forbidden 403[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]Can someone upload and give link.[/FONT][/COLOR]

---

### Post by dcagatay on 2021-05-19
I found an updated version of the driver (I think) at the following link: [https://mpow.s3-us-west-1.amazonaws.com/20201202_mpow_BH456A_driver+for+Linux.7z](https://mpow.s3-us-west-1.amazonaws.com/20201202_mpow_BH456A_driver+for+Linux.7z)

I did exactly what geekor said in his [post]("https://ubuntuforums.org/showthread.php?t=2453631&p=14006235#post14006235") and the dongle started working.

Reference: [https://gist.github.com/rometsch/dfd24fb09c85c1ad2f25223dc1481aaa#gistcomment-3709943](https://gist.github.com/rometsch/dfd24fb09c85c1ad2f25223dc1481aaa#gistcomment-3709943)

---

### Post by fabio.vix on 2021-05-20
Hi!

I've tested the updated version [COLOR=#000000]**dcagatay** posted.. and it has worked here (Ubuntu Unity 20.04, kernel 5.8.0-48). 
It's a Orico BTA-508 Bluetooth dongle.

All i've done is unzip the file, entered on the "[/COLOR]20201202_LINUX_BT_DRIVER" folder and the used the cmd:  

sudo make install INTERFACE=all

An important note: I realized that if there's any space on the path to the folder, the **MAKE** will fail while compiling the driver. So, make sure that the path to the folder has no space on the names.

By the way, I was wondering why the mic from my Motorola Escape 220 BT headphone wasn't working after i've paired it sucessfuly with de dongle, and i've found it:

[https://askubuntu.com/questions/354383/headphones-microphone-is-not-working](https://askubuntu.com/questions/354383/headphones-microphone-is-not-working)

---

### Post by nasim.ansari on 2021-10-11
rtl8761b firmware is not shipped with Linux distribution if you see error below errors:


   Direct firmware load for rtl_bt/rtl8761b_fw.bin failed with error -2
   firmware file rtl_bt/rtl8761b_fw.bin not found


Execute below commands to install firmware.
> cd /tmp
# Download rtl8761b_config and rtl8761b_fw from [https://github.com/Realtek-OpenSource/android_hardware_realtek](https://github.com/Realtek-OpenSource/android_hardware_realtek)
wget [https://raw.githubusercontent.com/Realtek-OpenSource/android_hardware_realtek/rtk1395/bt/rtkbt/Firmware/BT/rtl8761b_config](https://raw.githubusercontent.com/Realtek-OpenSource/android_hardware_realtek/rtk1395/bt/rtkbt/Firmware/BT/rtl8761b_config)
wget [https://raw.githubusercontent.com/Realtek-OpenSource/android_hardware_realtek/rtk1395/bt/rtkbt/Firmware/BT/rtl8761b_fw](https://raw.githubusercontent.com/Realtek-OpenSource/android_hardware_realtek/rtk1395/bt/rtkbt/Firmware/BT/rtl8761b_fw)
mv rtl8761b_config /lib/firmware/rtl_bt/rtl8761b_config.bin
mv rtl8761b_fw /lib/firmware/rtl_bt/rtl8761b_fw
sudo modprobe btusb
sudo systemctl start bluetooth.service
hciconfig -a # will show that Bluetooth is up now


---

