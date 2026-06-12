---
title: "Broadcom BCM4318 8.10"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by jonner3 on 2008-10-30
I know there have been a lot of posts on the BCM43 and tried reading through them with no avail.

I have an Acer Laptop with a BCM 4318 wireless card running Ubuntu 8.10. Hardware drivers show the BCM43 active and in use, however I am unable to scan or try to connect to any networks (just not able to click on wireless options)

I am new to Linux as a Desktop but do have experience on Command line servers so I am not completely new, just to the wireless Aspect. Anyone have any ideas?

---

### Post by Ayuthia on 2008-10-30
> **jonner3 said:**
> I know there have been a lot of posts on the BCM43 and tried reading through them with no avail.

I have an Acer Laptop with a BCM 4318 wireless card running Ubuntu 8.10. Hardware drivers show the BCM43 active and in use, however I am unable to scan or try to connect to any networks (just not able to click on wireless options)

I am new to Linux as a Desktop but do have experience on Command line servers so I am not completely new, just to the wireless Aspect. Anyone have any ideas?

Have you tried scanning from the command line?  Can you try the following:
```
lshw -C network
sudo iwlist scan
```
The first will see what driver it is trying to use and the next one will try to scan for wireless sites.

---

### Post by ercdvs on 2008-10-30
> **jonner3 said:**
> I know there have been a lot of posts on the BCM43 and tried reading through them with no avail.

I have an Acer Laptop with a BCM 4318 wireless card running Ubuntu 8.10. Hardware drivers show the BCM43 active and in use, however I am unable to scan or try to connect to any networks (just not able to click on wireless options)

I am new to Linux as a Desktop but do have experience on Command line servers so I am not completely new, just to the wireless Aspect. Anyone have any ideas?

Get a hardwired connection and get online.
run:
 sudo apt-get update
 sudo apt-get upgrade

There should be a new entry for a Broadcom driver in the hardware list under the admin menu ..   enable it, and it will download additional drivers, and you will be good to go after a reboot.

---

### Post by jonner3 on 2008-11-01
> jonner@jonner-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:43:6b:2d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.0.198 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:57:7f:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:38:27:1f:5d:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


jonner@jonner-laptop:~$ sudo iwlist scan
[sudo] password for jonner: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.






In Hardware Drivers already lists "Broadcom B43 Wireless Driver" and is enabled. Ran the apt update and upgrade, no change

---

### Post by Ayuthia on 2008-11-01
> **jonner3 said:**
> In Hardware Drivers already lists "Broadcom B43 Wireless Driver" and is enabled. Ran the apt update and upgrade, no change

Please try the following in the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo /etc/init.d/networking restart
sudo iwlist scan
```
Hopefully it is just the wl driver that is causing the problem.  If this works, you will need to blacklist the wl driver:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by jonner3 on 2008-11-02
No change, Iwlist scan shows no scan results, Hardware drivers shows the same driver listed.

---

### Post by brandoncolorado on 2008-11-02
Same problem here.

---

### Post by sinkinglow on 2008-11-02
I'm having the same issue. I followed the suggestions and received the same results. I had it working at one point yesterday. It seems like if you boot up with the hard wire connected it then sees the wireless network and you can unplug the wire and keep the wireless connection. But if you boot without being plugged into a wire it won't see any wireless sites. Sounds strange but that's what I've come to so far :)

---

### Post by Ayuthia on 2008-11-02
> **sinkinglow said:**
> I'm having the same issue. I followed the suggestions and received the same results. I had it working at one point yesterday. It seems like if you boot up with the hard wire connected it then sees the wireless network and you can unplug the wire and keep the wireless connection. But if you boot without being plugged into a wire it won't see any wireless sites. Sounds strange but that's what I've come to so far :)

Can you post the results of lshw -C network?  It sounds strange that you can see wireless sites only when there is a wired connection.  I am not doubting what you are saying, but I can't seem to guess why it would do that.

As for the others, it looks like ndiswrapper might be the option.  You can try this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by sinkinglow on 2008-11-02
Once I could see the wireless network, I was able to unplug and stay connected to wireless. I think I have think I have it figured out tho. It seems that the wireless light on this laptop is buggy. I toggled the function + F2 and the wireless connected but the light went off. Go figure... but it appears it was a user error :)  However here is the output:


lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:33:2e:56
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
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
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:aa:d1:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.7 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:fb:a7:f9:18:8f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by jonner3 on 2008-11-02
ndiswrapper has mostly got me fixed. Network manager still does not show any wireless but a manual scan does.

Only issue now is I have to use iwconfig to connect everytime I turn on the computer, I am assuming there is a file I can edit to always connect?


Disregard, I just found the /etc/network/interfaces file. well it isn't perfect but this is up and running with about 95% of functionality. Thanks for the help..

---

### Post by unknown03 on 2008-11-04
Same problem here too.. nothing seems to be working..

Also, when I go to Hardware drivers to activate the BCM43-fwcutter it installs then does nothing else. Restart and it still says its deactivated

---

