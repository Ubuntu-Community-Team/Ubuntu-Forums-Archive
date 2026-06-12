---
title: "Intel 3945ABG installed and recognized but not listed as device"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by tomwitt on 2007-05-12
I'm having a problem trying to get my wireless network card (an Intel 3495ABG) working.

I recently upgraded from Kubuntu 6.10 to 7.04 on my ThinkPad T60p.

lspci results - (the wireless hardware is seen)

[INDENT]lspci | grep -i net | grep -i controller
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
[/INDENT]

dmesg results - (firmware is loaded)

[INDENT]dmesg | grep -C 2 ipw
[   18.648000] input: Microsoft Natural Keyboard Pro as /class/input/input5
[   18.648000] input: USB HID v1.10 Device [Microsoft Natural Keyboard Pro] on usb-0000:00:1d.0-1.1
[   18.692000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   18.692000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   18.696000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   18.696000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   18.696000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   18.716000] pnp: Device 00:0a activated.
[   18.716000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[/INDENT]

lsmod results - (driver is loaded)

[INDENT]lsmod | grep ipw
ipw3945               118432  0
ieee80211              33608  1 ipw3945
[/INDENT]

lshw results - (hardware is recognized)

[INDENT]sudo lshw -C network
  *-network
[INDENT]       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:52:e0:21
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.1.45 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ee000000-ee01ffff ioport:3000-301f irq:16
[/INDENT]  *-network
[INDENT]       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:edf00000-edf00fff irq:21
[/INDENT][/INDENT]

iwconfig results - (no wireless devices found)

[INDENT]iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
irda0     no wireless extensions.
[/INDENT]

ifconfig results - (no device associated with wireless card)

[INDENT]ifconfig eth0      
          Link encap:Ethernet  HWaddr 00:16:41:52:E0:21
          inet addr:192.168.1.45  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fe52:e021/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:8942671 (8.5 MiB)  TX bytes:2484566 (2.3 MiB)
          Base address:0x3000 Memory:ee000000-ee020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
[/INDENT]

To complicate things (or, make things easier, take your pick), when I boot from the Kubuntu 7.04 live CD, the wireless card is seen and successfully enabled (complete with WPA).  I'd prefer not to have to do a complete reinstall of 7.04 (plus, that would be admitting defeat by a mere machine which is simply unallowable).  

I've rebooted using an earlier kernel version, removed then reinstalled the most recent kernel and associated drivers but that did not resolve the problem.

Any suggestions to help diagnose the problem and work toward a solution (short of a reinstall) would be greatly appreciated.

Thanks

-- Tom

---

### Post by pedroeloy on 2007-05-14
I'm new to ubuntu and linux, but i had a similar problem.

Check the file iftab under /etc ou /etc/networking it should map the macaddress to the interface and maybe that's what is wrong with your setup?

Regards,
PedroEloy

---

### Post by tomwitt on 2007-05-15
> **pedroeloy said:**
> I'm new to ubuntu and linux, but i had a similar problem.

Check the file iftab under /etc ou /etc/networking it should map the macaddress to the interface and maybe that's what is wrong with your setup?

Regards,
PedroEloy

I think you're onto something here.   I do have an iftab file which lists a mac address for eth1.  As I look more closely at the output of the lshw -C network command, it isn't showing a "serial:" listing.  

This brings up new questions:
[LIST=1]
[*] Why doesn't the command lshw -C networks doesn't show the 'serial:' line for the wireless card?
[*] At what point in the startup process does the serial/mac address get loaded and associated with the driver?
[*] How is the iftab file created?
[/LIST]

PedroEloy, I know you're new to linux and you probably don't yet have experience enough to answer these questions.  (I'm hoping someone else reading this post may have the answers and post a response).  I do want to thank you for responding since I think you've found something worth investigating as a next step in the troubleshooting process. 

-- Tom

---

### Post by tomwitt on 2007-05-15
Progress... it's working now!  Woohoo!

Issuing the command 'sudo modprobe -r ipw3945' gave the clue I needed.  It responded that it couldn't find /sbin/ipw3945d.

Looking around the forums I found a solution by gradedcheese in this thread ( [http://ubuntuforums.org/showthread.php?t=393448](http://ubuntuforums.org/showthread.php?t=393448) ) in which he recommends doing this
```

sudo cp /sbin/ipw3945d-2.6.20-12-generic /sbin/ipw3945d-`uname -r`
sudo modprobe ipw3945
sudo /sbin/ipw3945d-`uname -r`

```

As it turns out, I already had the ipw3945 daemon in /sbin appropriate for my kernel (the copy comand failed because the file existed).

I only needed to run that last line.  I'm curious why this doesn't happen automatically. 

I see on reboot I need to reissue the command "sudo /sbin/ipw3945d-`uname -r`" to get wireless working again. 

Hmm... I wonder if creating a symlink will allow the wireless network to start on reboot: 
    sudo ln -s /sbin/ipw3945d-`uname -r` /sbin/ipw3945d

Yes, it does. Cool!  (Although I'll have to remember to update this symlink when the kernel is updated).

Anyway, problem solved -- for the most part.

-- Tom

---

