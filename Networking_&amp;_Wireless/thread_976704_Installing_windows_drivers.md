---
title: "Installing windows drivers"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by monty40 on 2008-11-09
How do you install window drivers for wireless network Card Adapter?

Thanks

---

### Post by cariboo on 2008-11-09
MAke sure the live cd is available in System-->Administration-->Software Sources then go to System-->Administration-->Synaptic Package Manager and search for ndisgtk, when the package has been found right click on it and mark for installation, this will also mark ndiswrapper-utils and Ndiswrapper-common for installation. After installation go to System-->Administrations-->Wireless Driver, or something to that effect. I don't have it installed as my usb device is detected and installed automagically.

Jim

---

### Post by abooks on 2008-11-10
I'm trying to install two things on my desktop, which I just converted from Vista (feh!) to 8.10. One is the verizon broadband dongle USB 720, and the other is my printer, a HP Office jet K80. Do I need to pitch both out the window and buy something that Ubuntu will see, or are there drivers for them? 

Thanks from the rankest of noobs.

---

### Post by cariboo on 2008-11-10
I can't help you with the verizon dongle without a lot more information, but your HP printer should be easy to setup. Go to System-->Administration-->Synaptic Package Manager and search for **hplip-gui**, then install it. This will walk you through the setup of your printer. HP is one of the most well supported printer manufacturers. I've got an old HP Laserjet 5P that I can setup with my eyes closed.

As for your dongle, can you post the output of:

```
lsusb
```

and

```
sudo lshw -C network
```

in your next post. The above commands must be done in a Applications-->Accressories-->Terminal.

Jim

---

### Post by anomad on 2008-11-10
I am having similar wireless issues. I upgraded to 8.whatever last night from 6 something and now neither my USB card or my old d-link plug in card work?  

They both worked automagically before?  ubuntu sees them when I do a port scan thing, but internet no workie. 

I am having to switch back and forth between puppy to research then try things.

I don't know how to add the devices as network devices? How do I tell ubuntu to "use this device"?

---

### Post by abooks on 2008-11-11
OK Cariboo, I finally got the codes you asked about, and a machine and place I can send them.

First, the device name:

BUS 004, Device 002 ID1410:2110 Novatel Wireless Ovation U720/MCD3000

Next, the analysis:

 description: Ethernet interface 
       product: 82562V 10/100 Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 02 
       serial: 00:19:d1:37:b6:ef 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 56:a6:78:2e:fd:c7 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

Thanks for your patience!

Walt

---

