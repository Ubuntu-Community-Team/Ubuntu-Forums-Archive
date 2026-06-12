---
title: "Broadcom drivers"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-02-04
hi everyone
    i am trying to activate broadcom b43 wireless driver from additional drivers package...it starts asks for password downloads for sometimes and then gives an error    SystemError: installArchives() failed
what might be the reason? it got installed yesterday and was working properly before it automatically got inactivated

please help thanx in advance to all

---

### Post by vivek.pandey on 2011-02-04
somebody please reply my question..

---

### Post by Hippytaff on 2011-02-04
maybe uninstall and reinstall it. You might also want to try
```

rfkill unblock all

```
And it might be worth posting the results to a few commands to help people diagnose the problem.
```

lshw -C network

```
```

iwconfig

```
```

lspci | grep -i netw

```
 
There are lots of thread about broadcom drivers, so they might also be of some assistance.
:-)

---

### Post by vivek.pandey on 2011-02-04
> **Hippytaff said:**
> maybe uninstall and reinstall it. You might also want to try
```

rfkill unblock all

```And it might be worth posting the results to a few commands to help people diagnose the problem.
```

lshw -C network

``````

iwconfig

``````

lspci | grep -i netw

```iwconfig
vivek@NEO:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

ppp0      no wireless extensions.

There are lots of thread about broadcom drivers, so they might also be of some assistance.
:-)

thanks for reply i tried reinstalling many times each time i got the same error..here are the ops of the code you gave

```
lshw -C network
root@NEO:/home/vivek# lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:5b:26:60
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:3000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 78:e4:00:1f:ae:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-24-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 5
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

```
lspci | grep -i netw
vivek@NEO:~$ lspci | grep -i netw
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

---

### Post by vivek.pandey on 2011-02-04
> **Hippytaff said:**
> maybe uninstall and reinstall it. You might also want to try
```

rfkill unblock all

```
And it might be worth posting the results to a few commands to help people diagnose the problem.
```

lshw -C network

```
```

iwconfig

```
```

lspci | grep -i netw

```
 
iwconfig
vivek@NEO:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

ppp0      no wireless extensions.

There are lots of thread about broadcom drivers, so they might also be of some assistance.
:-)

thanks for reply i tried reinstalling many times each time i got the same error..here are the ops of the code you gave

lshw -C network
root@NEO:/home/vivek# lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:5b:26:60
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:3000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 78:e4:00:1f:ae:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-24-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 5
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

lspci | grep -i netw
vivek@NEO:~$ lspci | grep -i netw
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by Hippytaff on 2011-02-04
try```
ifconfig iw0 up
```

---

### Post by TBABill on 2011-02-04
I have a BCM4312 and I have never had very good luck with the b43 driver. It's open source but still relies on the firmware from Broadcom. Are you able to remove the b43 driver (may have to use Synaptic to do so) and install the STA driver (actual driver is wl)?
 
If you can't just choose the STA driver and use it under SYSTEM>ADMINISTRATION>HARDWARE (or additional drivers in 10.10), you could try ```
sudo apt-get install bcmwl-kernel-source
``` This step installs the WL (STA) driver. And then ```
sudo modprobe -r b43 ssb wl
``` This code tells the system to ignore the b43, ssb and wl drivers. Then ```
sudo modprobe wl
``` and see if it starts working.
 
Even if it starts working a couple extra steps will need to be done. You'll need to blacklist the b43 and ssb drivers in /etc/blacklist.conf and enter the wl in /etc/modules so the system knows to activate it upon boot. But these can be done after figuring out what's keeping it from working.

---

### Post by TeoBigusGeekus on 2011-02-04
A recent adventure of mine with a BCM4313 had a happy ending only with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by Hippytaff on 2011-02-04
> **TBABill said:**
> I have a BCM4312 and I have never had very good luck with the b43 driver.

They are infamously annoying - glad someone with a bit more experience with them has chimed in :-)

---

### Post by TBABill on 2011-02-04
Unfortunately it's a pain to get that experience. In some distros it's pretty easy, like in Ubuntu, but you have to know which driver you want/need since it offers both. Some claim the b43 works ok for the same card on their machine, but most state it doesn't. I haven't had luck on my 3 different laptops with the 4312, but I always have to figure out what steps to take to try a different distro just to get wireless going. Next laptop will have an Intel wireless device just to rid myself of most of the wireless worries.

---

### Post by vivek.pandey on 2011-02-04
> **Hippytaff said:**
> try```
ifconfig iw0 up
```

i tried this code its output is 

vivek@NEO:~$ ifconfig iw0 up
iw0: ERROR while getting interface flags: No such device

---

### Post by vivek.pandey on 2011-02-04
> **Hippytaff said:**
> try```
ifconfig iw0 up
```

thanx for your help
i tried this code its output is 

vivek@NEO:~$ ifconfig iw0 up
iw0: ERROR while getting interface flags: No such device

plus i tried to reactivate the driver after executing your first code you gave..its stuck so badly that i cant do anything to close the additional drivers window
i am not blaming your code please understand this i am only trying to say i followed what you did

---

### Post by Hippytaff on 2011-02-04
restart and try tbabills suggestion, failing that it looks as though your going to have to look into using the windows driver with ndisgtk which is the ndiswrapper with a gui (I think you need the xp driver)

btw - the code was just diagnostic stuff, so it shouldn't harm your system :-)

---

### Post by vivek.pandey on 2011-02-04
> **Hippytaff said:**
> restart and try tbabills suggestion, failing that it looks as though your going to have to look into using the windows driver with ndisgtk which is the ndiswrapper with a gui (I think you need the xp driver)

btw - the code was just diagnostic stuff, so it shouldn't harm your system :-)

thats what i said i didnt mean that your command did that..i told it because i felt that may help you recognize the problem..o0rry if you were hurt

btw why do i need a xp driver on ubuntu machine.sounds bit strange

---

### Post by Hippytaff on 2011-02-04
I wasn't hurt ;-)

The open source broadcom driver isn't great. The Ndiswrapper tool is used to wrap windows drivers, so that linux can use them, but I believe it only works with XP drivers

---

### Post by Safsal on 2011-02-11
TBABill
 
Thank You immensely for posting those two codes that disabled and enabled a driver.
 
I am new to ubuntu and I was getting very frustrated that the internet on my Dell was seen, but connection was impossible.
 
Appharently there was too much internal traffic due to driver.  I will now try to blacklist.:D

---

### Post by Hakunka-Matata on 2011-02-11
You can make it work, there are a lot of places to go wrong on the way however.  I've dealt with this problem many, many times.  Try the following link:  [http://linuxwireless.org/en/users/Drivers/b43#availabledevices]("http://linuxwireless.org/en/users/Drivers/b43#availabledevices")

And good luck

---

