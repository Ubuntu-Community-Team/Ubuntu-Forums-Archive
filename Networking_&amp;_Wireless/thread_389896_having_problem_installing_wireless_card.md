---
title: "having problem installing wireless card"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by Khaled Khalil on 2007-03-21
i followed instructions from [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)") guide by FrodoB, all was going fine untill step 7:
after "iwconfig"
"If rausb0 is present it is time to connect to the internet."
if not ?:confused: 

"iwconfig" returns:"
wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"BaseWLNW"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B
"
but no rausb0 :( 

also when i tried "sudo ifup rausb0" i got:
"rausb0: ERROR while getting interface flags: No such device
Failed to bring up rausb0."
"ifup/ifdown wlan0" affect the dongle's led but not rausb

can someone help me ?

---

### Post by handaxe on 2007-03-21
Not sure I can help all the way. Did you follow that guide in every step, doing the checks that files were installed into the right directories?

Type

```
lsmod
``` at the terminal.

Check output for the presence of the rt73 driver (assuming that is the driver you installed).  If it is not there, the try (at the terminal)

```
sudo depmod -a
sudo modprobe rt73
```If "module not found" or words to that effect is the reply then something went wrong or was not done correctly in the steps outlined in the how- to.

If you get no error after the modprobe then

```
sudo lshw -c Network
``` should show you the interface with the loaded driver (plus other stuff).

If you find that wlan0 persists as the interface present, you could delete it from /etc/iftab and retry the how-to (or could he rename it rausb0?  Someone else who knows? wlan0 seems toi be finding his AP???)

Double check that you followed that how to in all steps.

HA

---

### Post by Khaled Khalil on 2007-03-21
thanks handaxe
"lsmod" return 5 results containing rt73
```
k@Kambar:~/RT73_Linux_STA_Drv1.0.3.6/Module$ lsmod|grep rt73
rt73                  223872  0 
rt73usb                37888  0 
80211                 175880  2 rate_control,rt73usb
crc_itu_t               3200  1 rt73usb
usbcore               134912  9 rt73,rt73usb,ndiswrapper,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
```
:confused:

though, i tried the other commands
```
sudo depmod -a
sudo modprobe rt73
```
returned nothing

```
sudo lshw -c Network
```
returned:
```
k@Kambar:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo lshw -C Network
  *-usb DISABLED          
       description: Wireless interface
       product: 802.11 bg WLAN
       vendor: Ralink
       physical id: 3
       bus info: usb@5:3
       logical name: wmaster0
       version: 0.01
       serial: 00:19:5b:39:ef:ba
       capabilities: usb-2.00 logical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=CVS firmware=rt73usb->%s: Error - vendor requ5-3:1.0 link=yes maxpower=300mA multicast=yes speed=480.0MB/s wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:14:2a:00:2f:d2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.65 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a400-a4ff iomemory:fa010000-fa0100ff irq:193
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:5b:39:ef:ba
       capabilities: ethernet physical wireless
       configuration: multicast=yes wireless=IEEE 802.11g

```
wmaster0 already has drive:rt73usb
wlan0 didn't said anything about its drive !
and nothing about rausb0 !

"/etc/iftab" doesn't contain anything about wlan0 nor rausb0, just one line about eth0
should i try to delete it (wlan0, and maybe wmaster0 also) from "/etc/network/interfaces" ?
i will try to do so then retry the how to now

---

### Post by handaxe on 2007-03-21
Hi.

Am trying to digest this and hoping that someone can come in and help who is familiar with this driver because now you have provided proper info.

Back to reading...
HA

---

### Post by handaxe on 2007-03-21
Hi,

It seems that either you did not blacklist your original (ie ubuntu installed) driver or the blacklisting failed to stick.

Both rt73usb (the original) and rt73 (the one you installed) are loaded.  Not good.

I would retry the how to - perhaps do the blacklisting and then reboot and check that rt73usb has not loaded then proceed with the install.

HA

---

### Post by Khaled Khalil on 2007-03-21
> **handaxe said:**
> and then reboot
that was really what i had to do
i am now online using the wireless card :) , thank you handaxe very much
i feel really grateful, i am sorry, i annoyed you because of my stupidness and my lack of patience
have a nice day/night

---

### Post by handaxe on 2007-03-22
No annoyance here I assure you. Glad to read you got going...

HA

---

