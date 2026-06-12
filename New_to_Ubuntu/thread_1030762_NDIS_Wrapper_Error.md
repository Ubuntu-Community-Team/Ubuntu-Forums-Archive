---
title: "NDIS Wrapper Error"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by minifly3 on 2009-01-04
I'm trying to install ndis wrapper to use my wireless. This is on the latest ubuntu.
~sorry if in wrong category~

The error is long so i saved it to a text file.
[http://www.zetolic.com/error.txt](http://www.zetolic.com/error.txt)

I tried using this [http://ankurs.com/2008/04/installing...on-ubuntu-804/](http://ankurs.com/2008/04/installing...on-ubuntu-804/) but:
[IMG]http://www.tehupload.com/uploads/8558593d7aa81c1Screenshot2.png[/IMG]

Or do i need to blacklist one of the drivers?

> colin@colin-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5007G Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:11:2f:55:eb:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:13:86:9a:99:7c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
colin@colin-desktop:~$ \ndiswrapper -l
net5211 : driver installed
	device (168C:001D) present (alternate driver: ath_pci)
colin@colin-desktop:~$ 

---

### Post by Michael.Godawski on 2009-01-05
hi, 
have you tried to install ndiswrapper from the CD before compiling it for yourself?


[LIST]
[*][http://godawski.oxyhost.com/solvingwireless.html#ndiswrapper](http://godawski.oxyhost.com/solvingwireless.html#ndiswrapper)
[/LIST]

---

### Post by minifly3 on 2009-01-05
yes i have tried that, it gives me the screenshot shown

---

### Post by stchman on 2009-01-05
First off what kind of wireless card do you have?  The reason I have seen that error is that you are using the wrong .inf file for the wireless card.

Give us an lspci output in this thread.  It appears that you are using Intrepid.  From what I have seen the net5211 is an Atheros based wirelss card.  Install the Intrepid backport kernel modules as they have better Atheros wireless support.

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

This worked on my Acer Aspire One.

If you want to use ndiswrapper you will need to blacklist the ath_pci and ath5k modules.

---

### Post by minifly3 on 2009-01-05
lspci output: 
> 00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
colin@colin-desktop:~$ 


Card: Belkin f5d7010
The drivers are the ones under xp2k on the cd.

I installed the Intrepid backport kernel modules. What do i do after that? (I'm fairly new to linux only used centos 5 servers)

---

### Post by albinootje on 2009-01-05
> **minifly3 said:**
>  device (168C:001D) present (alternate driver: ath_pci)

What gives :
```

lsmod|grep ath
ifconfig -a
sudo iwconfig
sudo iwlist scan

```

---

### Post by stchman on 2009-01-05
> **minifly3 said:**
> lspci output: 


Card: Belkin f5d7010
The drivers are the ones under xp2k on the cd.

I installed the Intrepid backport kernel modules. What do i do after that? (I'm fairly new to linux only used centos 5 servers)

After the backport kernel modules are installed go to System--->Administration--->Hardware and enable the drivers.

---

### Post by minifly3 on 2009-01-05
drivers are enabled but not being used it says.

---

### Post by albinootje on 2009-01-05
> **minifly3 said:**
> drivers are enabled but not being used it says.

Did you try this or not ?
```

sudo iwlist scan

```

---

### Post by minifly3 on 2009-01-06
it says these devices don't support scanning.

---

