---
title: "[SOLVED] Wireless works with Live CD, but not when installed"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by oneaustin on 2008-07-01
I ran the live CD on my laptop (Acer  AS5610Z-2328-VHP-PMDT2060/1G/120/CAM/15.4  US) and it showed circuit card icon next to the networking icon.  It said it need to install the driver.  I connected by Ethernet, clicked ok and it began working.  It found all nearby networks automatically, connected to the one I chose and worked well.

Then I installed Ubuntu (8.04) and the wireless doesn't work.  It doesn't have the hardware listed as in need of a driver, and all wireless options are greyed out.
I searched the help file and ran "sudo lshc -C network" and saw the name of my card listed, but it said * Network Disabled.  I couldn't find anything else in help files.  Does anyone have any suggestions?
Thank you

---

### Post by chili555 on 2008-07-01
> Does anyone have any suggestions?Sure, two of them, in fact. First, please post your ```
sudo lshw -C network
```Second, is the wireless switch on or off?```
sudo cat /var/log/messages | grep -i switch
```

---

### Post by oneaustin on 2008-07-01
From "sudo lshw -C network" i get ```
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:cc:55:68
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:00:1c:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

Fro the second question:
```
:~$ sudo cat /var/log/messages | grep -i switch
Jun 30 17:39:24 a-book kernel: [   18.105061] SMP alternatives: switching to UP code
Jun 30 17:39:24 a-book kernel: [   18.941207] SMP alternatives: switching to SMP code
Jun 30 17:39:24 a-book kernel: [   19.437601] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 30 17:39:24 a-book kernel: [   36.854609] input: Lid Switch as /devices/virtual/input/input3
Jun 30 17:39:24 a-book kernel: [   36.854734] ACPI: Lid Switch [LID]
Jun 30 18:05:44 a-book kernel: [   15.177789] SMP alternatives: switching to UP code
Jun 30 18:05:44 a-book kernel: [   16.007644] SMP alternatives: switching to SMP code
Jun 30 18:05:44 a-book kernel: [   16.505475] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 30 18:05:44 a-book kernel: [   33.995614] input: Lid Switch as /devices/virtual/input/input3
Jun 30 18:05:44 a-book kernel: [   33.995736] ACPI: Lid Switch [LID]
Jun 30 18:16:09 a-book kernel: [   29.346844] SMP alternatives: switching to UP code
Jun 30 18:16:09 a-book kernel: [   30.187316] SMP alternatives: switching to SMP code
Jun 30 18:16:09 a-book kernel: [   30.684188] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 30 18:16:09 a-book kernel: [   47.577736] input: Lid Switch as /devices/virtual/input/input3
Jun 30 18:16:09 a-book kernel: [   47.577861] ACPI: Lid Switch [LID]
Jul  1 03:16:37 a-book kernel: [   24.685736] SMP alternatives: switching to UP code
Jul  1 03:16:37 a-book kernel: [   25.526830] SMP alternatives: switching to SMP code
Jul  1 03:16:37 a-book kernel: [   26.021462] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul  1 03:16:37 a-book kernel: [   43.617818] input: Lid Switch as /devices/virtual/input/input3
Jul  1 03:16:37 a-book kernel: [   43.617944] ACPI: Lid Switch [LID]
Jul  1 14:59:18 a-book kernel: [   16.854446] SMP alternatives: switching to UP code
Jul  1 14:59:18 a-book kernel: [   17.694228] SMP alternatives: switching to SMP code
Jul  1 14:59:18 a-book kernel: [   18.190156] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul  1 14:59:18 a-book kernel: [   35.544213] input: Lid Switch as /devices/virtual/input/input3
Jul  1 14:59:18 a-book kernel: [   35.544338] ACPI: Lid Switch [LID]

```

Does that help/answer your questions?

---

### Post by oneaustin on 2008-07-05
Can anyone help me out?

---

### Post by oneaustin on 2008-07-07
> **oneaustin said:**
> Can anyone help me out?

Help please?
Anyone?

---

### Post by chili555 on 2008-07-08
Please hook up the ethernet cable again and try:```
sudo apt-get install b43-fwcutter
```Does your wireless come to life?

---

### Post by oneaustin on 2008-07-08
<code>austin@a-book:~$ sudo apt-get install b43-fwcutter
[sudo] password for austin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter
austin@a-book:~$ </code>
Did I do something wrong?

---

### Post by chili555 on 2008-07-08
When you open System-Administration-Synaptic; select Settings-Repositories. Do you have *main, universe, restricted* and *multiverse* enabled? Press 'Reload' and search for *b43-fwcutter* there and install it.

---

### Post by oneaustin on 2008-07-08
I ran the update manager (237 updates) and restarted.  Now it lets me connect wirelessly by manually inputing the SSID, etc. but it doesn't find wireless networks automatically.
I also noticed that the wireless signal quality is much lower than when I ran Vista on this same machine in the same positions and router.
How can I set it to tell me what networks are available?

---

### Post by oneaustin on 2008-07-11
I ran into problems installing b43-fwcutter, it couln't find all files....
However, I did run the update utility and after the reboot, it found all the nearby networks.:)

---

