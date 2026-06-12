---
title: "Usb ax88179 based network adpater needs to be replug after boot"
date: 2019-11-09
forum: Networking &amp; Wireless
---

### Post by pedroply on 2019-11-09
Hi, 

I have a very basic home server made from a very cheap hp desktop. It has a proprietary motherboard which only supports 100Mbits\s on the Ethernet adapter and no available pci slots for any sort of expansion.. So I decided to buy a Gigabit Ethernet Adapter since it does have 2 USB3.1 on the back! I had some problems since ubuntu wasn't automatically starting the card up, don't no why, but now it runs fine. That is until the pc is restart, where the card seems to hang and ubuntu cant initialize it nor can I do it manually with ifconfig <card> up. I really have to unplug it and plug it back in for it to work. This is quite annoying since every time the pc needs to restart/loses power I have to physically go there and resolve it. Any one had similar experiences? 

The ethernet adaptar is also a hub with 3 extra USB3.1 ports which I though was a good idea but don't know if it is interfering or not. I also have an external hard drive connected to the other USB3.1 port an it mounts on boot using fstab without any problems. 

This is the output of "lshw -class network" referent to the new card:
```

description: Ethernet interface
       physical id: 2
       logical name: enx000088ab3d8b
       serial: 00:00:88:ab:3d:8b
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a driverversion=22-Aug-2005 duplex=full firmware=ASIX AX88179 USB 3.0 Gigabit Et ip=192.168.1.91 link=yes multicast=yes port=MII speed=1Gbit/s

```

Also, I'm running Ubuntu 18.04.3 LTS, 4.15.0-66-generic

Thanks in advance!

---

### Post by pedroply on 2019-11-13
Hi, 

Today I had to remove the pc and disconnect it from power. When I connected the network card seemed to boot just fine. The only difference was that I also connected the on board card as well. If something odd comes up I will post here.

---

### Post by pedroply on 2019-11-13
So I did some more digging and apparently it still doesn't work after booting with or without the other card connected. 
Found a simple script that would allow me to simulate a usb unplug and plug, but after using it although the card works, it only performs to 100mbps! even though it showed both on lshw and ethtool that the link size and capacity were 1000mbps or 1gbps.
 To get this 100mbps readings I was using iperf, ran multiple tests over the network to ensure it wasn't causing any bottleneck and could indeed acheive gigabit speeds using another computer as iperf server an a laptop connected to the same switch has the hp server. 

 I solved this by running "netplan apply" and only then the card worked has expected. 
Setting the script to run at boot has a service makes it work has desired but I imagine there are more elegant solutions available. 

I will leave it here shall anyone encounter the same problem:
```

#!/bin/bash


port="6-2" # as shown by lsusb -t: {bus}-{port}(.{subport})


bind_usb() {
  echo "$1" >/sys/bus/usb/drivers/usb/bind
}


unbind_usb() {
  echo "$1" >/sys/bus/usb/drivers/usb/unbind
}


unbind_usb "$port"
# sleep 1 # enable delay here
bind_usb "$port"
sleep 5 #needs to wait for the card otherwise it will not process limiting it to 100mbps somehow


netplan apply

```

---

### Post by jetsam on 2019-11-14
Yes, I have similar hang-ups with my usb audio interface / recording studio-in-a-box-thing.  I think it's a bios issue, but I'm not sure.

Something goes wrong in setting up the usb bridges, and I'm almost certain it's at a low level.  Unplug/replug can kick-start the system into re-initiating the usb systems...  But the problem comes back sometimes, and I haven't got a very good handle on what triggers it.  Having other usb devices connected sometimes causes it to happen, but not always.  I can always trigger it by turning off the audio interface and then starting up the computer.  It sometimes causes the whole system to hang in a worst case scenario, but a few reboots will almost always clear it up.

Mysteries...

---

