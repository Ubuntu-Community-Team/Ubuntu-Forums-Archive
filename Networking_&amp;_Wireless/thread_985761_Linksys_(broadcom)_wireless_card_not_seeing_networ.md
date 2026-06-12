---
title: "Linksys (broadcom) wireless card not seeing networks"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by greengunboat on 2008-11-17
Hello,
New to linux (Ubuntu 8.10), but I finally made the switch from windows. I have a Linksys wireless card plugged into a pci slot. Ubuntu doesnt give me any hardware driver errors, and it seems to recognize the card, but it can't find my wireless network.

The network controller is:

Broadcom Corp BCM4303 802.11b Wireless LAN

iwconfig eth0 returns "no wireless extions"

iwlist scan returns "eth0 doesnt support scanning"

Any help is greatly appreciated...

---

### Post by pytheas22 on 2008-11-17
If you go to System>Administration>Hardware Drivers, there should be an option to enable your wireless card.

If that doesn't work, try running this command (which manually does what the Hardware Drivers utility is supposed to do), then reboot:
```

sudo apt-get install b43-fwcutter
```

If you still have no wireless after running that command and rebooting, please post the output of the following commands:
```

lspci -nn | grep -i broadcom
lshw -C Network
ls /lib/firmware
uname -m
dmesg | grep -e wlan -e b43
```

---

### Post by greengunboat on 2008-11-18
Tried the hardware drivers... it just says something about my video card and nothing else.

Tried the sudo apt-get install b43-fwcutter and it returns "couldnt find package"

So I ran the commands and got this:

sudo apt-get install b43-fwcutter

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter


**lspci -nn | grep -i broadcom**
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)

**lshw -C Network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 3CSOHO100B-TX 910-A01 [tulip]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 31
       serial: 00:0a:48:09:8e:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:1d:20:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:08:fe:ed:c4:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**ls /lib/firmware**
2.6.27-7-generic                    dvb-usb-vp7045-01.fw
acx                                 dvb-usb-wt220u-02.fw
aic94xx-seq.fw                      dvb-usb-wt220u-fc03.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502_3com-wpa.bin         ipw2100-1.3.fw
atmel_at76c502.bin                  ipw2100-1.3-i.fw
atmel_at76c502d.bin                 ipw2100-1.3-p.fw
atmel_at76c502d-wpa.bin             ipw2200-bss.fw
atmel_at76c502e.bin                 ipw2200-ibss.fw
atmel_at76c502e-wpa.bin             ipw2200-sniffer.fw
atmel_at76c502-wpa.bin              isl3877
atmel_at76c503-i3861.bin            isl3886
atmel_at76c503-i3863.bin            isl3887usb_bare
atmel_at76c503-rfmd-0.90.2-140.bin  isl3890
atmel_at76c503-rfmd-acc.bin         isl3890usb
atmel_at76c503-rfmd.bin             iwlwifi-3945-1.ucode
atmel_at76c504_2958-wpa.bin         iwlwifi-4965-1.ucode
atmel_at76c504a_2958-wpa.bin        iwlwifi-4965-2.ucode
atmel_at76c504.bin                  iwlwifi-5000-1.ucode
atmel_at76c504c-wpa.bin             ql2100_fw.bin
atmel_at76c505a-rfmd2958.bin        ql2200_fw.bin
atmel_at76c505-rfmd2958.bin         ql2300_fw.bin
atmel_at76c505-rfmd.bin             ql2322_fw.bin
atmel_at76c506.bin                  ql2400_fw.bin
atmel_at76c506-wpa.bin              rt2561.bin
bcm2033-fw.bin                      rt2561s.bin
bcm2033-md.bin                      rt2661.bin
dvb-fe-or51132-qam.fw               rt73.bin
dvb-fe-or51132-vsb.fw               v4l-cx23418-apu.fw
dvb-fe-or51211.fw                   v4l-cx23418-cpu.fw
dvb-fe-tda10046.fw                  v4l-cx23418-dig.fw
dvb-ttpci-01.fw                     v4l-cx2341x-dec.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-enc.fw
dvb-usb-bluebird-01.fw              v4l-cx2341x-init.mpg
dvb-usb-dib0700-1.10.fw             v4l-cx25840.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dtt200u-01.fw               zd1201-ap.fw
dvb-usb-tvwalkert.fw                zd1201.fw
dvb-usb-umt-010-02.fw               zd1211
dvb-usb-vp702x-01.fw

**uname -m**
i686

 **dmesg | grep -e wlan -e b43**
[    3.072356] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.159111] b43legacy-phy0: Broadcom 4301 WLAN found
[   13.182685] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   13.182712] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   13.204048] b43legacy-phy0 debug: Radio initialized
[   29.292316] input: b43legacy-phy0 as /devices/virtual/input/input7
[   29.368089] firmware: requesting b43legacy/ucode2.fw
[   29.405805] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode2.fw" not found or load failed.
[   29.405821] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[   29.473830] input: b43legacy-phy0 as /devices/virtual/input/input8
[   29.516148] firmware: requesting b43legacy/ucode2.fw
[   29.527318] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode2.fw" not found or load failed.
[   29.527335] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

---

### Post by pytheas22 on 2008-11-18
Try going to System>Administration>Software Sources.  Under the 'Ubuntu Software' tab, make sure that all of the boxes are checked.  Then close the window.  You should be asked about reloading the sources list; say yes.

Then try running again:

```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

This should take care of it--all that you need is to install firmware.  If after rebooting the wireless still won't work, please post the output of:
```

dmesg | grep -e b43 -e wlan
ls /lib/firmware
```

---

### Post by greengunboat on 2008-11-18
Under the software tab... all of it is checked.

I tried running the commands.
The sudo get-apt update appears to try to get some stuff online and fails because the internet isn't hooked up.

The sudo apt-get install b43-fwcutter tries to get online as well and fails.

On my software tab... all the boxes are checked, and then it give me another box that says 'Installable from CDROM'
and there is another check box(that is checked) and it says "Cdrom with Ubuntu 8.10 'Intrepid Ibex'

---

### Post by pytheas22 on 2008-11-18
Sorry, I thought you were connected via ethernet to the Internet.  If it's possible to get connected that way, that would be the best thing; get online and then follow the steps in post #4.

If it's not possible for you to get the machine online without using the wireless, please follow these steps to install firmware:

1. on a machine with Internet access, download [this file]("http://burnthesorbonne.com/files/b43_firmware.tar.gz") and save it to a USB drive or CD
2. transfer that file to your Ubuntu computer and save it on the desktop there
3. run these commands:

```
cd ~/Desktop
sudo cp b43_firmware.tar.gz /lib/firmware
cd /lib/firmware
sudo tar -xzvf b43_firmware.tar.gz
```

This should get the firmware where it needs to be.  After completing these steps, reboot.  If the wireless still doesn't work then, please post the output of:
```

dmesg | grep -e b43 -e wlan
ls /lib/firmware
```

---

### Post by greengunboat on 2008-11-18
Hey man, it works great now. Thanks for your help.

---

### Post by Asbj.S. on 2009-11-17
> **pytheas22 said:**
>   If the wireless still doesn't work then, please post the output of:
```

dmesg | grep -e b43 -e wlan
ls /lib/firmware
```

Allow me to jump in here, as I have the same (or similar) problem as the original poster.

I did follow the instructions given, I installed the package b43fwcutter (apt-get install b43-fwcutter). During installation I answered yes to the question to download firmware.
I then rebooted.

I still do not have wireless working, though.  dmesg claims that the microcode is not responding (see below).  I do seem to have firmware installed in /lib/firmware, see further below.

Any advice on how to proceed is most welcome.

With kind regards
Asbjørn Sæbø



root@snegle:~# dmesg |grep b43
[    2.001082] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.707979] b43legacy-phy0: Broadcom 4301 WLAN found
[    8.732029] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[    8.732071] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[    8.756039] b43legacy-phy0 debug: Radio initialized
[   17.036093] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   17.606567] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   17.637649] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   18.780035] b43legacy-phy0 ERROR: Microcode not responding
[   18.780118] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[   20.964033] b43legacy-phy0 ERROR: Microcode not responding
[   20.964043] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

root@snegle:~# ls /lib/firmware/b43legacy/
a0g0bsinitvals2.fw  a0g0initvals5.fw    b0g0bsinitvals2.fw  b0g0initvals5.fw  ucode11.fw  ucode5.fw
a0g0bsinitvals5.fw  a0g1bsinitvals5.fw  b0g0bsinitvals5.fw  pcm4.fw           ucode2.fw
a0g0initvals2.fw    a0g1initvals5.fw    b0g0initvals2.fw    pcm5.fw           ucode4.fw

---

### Post by pytheas22 on 2009-11-17
Asbj.S.: I've never seen that before, and unfortunately googling your error message brings up nothing besides this thread and the b43 source code.

It's possible that the firmware you downloaded when installing the b43-fwcutter package got corrupted in transit and is not working because of that.  So my first suggestion would be to manually remove the b43 firmware in /lib/firmware, then download a fresh copy from [http://burnthesorbonne.com/files/b43_firmware.tar.gz](http://burnthesorbonne.com/files/b43_firmware.tar.gz) and put it in the place of the old firmware.  Hopefully this will solve the problem.  The md5 sum for that file is 12eea4e227134ec77fb5b8260f8e106d in case you want to be sure that it downloads properly.

If you need more specific instructions on how to do what I recommend in the paragraph above, let me know and I'll write out the commands.

Also, which version of Ubuntu are you on and what's your kernel architecture (if you don't know, just post the output of the command "uname -a")?

---

### Post by Asbj.S. on 2009-11-18
> **pytheas22 said:**
> Asbj.S.: I've never seen that before, and unfortunately googling your error message brings up nothing besides this thread and the b43 source code.

It's possible that the firmware you downloaded when installing the b43-fwcutter package got corrupted in transit and is not working because of that.



Actually, the symptoms have changed now.  I do not now exactly when, but I have done a new fresh install (the previous install was also fresh) and an apt-get update; apt-get upgrade in between.  After that, the error message about the micro code has disappeared.  But I am still not able to get the wireless up.  The "Turn on wireless" (or whater it is called in english) menu selection in the network manager is greyed out and not selectable.

I am starting to think that the problem may be that the radio itself is turned off.
There is no light in the wireless LED, and dmesg gives the messages below.
Note the 
[   78.840059] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

The button to turn the radio off and on is Fn-F2.  But that does not seem to have any effect.  Which in one way is weird, as all other "special" buttons on this laptop seem to work well (for the first time).  Is there any way to check what this button is doing? Or is there any other way to turn on the radio?

The system is an Asus laptop, I think the correct model name is L5800C.
The system is a fresh install of Ubuntu 9.10, with the updates from apt-get update and apt-get upgrade.
asbjorn@snegle:~$ uname -a
Linux snegle 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

With kind regards
Asbjørn Sæbø
  
asbjorn@snegle:~$ dmesg |grep b43
[    1.947768] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.590634] b43legacy-phy0: Broadcom 4301 WLAN found
[    8.617115] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[    8.617137] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[    8.641036] b43legacy-phy0 debug: Radio initialized
[   17.540078] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   17.933059] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   18.062234] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   18.248043] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   18.307386] b43legacy-phy0 debug: Chip initialized
[   18.307664] b43legacy-phy0 debug: 30-bit DMA initialized
[   18.307852] b43legacy-phy0 debug: Wireless interface started
[   18.307863] b43legacy-phy0 debug: Adding Interface type 2
[   78.816044] b43legacy-phy0: Radio hardware status changed to DISABLED
[   78.816052] b43legacy-phy0 debug: Radio initialized
[   78.840052] b43legacy-phy0: Radio turned on by software
[   78.840059] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   78.840165] b43legacy-phy0 debug: Removing Interface type 2
[   78.840468] b43legacy-phy0 debug: Wireless interface stopped
[   78.840606] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[   78.840655] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[   78.840707] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   78.848050] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   78.856030] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   78.864029] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   78.872028] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 2/128
[   78.880028] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   78.888028] b43legacy-phy0 debug: Radio initialized
[   78.888046] b43legacy-phy0 debug: Radio initialized

---

### Post by pytheas22 on 2009-11-18
**Asbj.S.**: what kind of laptop do you have?  If you press the button to enable wireless, then type "sudo iwlist scan", do you see a list of networks?  Also, is there an option in your BIOS for enabling or disabling the wireless card?  If so, try playing with it.

---

### Post by Kingerlight on 2009-11-19
All right, I'm having a similar problem, and I am likewise new to Ubuntu.  I'm running 9.10, and have my Ethernet working just fine.  I installed b43-fwcutter, and it is now updated.  I updated all of my software, and made sure all of the 'Software Sources' items referenced are enabled.  I installed Ubuntu directly over Windows 7, and reformatted my entire hard drive to have a dedicated Linux machine.

I do not believe that my wireless adapter was disabled while operating in Windows 7, but the wireless activity LED is unlit.

**lspci -nn | grep -i broadcom**
03:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

**lshw -C Network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:1b:f9:a3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:18 memory:c0100000-c0103fff ioport:a000(size=256)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:c0200000-c0201fff
  *-network
       description: Ethernet interface
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet
       vendor: ADMtek
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 11
       serial: 00:0a:cd:11:04:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.102 latency=64 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:22 ioport:b400(size=256) memory:44000000-440003ff memory:40000000-4001ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:07:19:17
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

**ls /lib/firmware**
2.6.31-14-generic
acx
aic94xx-seq.fw
ar9170-1.fw
ar9170-2.fw
ar9170.fw
atmel_at76c502_3com.bin
atmel_at76c502_3com-wpa.bin
atmel_at76c502.bin
atmel_at76c502d.bin
atmel_at76c502d-wpa.bin
atmel_at76c502e.bin
atmel_at76c502e-wpa.bin
atmel_at76c502-wpa.bin
atmel_at76c503-i3861.bin
atmel_at76c503-i3863.bin
atmel_at76c503-rfmd-0.90.2-140.bin
atmel_at76c503-rfmd-acc.bin
atmel_at76c503-rfmd.bin
atmel_at76c504_2958-wpa.bin
atmel_at76c504a_2958-wpa.bin
atmel_at76c504.bin
atmel_at76c504c-wpa.bin
atmel_at76c505a-rfmd2958.bin
atmel_at76c505-rfmd2958.bin
atmel_at76c505-rfmd.bin
atmel_at76c506.bin
atmel_at76c506-wpa.bin
b43
b43legacy
BCM2033-FW.BIN
BCM2033-MD.BIN
dvb-fe-xc5000-1.6.114.fw
dvb-usb-dib0700-1.20.fw
i2400m-fw-usb-1.3.sbcf
i2400m-fw-usb-1.4.sbcf
ipw2100-1.3.fw
ipw2100-1.3-i.fw
ipw2100-1.3-p.fw
ipw2200-bss.fw
ipw2200-ibss.fw
ipw2200-sniffer.fw
isl3877
isl3886pci
isl3886usb
isl3887usb
isl3890
iwlwifi-1000-3.ucode
iwlwifi-3945-1.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-1.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
lbtf_usb.bin
NPE-B
NPE-B.01020201
NPE-C
NPE-C.02020201
ql2100_fw.bin
ql2200_fw.bin
ql2300_fw.bin
ql2322_fw.bin
ql2400_fw.bin
rt2561.bin
rt2561s.bin
rt2661.bin
rt2860.bin
rt2870.bin
rt73.bin
v4l-cx23418-apu.fw
v4l-cx23418-cpu.fw
v4l-cx23418-dig.fw
v4l-cx2341x-dec.fw
v4l-cx2341x-enc.fw
v4l-cx2341x-init.mpg
v4l-cx23885-avcore-01.fw
v4l-cx23885-enc.fw
v4l-cx25840.fw
v4l-pvrusb2-24xxx-01.fw
v4l-pvrusb2-29xxx-01.fw
zd1201-ap.fw
zd1201.fw
zd1211

**uname -m**
i686

**dmesg | grep -e wlan -e b43**
[    4.064077] b43-pci-bridge 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.770721] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.168077] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.107574] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.173588] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.211716] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.412041] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.460466] Registered led device: b43-phy0::tx
[   20.460483] Registered led device: b43-phy0::rx
[   20.460500] Registered led device: b43-phy0::radio
[   20.460547] b43-phy0: Radio hardware status changed to DISABLED
[   20.460737] b43-phy0: Radio turned on by software
[   20.460739] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   20.461086] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[COLOR=Blue]*I threw this in just in case it helps.*[/COLOR]
**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth1      Interface doesn't support scanning.


Thanks in advance!

---

### Post by pytheas22 on 2009-11-19
**Kingerlight**: from your dmesg output, it looks like your wireless card is turned off, which is the problem.  On most laptops there's either a physical switch or a software switch (like Fn+F2) that you can use to enable and disable the wireless card.  Please make sure it's turned on, then type "sudo iwlist scan" and it should return a list of networks within range.

On some computers, you may also have a setting in BIOS for controlling the wireless card; try playing with this if the switch doesn't work or doesn't exist.

If none of this seems to help, please let me know the exact model of your laptop.

---

### Post by Kingerlight on 2009-11-20
That is what I suspected, especially from the results of the **lshw**.  I've been carrying an Ethernet cord around with me all day, deposing other students from their locations if they happen to be near a function Ethernet port.  I came home and set up my **Gateway 7510gx**, and forgot to plug in the Ethernet cable.  I opened up Firefox, and the connection could obviously not be established.  I reconnected the cable and looked at your post, rebooting to examine the BIOS settings (of which there were actually none).  Upon rebooting into Ubuntu, I noticed that the wireless activity LED was lit.  I promptly conducted the **sudo iwlist scan** and it returned information about various wireless networks in range.  I am now able to connect to the wireless in my house.

_**DISCLAIMER:**_
I have no idea what changed or why it now works.  Apart from the output I posted earlier, I did not do any kind of system modification.  Maybe I unknowingly installed some software/hardware/firmware update and the reboot re-enabled my wireless.  I am completely bemused.

**pytheas22**: Thank you for the help so far, and thank you for being willing to help further.  Kind regards.

---

### Post by pytheas22 on 2009-11-20
Kingerlight: glad to hear it's working now.  Let me know if you have any more problems.  It could have just been something weird going on with your BIOS.

---

### Post by Kingerlight on 2009-11-20
I'm guessing so.  Dunno how it got fixed, but I am pleased!

---

