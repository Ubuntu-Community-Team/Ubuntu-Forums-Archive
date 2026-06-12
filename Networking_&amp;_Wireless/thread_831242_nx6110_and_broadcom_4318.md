---
title: "nx6110 and broadcom 4318"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by hollowhead on 2008-06-16
Has anyone managed to get this wifi card on this laptop working in hardy?  It worked in gutsy then I upgraded tried the restricted drivers route, but it did not install, then I tried [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

Jamie was very helpful but no joy.  I also posted to launchpad.  Then I noticed there was a restricted driver upgrade and kernel headers.  Once these were upgraded the restricted driver for the card installed and the wifi light came on.  But the network manager shows no wifi. Ndiswrapper is loading as a module presumably I don't want this I have to say I am completely confused about b43, bcm43xxx and wrapper....

Ta.  NH

---

### Post by Ayuthia on 2008-06-16
> **hollowhead said:**
> Has anyone managed to get this wifi card on this laptop working in hardy?  It worked in gutsy then I upgraded tried the restricted drivers route, but it did not install, then I tried [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

Jamie was very helpful but no joy.  I also posted to launchpad.  Then I noticed there was a restricted driver upgrade and kernel headers.  Once these were upgraded the restricted driver for the card installed and the wifi light came on.  But the network manager shows no wifi. Ndiswrapper is loading as a module presumably I don't want this I have to say I am completely confused about b43, bcm43xxx and wrapper....

Ta.  NHWhat did you use in Gutsy?

I am not for sure about what you are confused about the b43, bcm43xx, and ndiswrapper modules.  The b43 is the newest module introduced.  It replaces bcm43xx.  Its firmware is found in /lib/firmware/b43 and /lib/firmware/b43legacy (using the repository version of b43-fwcutter).  The b43 module also introduces ssb which has been causing issues with ndiswrapper.

ndiswrapper 1.50 and higher only work on Hardy because of the new kernel 2.6.24.  You have to make sure that ndiswrapper loads before ssb or else it will not work.

bcm43xx is the old module and is blacklisted by default in Hardy.  It can be used though.  You have to make sure that it is installed (bcm43xx-fwcutter).  The firmware is found in /lib/firmware and is found as /lib/firmware/bcm43*.fw.  To use this module, you will have to make sure that b43, ssb, and ndiswrapper are not loaded.

If you want to try one them, just pick one and we can help get it configured for you.

The 4318 card and the 4306 cards have been struggling lately.  The 4306 cards have been having issues in 2.6.24-18.  I am trying to see if I can duplicate it on my end, but I don't have a 4318 card and I have seen people get some to work with one type but not another.  Unfortunately, it is not consistent and I have not picked up many subvendors to confirm which one needs which module.

---

### Post by hollowhead on 2008-06-17
Thanks for your reply Ayuthia.  I have tried the following I have completely removed Ndiswrapper (I assume I don't need it) although even afterwards its module was loading (see below).  I tried blacklisting b43 first of all and removing its module and rebooting I lost my wifi light.  Then I did the opposite blacklisted Ndiswrapper and bcm43xx and using b43 as this shows up in system-> admin->hardware drivers.  I rebooted and got my light back but no access to wifi.  So I want to go for b43.  Here is some output from my terminal

lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper

ndiswrapper           185104  0 
b43                   113952  0 
rfkill                  7568  3 rfkill_input,b43
mac80211              162708  1 b43
led_class               5124  1 b43
input_polldev           5000  1 b43
ssb                    31236  2 b43,b44
usbcore               143724  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

I cannot understand why ndiswrapper is loading when I have blacklisted it and uninstalled it? If I remove the ndiwrapper module then it is not listed with above command.

sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:c2:e5:b9:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.2 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:14:a5:65:71:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Can you explain in simple words of two syllables how to get it working?  Ta.  NH.

---

### Post by Ayuthia on 2008-06-17
> **hollowhead said:**
> 

I cannot understand why ndiswrapper is loading when I have blacklisted it and uninstalled it? If I remove the ndiwrapper module then it is not listed with above command.It sounds like you might be using a wireless fix script.  Did you create one and place it in /etc/init.d or /etc/rc.local?

> Can you explain in simple words of two syllables how to get it working?  Ta.  NH.The first thing that we can do is see if we can get your card working by using the firmware that you installed:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo depmod -ae
sudo moprobe b43 b44
sudo ifconfig wlan0 up
sudo dhclient -r wlan0
```Let me know if the wireless card lights up and if you are able to connect.  If you can, then we need to find the script that is causing ndiswrapper to load.

The first line in the code will remove the b43, b44, ssb, and ndiswrapper modules.  The b44 driver is actually your wired card driver, but we want to remove the ssb driver and reload it.  The b43 and b44 drivers require ssb so to remove ssb, we have to remove the two drivers.  

The second line rebuilds the module dependencies.  

The third line will then load only the b43 and b44 drivers and not ndiswrapper.  The ssb driver will automatically load because the b43 and b44 need it.

The fourth line turns on your wireless card.

The fifth line will reset the dhcp for your wireless.

If for some reason your wired connection does not work, you might need to turn it back on:
```
sudo ifconfig eth0 up
sudo dhclient eth0
```

When you test your wireless, please make sure that you have pulled the cord from your wired connection.  The wireless does not work with the wire plugged in.

---

### Post by jeremy1138 on 2008-06-17
I have an HP laptop (model dv5020us) with the broadcom 4318 wireless card and I had a lot of problems getting it working when I upgraded to Hardy.  I ended up doing a clean install and I tried a few things to get it working with no success until I found this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

It's a tutorial that has instuctions for getting various Broadcom cards to work.  I followed the instructions and wireless is now working great.  Give it a try!

---

### Post by hollowhead on 2008-06-17
OK thanks for your help, Jeremy that is the thread I tried it didn't work.  

I tried the following

sudo modprobe -r b43 b44 ssb ndiswrapper
sudo depmod -ae

no errors or comments at the command line
then 
 sudo modprobe b43 b44
FATAL: Error inserting b43 (/lib/modules/2.6.24-17-386/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

So I loaded the modules separately b44 gave me the network card back

b43 apparently did nothing no error no light back on

sudo ifconfig wlan0 up gave the following error
wlan0: ERROR while getting interface flags: No such device

I believe my wifi is eth1

so I tried 

 sudo dhclient -r eth1

no error

sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:14:a5:65:71:d2
Sending on   LPF/eth1/00:14:a5:65:71:d2
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 137.195.229.251 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

I then had a look at dmesg 

as it suggested below I tried pushing the button and on it came I unplugged the ethernet and it connected to my wifi network although the speed is only 2mb/sec I used to get at least 24.  So nearly there how do I make it permanent and get the speed back up given the laptop is practically on top of my router and the signal strength is 75%?


 50.884426] Registered led device: b43-phy0:radio
[   50.890801] b43-phy0: Radio hardware status changed to DISABLED
[   52.593931] [drm] Initialized drm 1.1.0 20060810
[   52.645990] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[   52.646000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   52.646071] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   68.616753] NET: Registered protocol family 10
[   68.617242] lo: Disabled Privacy Extensions
[   68.618709] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.619271] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   73.752315] b44: eth0: Link is up at 100 Mbps, full duplex.
[   73.752321] b44: eth0: Flow control is off for TX and off for RX.
[   73.753165] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   78.155627] NET: Registered protocol family 17
[   92.669988] eth0: no IPv6 routers present
[  214.898964] ACPI: PCI interrupt for device 0000:02:0e.0 disabled
[  214.899593] ACPI: PCI interrupt for device 0000:02:04.0 disabled
[  214.934527] usbcore: deregistering interface driver ndiswrapper
[  230.683219] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[  230.708354] ssb: Sonics Silicon Backplane found on PCI device 0000:02:04.0
[  230.711876] b43: Unknown parameter `b44'
[  230.792834] b43-phy0: Broadcom 4318 WLAN found
[  230.797921] phy0: Selected rate control algorithm 'simple'
[  230.824078] udev: renamed network interface wlan0 to eth1
[  230.879860] input: b43-phy0 as /devices/virtual/input/input10
[  231.836502] Registered led device: b43-phy0:radio
[  231.843324] b43-phy0: Radio hardware status changed to DISABLED
[  231.848633] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  231.919251] b43-phy0: Radio turned on by software
[  231.919259] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  240.236893] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 16 (level, low) -> IRQ 22
[  240.248771] ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0
[  240.249101] b44.c:v2.0
[  240.269398] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:c2:e5:b9:43
[  240.445544] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  240.834039] b44: eth0: Link is up at 100 Mbps, full duplex.
[  240.834045] b44: eth0: Flow control is off for TX and off for RX.
[  240.834883] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  243.316765] eth0: no IPv6 routers present
[  263.247227] b44: eth0: Link is down.
[  271.242596] b44: eth0: Link is up at 100 Mbps, full duplex.
[  271.242602] b44: eth0: Flow control is off for TX and off for RX.
[  271.243432] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  273.727889] eth0: no IPv6 routers present
[  275.117283] b44: eth0: Link is down.
[  288.161052] b44: eth0: Link is up at 100 Mbps, full duplex.
[  288.161057] b44: eth0: Flow control is off for TX and off for RX.
[  288.161896] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  290.565826] eth0: no IPv6 routers present

Ta NH sent via wifi!

---

### Post by Ayuthia on 2008-06-17
> **hollowhead said:**
> 
I then had a look at dmesg 

as it suggested below I tried pushing the button and on it came I unplugged the ethernet and it connected to my wifi network although the speed is only 2mb/sec I used to get at least 24.  So nearly there how do I make it permanent and get the speed back up given the laptop is practically on top of my router and the signal strength is 75%?

Ta NH sent via wifi!

Ok.  We now know that the wireless card works.  The next part is to figure out what is loading the ndiswrapper module.  The link that you used for NDISwrapper has three options to make things permanent.  The file that I think might be causing the problem would be /etc/init.d/rc.local.  Can you post the results of:
```
cat /etc/modprobe.d/blacklist*|grep -i -e b43 -e bcm43xx -e b44 -e ssb -e ndiswrapper
cat /etc/modules|grep -i -e b43 -e bcm43xx -e b44 -e ssb -e ndiswrapper
cat /etc/init.d/rc.local
```
The first two is to verify that the modules are blacklisted and auto loaded correctly.  The last one is to see if ndiswrapper is being loaded in that script.

---

### Post by hollowhead on 2008-06-18
Ayuthia, 

Thanks for your help its working consistently on reboot!  I don't know how to formally thankyou but consider yourself thanked.  The speed is not as fast as it should be but mostly I get better % reception than I used to.  Kwifimanager says I'm getting 11mb/s rather than 1 as reported by network manager. Ta.  Neil.

---

