---
title: "New installation won't connect to wifi"
date: 2017-09-26
forum: Networking &amp; Wireless
---

### Post by floyd1677 on 2017-09-26
Hi everyone,
I'm pretty new to Linux but have recently been given an old Dell desktop which I've installed Lubuntu 17.04 on. I've had no problems connecting to the internet via ethernet but I have a generic 802.11N wifi adapter which for some reason won't connect. When I check my available networks, the available wifi networks are showing but when I attempt to connect it seems to hang for about a minute before I get the message; "Disconnected - you are now offline"

Can anyone walk me through what I need to do to get my wifi working?

Thanks.

---

### Post by howefield on 2017-09-26
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by Bucky Ball on 2017-09-26
Welcome. Please open a terminal and supply us with the output of this command for starters.

```
sudo lshw -C network
```

That will give people a quick look at what's there and in what state.

Out of curiousity, have you done an update/upgrade since you installed the OS and then rebooted? Something to remember is that the ethernet cable being plugged in will generally override wireless. If you haven't already, suggest you pull the ethernet cable and reboot with that out and see how you go, but not before doing an update, if you haven't already. 

Good luck.

---

### Post by floyd1677 on 2017-09-26
Thanks, tried update and upgrade, also tried the reboot without the ethernet cable and, while the networks are showing I just still get the disconnected message when I try them. I've run the code you gave and here's the result

>   *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: 00:25:64:83:59:89
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:4
       logical name: wlx20e917050d7d
       serial: fe:63:fb:39:ed:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=4.10.0-35-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11


---

### Post by Bucky Ball on 2017-09-26
OK, how about the output of this, please:

```
iwconfig
```

There is a driver for that card already in the kernel so no need to install one by the looks. A problem somewhere else it seems. Are you getting asked for a password when you try to log on to the network? Tried 'Edit connections', put the correct details for that network in manually then reboot? (Click network icon and 'Edit Connections'.)

(PS: You almost got the tags right. Use [code] and the appropriate end tag for code. ;))

---

### Post by floyd1677 on 2017-09-26
that gave me this:
```
wlx20e917050d7d  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

enp2s0    no wireless extensions.

```

I entered the password in setup originally when it first found the network, I've double checked it so many times! lol

---

### Post by praseodym on 2017-09-26
There is a bug in 17.04. Please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
You'd better c/p these lines. Reboot then

---

### Post by floyd1677 on 2017-09-26
Absolutely brilliant! Thanks for that, I've spent about two weeks trying to figure out what was wrong with it! I can finally move the computer out of the living room before I get in any more trouble for having wires/computer parts everywhere! 
Thanks again!

---

### Post by mörgæs on 2017-09-26
Congratulations, please read the signature in post #3.

---

### Post by Bucky Ball on 2017-09-26
Nicely! Enjoy. ;)

---

### Post by klaipedaville on 2018-09-07
> **praseodym said:**
> There is a bug in 17.04. Please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
You'd better c/p these lines. Reboot then

I have absolutely the same issue as if the person who asked the question was using my computer! It's a 100% match! The only difference is that my Xubuntu version is 18.04.01 and the above mentioned solution does not help.

All the replies from "iwconfig" and "sudo lshw -C network" are absolutely the same as typed by the person who asked the question. 

Could anybody advise please, how do I get rid of this "traveling" from version to version bug now? Many thanks in advance!

---

### Post by wildmanne39 on 2018-09-07
Hello and welcome to the forum klaipedaville, please start your own thread instead of posting in a thread that is marked solved and is a year old so you can get the help you need.

Thanks

Old thread back to sleep!

---

