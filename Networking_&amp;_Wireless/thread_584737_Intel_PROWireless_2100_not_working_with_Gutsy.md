---
title: "Intel PRO/Wireless 2100 not working with Gutsy"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by elbono on 2007-10-21
Hi, 

I have an intel PRO/Wireless 2100 which used to work out of the box on Fiesty but now doesn't show up in the network manager. The Restricted Drivers manager shows that the "Lucent/Agere linmodem controller device" is enabled but "not in use" this may be a solution but I cannot figure out how to put this driver into use.

below is the revelant output from lspci

02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

and from iwconfig I get

eoin@Willo-The-Whisp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I can use the wireless fine on my XP partition but only the wired connection works with Gutsy.

Any help would be really really appreciated!

---

### Post by elbono on 2007-10-21
Hey after checking around the forums a bit more I ran this ```
lshw -C network
``` and this is my output

eoin@Willo-The-Whisp:~$ sudo lshw -C network
[sudo] password for eoin:
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:27:12:2f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.36 latency=32 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=34 mingnt=2

I think this is not what is should be from looking at what is posted on this thread [http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

Can anyone help me or give me any clues as where to start?

---

### Post by ElJuifos51 on 2007-10-21
Hey hi,

I have the same card and exactly the same problem.

I'm interested for any solutions

Thanks

---

### Post by Marcel Meijer on 2007-10-22
I have exactly the same problem but I found out that my wireless works fine when I boot from the live CD.

---

### Post by Marcel Meijer on 2007-10-23
When I reload the module with modprobe I get the following output:

000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  343.552000] ipw2100: eth1: Firmware 'ipw2100-1.3.fw' not available or load failed.
[  343.552000] ipw2100: eth1: ipw2100_get_firmware failed: -2
[  343.552000] ipw2100: eth1: Failed to power on the adapter.
[  343.552000] ipw2100: eth1: Failed to start the firmware.
[  343.552000] ipw2100Error calling register_netdev.
[  343.552000] ACPI: PCI interrupt for device 0000:02:03.0 disabled
[  343.552000] ipw2100: probe of 0000:02:03.0 failed with error -5

Does this help?

Again it works fine when I boot from the live CD and used to work fine under Ubuntu 7.04.

---

### Post by jogeer on 2007-10-24
I have the same card and the same problem. The wireless worked for a while after installing gutsy. Then, it just stopped. I have no idea why.

{bump}

---

### Post by marioquark on 2007-10-25
> **jogeer said:**
> I have the same card and the same problem. The wireless worked for a while after installing gutsy. Then, it just stopped. I have no idea why.

{bump}

the problem was solved copying the firmware file ipw2100-1.3.fw in the /lib/firmware/<your kernel> directory

now i get no more kernel error, but the network manager continues not to work :(

what can i do?

---

### Post by marioquark on 2007-10-25
SOLVED!!!

just clean the /etc/newtwork/interfaces file, leaving in only the "lo" interface informations... ;)

cheers

---

### Post by Akhorahil on 2007-10-29
Hi all,

Copying the firmware file isn't needed. Apparently the kernel packaging has changed with gutsy, and firmware files and some other kernel modules are now placed in the linux-ubuntu-modules package. Installing the right package for the running kernel makes the wireless card work. (use uname -a to find out if the 386 or generic package is needed).

---

### Post by spockrock on 2007-10-29
I have a similar problem the card is detected, but it wont connect to a wireless access point, in both gutsy gibbon and opensuse 10.3

---

### Post by jogeer on 2007-10-29
Mine works now.

I reinstalled the linux-generic package and double checked that the laptop's wifi kill switch was not-a-killiln' (Fn+F2 toggles it on this laptop).

Not really sure which one solved the problem....

I hope this helps. :)

---

### Post by le_vainqueur on 2007-11-13
> **jogeer said:**
> Mine works now.

I reinstalled the linux-generic package and double checked that the laptop's wifi kill switch was not-a-killiln' (Fn+F2 toggles it on this laptop).

Not really sure which one solved the problem....

I hope this helps. :)

Reinstalling the package "linux-generic" worked for me too.  I didn't do anything to my switch

Thanks for the help!

---

