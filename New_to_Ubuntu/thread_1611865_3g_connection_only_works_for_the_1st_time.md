---
title: "3g connection only works for the 1st time"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by xxdiegoxx on 2010-11-02
[I][B][COLOR=RoyalBlue][FONT=Verdana]hello!

im not that new to ubuntu, but im new to making it work right.

while using 9.04, i installed a kernel that allowed my 3g zte modem to work and i could connect to internet. now, with my new netbook, using 10.10 x64, internet only works the 1st time or while using the livecd - which i believe is equal to the 1st use... anyway...

i live in brazil - and know of the portuguese version of the forums - and am using a 3g provider form the list ubuntu offers. since the provider's helpdesk is stupid enough to not even know what ubuntu is, and im discarding OS incompactbility - i could connect with 9.04 and can connect for once in 10.10, i believe is some kind of misconfiguration.

i already browsed the forums and no one seens to have asked/answered exactly what i asked.

how can i set it right?

thanks in advance!

sorry if this is the wrong forum and sorry for any mispelling errors that may exist.
[/FONT][/COLOR][/B][/I]

---

### Post by Hippytaff on 2010-11-02
Is it a usb dongle?

---

### Post by xxdiegoxx on 2010-11-02
> **Hippytaff said:**
> Is it a usb dongle?


[B][COLOR=RoyalBlue][FONT=Verdana][I]"dongle"?!

its the usb 3g modem zte mf626...


[/I][/FONT][/COLOR][/B]

---

### Post by Hippytaff on 2010-11-02
ok...so with it plugged type
```

lsusb

``````

iwconfig

``````

lshw -C network

``````

rfkill list

```into the terminal, one at a time (CTRL+ALT+T to open a terminal) and post the output and we can have a look at whats going on (I've got a feeling either a driver issue)

---

### Post by gandaran on 2010-11-02
> **xxdiegoxx said:**
> [B][COLOR=RoyalBlue][FONT=Verdana][I]"dongle"?!

its the usb 3g modem zte mf626...


[/I][/FONT][/COLOR][/B]
look if it did work in the live cd then it must work!
did you use the network manager for the set up?
ensure your connection details are correct and check-mark the 'connect automatically' box then shutdown your computer with the modem plugged in and then start the computer.
I have found that some usb dongles need to shutdown the computer completely for them to work in ubuntu 10.10, just rebooting doesn't fix it.
if still no work with network manager you can try a third party software like betavine/vodafone mobile connect, this software can work with any ISP not just vodafone.

---

### Post by Hippytaff on 2010-11-02
I was thinking a either driver conflict would cause it to work intimitantely, or for some reason there was a block on rfkill after the first succesful use...though that sounds sensible

---

### Post by xxdiegoxx on 2010-11-08
[I][FONT=Verdana][B][COLOR=RoyalBlue]sorry for taking so long... i used my once-in-installationtime internet access and had to wait untill i get another one...


heres what i got:

[/COLOR][/B][/FONT][/I]```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: b4:82:fe:c8:b9:83
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:46:ac:b3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes
       resources: irq:44 memory:f0200000-f0203fff ioport:2000(size=256)


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```[I][FONT=Verdana][B][COLOR=RoyalBlue]
[/COLOR][/B][/FONT][/I]

---

### Post by Hippytaff on 2010-11-08
Try
```

rfkill unblock all

```

---

