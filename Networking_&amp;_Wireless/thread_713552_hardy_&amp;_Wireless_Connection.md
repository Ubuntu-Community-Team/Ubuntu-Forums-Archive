---
title: "hardy &amp; Wireless Connection"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by keypad4s on 2008-03-02
I'm playing with Hardy Heron and have it installed on my laptop. Problem is after installation and software update my wireless network card stopped working. Heres the thing, If i choose to boot with ubuntu hardy 2.6.24-10-generic, the wireless work but the video has an error. If I choose ubuntu hardy 2.6.24-11-386, everything but the network card which is PRO/Wireless 4965 AG or AGN Network Connection. any suggstion would be helpful. also i'm still a newby to linux itself but i learning.

the lspci  shows:
```
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
```

the  sudo lshw -class network:
```

 *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by rustybronco on 2008-03-02
a few things you can do...
Keep playing with hardy for a while it will come around, hardy is still alpha stage.

search on the PRO/Wireless 4965 AGN or just 4965,
I thought someone with in the last few days/weeks had found a solution for that chipset.
I would use 7.10 and try the recommended method on anything but hardy (it breaks from time to time )

you can use ndiswrapper + the proper drivers  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

or if you don't mind trying it...install 7.10 and upgrade your kernel to hardy's kernel ( it may break also! )

---

### Post by sm1l3 on 2008-04-24
well I upgraded today and lost the wlan0 interface.

snip from  lshw -C network


*-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965



***Notice no Logical Name ***

 dmesg|grep iwl

[   36.945441] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   36.945446] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   36.945543] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   37.902539] iwl4965: Radio disabled by HW RF Kill switch
[  460.394288] iwl4965: Error sending REPLY_CARD_STATE_CMD: time out after 500ms.
[ 2393.301160] iwl4965: Radio disabled by HW RF Kill switch
[ 2417.754857] iwl4965: Error sending REPLY_CARD_STATE_CMD: time out after 500ms.

*** I manually changed the  /sys/bus/pci/drivers/iwl4965/*/rf_kill to see if that would make a difference and I noticed the error ****

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

***Don't even see it /etc/network/interfaces***

snip from lspci -nn

10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)


Thoughts?

---

### Post by R3T on 2008-04-24
Hi,
I juz updated to 8.04 this morning... and now... my cpu is always running at 100% when I use wifi to go online... any fixes? I'm using a intel 915 chipset pentium M with intel wireless bg

kinda regret updating...

---

### Post by sm1l3 on 2008-04-25
Actually I think my issue was related to some interrupt, ioport or DMA conflict. After disabling serial port and parallel port in the BIOS my wifi works. The rational for disabling those ports is a new interface appeared called 'pan0' after the upgrade and it seemed to be associated with the BlueTooth. *shrug* I wish I understood more about what occured and why both the BlueTooth and wifi work today.

---

### Post by azeemarif on 2008-04-28
Hello,

I had problems with Intel 3945abg wireless on Ubuntu 8.04 but everything was fixed by one single command

------------------------------------------------------------
sudo apt-get install linux-backports-modules-hardy-generic
------------------------------------------------------------


~Ar

---

