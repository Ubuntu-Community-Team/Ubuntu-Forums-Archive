---
title: "Belkin f5d6050 mystery"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by lhuggybear on 2007-08-15
I have the above USB adapter and 7.04 in dual boot configuration.

When booting in Ubuntu, the card does not get recognised. There simply is no wireless connection in the Network Manager.

If I then restart and, shame on me, reboot in XP, the connection gets established faultlessly. If I then restart again in Ubuntu, the wireless connection is automatically established and it has remebered previous properties and WEP of the adapter. I can then go on with my work. All well...

Except that at the next boot, the connection will be invisible again, until I get it started in Windows.

Please help...

---

### Post by lhuggybear on 2007-08-15
Please help... I am at a complete loss...

---

### Post by noob12 on 2007-08-15
I've seen this kind of problem for some USB adapters on cold boots vs. warm boots primed by Windows.  The causes I have seen are (a) that some firmware is being loaded by Windows that is not being loaded by Ubuntu, or (b) on cold boots the device has a different device id that the driver is not recognizing, so the device never gets claimed by the driver.  This happens because the device has two ids: one which identifies the device as a drive and one which identifies the device as a wireless ethernet adapter.

The fix for cause (a)  is to make sure the firmware is installed and will be loaded by the driver.  The fix for cause (b)  usually is to toggle some switch on the device which tells it to always look like a wireless ethernet device, and not look like a drive.  Some devices don't have switches and effectively can only be controlled by the driver to make this transition.  If so, moving to ndiswrapper + the windows driver *may* fix the issue.

Having finished that lecture, we need to do some diagnosis to figure out your situation.  Based on the results, I and others may be able to provide suggestions.

We need to gather this after both the cold boot and the warm Windows-primed boot.  Please collect the info and post it from both situations.
```

lsusb 

sudo lshw -C network

ifconfig -a

```

---

### Post by lhuggybear on 2007-08-16
Thanks a lot noob12...

My device has no switch at all, so it is a driver issue...
I have the driver, but I have no idea what to do with the driver in my new chosen environment (not to say that I am pretty proficient in Bill's old world)...

What is ndiswrapper?

---

### Post by noob12 on 2007-08-16
ndiswrapper is a kernel module and a set of utilties that allows you to take a standard NDIS windows network device driver and use it within linux.

Before we go there let's see the info that I had asked for earlier.

In your situation, since whatever driver you have seems to run fine after the Windows warm reboot,  we really want to do the minimal.
You can probably just install the right firmware file on Ubuntu or edit the device id mapping files to match what you have on cold boots.
If you are not already using ndiswrapper, then I think you won't need it.

---

### Post by lhuggybear on 2007-08-17
Hi Noob12... here are my data for both a cold and then a warm boot.

COLD

lsusb
Bus 005 Device 005: ID 1058:0900 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  

sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:87:f3:ec
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: iomemory:fcfe0000-fcffffff ioport:df40-df7f irq:18


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:87:F3:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xdf40 Memory:fcfe0000-fd000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


AND NOW WARM

lsusb
Bus 005 Device 003: ID 1058:0900 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0d5c:a002 Belkin F5D6050 802.11b Adapter
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  


sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:87:f3:ec
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: iomemory:fcfe0000-fcffffff ioport:df40-df7f irq:18
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:f1:2a:8b:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=0.100.5-78 ip=192.168.0.12 wireless=IEEE 802.11b


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:87:F3:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xdf40 Memory:fcfe0000-fd000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:30:F1:2A:8B:8D  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:f1ff:fe2a:8b8d/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17500 (17.0 KiB)  TX bytes:9523 (9.2 KiB)




Hope this helps you...
Thanks SOOOOOO much for taking the time to respond so clearly.

---

### Post by noob12 on 2007-08-17
So, good think we checked.  Because this is neither of the two problems I had suspected.  Here the  problem is that the device isn't even being detected on cold boot.

Notice the difference in the two **lsusb** outputs above.  In the cold boot, the device isn't even there.  It's not there with a different device id; it just doesn't show.
That explains the rest; it means the driver won't see it and will never set up the device.

See what happens after a cold boot if you just unplug and then again plug in the USB device.
Let me know.

---

### Post by lhuggybear on 2007-08-17
That of course DOES work. I can't imagine that I hadn't done that before, but obviously, I did not... Probably booted without the device and connected later, but that doesn't do the trick.

---

### Post by noob12 on 2007-08-17
OK.  Great to hear. 

This suggests you might be able to solve your problem fully by adjusting BIOS settings so that the device will get detected on boot.  Or it might be an Ubuntu / linux bug.

I'll try to do a bit more research, but at least you have a faster workaround now.

---

### Post by lhuggybear on 2007-08-17
Well, you should know by now I have no clue about what I am doing!!!!!!!!!!!!!!
So how do I adjust the BIOS...

Just joking, amazing what one learns by doing things like this, step by step. Beats the books...

---

### Post by noob12 on 2007-08-18
I looked around for more information.  It looks like several other people have discovered the unplug/replug solution, but I don't see any real solutions.

I can't give you clear guidance on the BIOS settings because that tends to be very specific to your machine.  I'm also not even sure there is a setting that will solve this and also work properly for both Windows and Ubuntu boots.

There might be some other readers on the forum that can help you do better than the unplug/replug solution as I'm sure you'll find that tiresome over time, perhaps already.

I wasn't able to find a bug about this on launchpad; you should consider filing one.  They will probably ask for your kernel version which you can get from **uname -r**.  I think you could pretty much just cut and paste the information you provided in your postings on this thread over there.

Please note: I will be away from the forum for the next week, so I won't be able to respond during that time.

---

