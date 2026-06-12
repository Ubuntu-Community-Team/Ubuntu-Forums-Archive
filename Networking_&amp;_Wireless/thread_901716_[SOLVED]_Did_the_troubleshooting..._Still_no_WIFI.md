---
title: "[SOLVED] Did the troubleshooting... Still no WIFI"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by solaceinsilence9 on 2008-08-26
I've checked out the troubleshooting guide for Ndiswrapper and I am still at a dead end. I have followed the steps 1-6 to the best of my knowledge and still no WIFI! First here are some computer specs:

Dell Inspiron 1501 
Amd 64 Athlon X2 Processor
Broadcom V4 WIFI

I can left-click on the network manager and goto "Connect to Other Wireless Networks". Once I do this I manually enter my network Id along with the correct security encryption type and the correct passy. Once I click ok I can left-click again on the Network Manager and "see" the network I just entered, expect there is no signal. When I goto Manual Configuration "Roaming Mode" is enabled for both wireless and wired networks. It doesnt matter if I disable roaming mode for the WIFI and manually enter all the network information in the network settings. Still no WIFI. Here are the modules I have blacklisted:

blacklist b44
blacklist ssb

The reason why those two are blacklisted is because the troubleshooting mentioned something about conflicting modules. So, I blacklisted those thinking that they might be having problems with b43. It's important to note that WIFI wasnt working before those were blacklisted. Hope that helps some... Also below is a small list of some commands that I typed in that may help you with my problem... Any help would be great! 


```
benjamin@ubuntu:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)



benjamin@ubuntu:~$ uname -mi
x86_64 unknown


results of the lspci -nn command:
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

results of lshw command:

  *-network
                description: Network controller
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb


  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:46:80:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


benjamin@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


benjamin@ubuntu:~$ lsmod | grep ndis
ndiswrapper           243872  0 
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd



benjamin@ubuntu:~$ dmesg | grep -e ndis -e wlan
[  310.603708] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  310.636299] usbcore: registered new interface driver ndiswrapper


```

:popcorn:

---

### Post by solaceinsilence9 on 2008-08-26
Oh ya and i forgot to mention, I am running a AMD64 Athlon X2 Processor. I have Windows Vista (32 bit) on one partition and Ubuntu on the other which is the x86_64 version of Herion.

---

### Post by falcon61102 on 2008-08-26
Ok... I read your post too fast.  Even if you have blacklisted ssb, you may still need to stop the module.  Try this:
```
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
```

That will reload your ndiswrapper module after disbaling the ssb.

Also have you blacklisted the b43 series as well?  If not, that might help.

---

### Post by solaceinsilence9 on 2008-08-27
Ok I have fixed my wifi.

---

### Post by falcon61102 on 2008-08-27
What did you do to fix it?

---

