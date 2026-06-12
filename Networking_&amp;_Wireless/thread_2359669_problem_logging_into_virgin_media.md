---
title: "problem logging into virgin media"
date: 2017-04-26
forum: Networking &amp; Wireless
---

### Post by keithmart2 on 2017-04-26
Hi

I am new to Ubuntu, and have loaded 17.04 on to an advent laptop that was running windows 7

All appears to work ok with the exception of logging on to virgin broadband.

I can list all the local broadbands, and can connect to BT zone (but not being a BT customer cannot get past the welcome screen)

Broadband is ok on my windows 10 computer, and phone.

For some reason ubuntu will not accept the broadband password. I have retyped it numerous times, and tried rebooting.

Does anybody have any ideas??


Regards

Keith

Leeds UK

---

### Post by Bucky Ball on 2017-04-26
Welcome. Try this. Open a terminal and

```
sudo apt update
sudo apt full-upgrade
```

If your wireless doesn't come up or you don't get a message about it, reboot the machine, then open a terminal and, for a start, post the result of this command, please.

```
sudo lshw -C network
```

Also, look in 'Additional Drivers' after update/upgrade/reboot. Anything there pertaining to wireless? Don't install if there is, just let us know which wireless driver is showing there along with posting the output of the command.

---

### Post by ajgreeny on 2017-04-26
I am a bit concerned that you might be mistaking the broadband password with the wifi network password which are usually two different passwords.

---

### Post by keithmart2 on 2017-04-27
Hi

Thanks for your replies.

The  password I am using is the correct one.

The report:




keithmart@keith-ubuntu:~$sudo lshw -c network  *-network                
       description:Wireless interface
       product:RTL8187SE Wireless LAN Controller
       vendor: RealtekSemiconductor Co., Ltd.
       physical id: 0
       bus info:pci@0000:04:00.0
       logical name:wlp4s0
       version: 22
       serial:62:a5:1a:37:9b:e4
       width: 32 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress bus_master cap_list ethernet physical wireless
       configuration:broadcast=yes driver=rtl818x_pci driverversion=4.10.0-19-genericfirmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources:irq:17 ioport:3000(size=256) memory:fa000000-fa003fff
  *-network
       description:Ethernet interface
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: RealtekSemiconductor Co., Ltd.
       physical id: 0
       bus info:pci@0000:05:00.0
       logical name:enp5s0
       version: 03
       serial:00:03:0d:f3:37:69
       size: 10Mbit/s
       capacity:1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pmmsi pciexpress msix vpd bus_master cap_list rom ethernet physical tpmii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration:autonegotiation=on broadcast=yes driver=r8169driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fwlatency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources:irq:27 ioport:4000(size=256) memory:f6000000-f6000fffmemory:f4000000-f4003fff memory:fc000000-fc01ffff
keithmart@keith-ubuntu:~$ 

Regards

Keith

Leeds UK

---

### Post by howefield on 2017-04-27
Does the connection work ok with an ethernet cable and what is the model of the router/modem ?

---

### Post by philhughes on 2017-04-27
One thing to check is that your keyboard is correctly set up for the UK. Otherwise, if you have non-alphanumeric characters in your password, you may not actually be typing the correct password (eg pound gets swapped for #).

---

### Post by keithmart2 on 2017-04-29
Hi Guys

Thanks for the suggestions.

I have installed the 32 bit version and it is now working ok.

The laptop is a 64 bit machine, so it SHOULD have been ok, but who knows.

I will now get on with learning the vagaries of ubuntu

:confused::confused::D:D

Regards

Keith

Leeds uk

---

