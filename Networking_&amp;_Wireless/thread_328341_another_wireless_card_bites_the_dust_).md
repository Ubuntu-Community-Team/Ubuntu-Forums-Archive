---
title: "another wireless card bites the dust :)"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by jurgenfr on 2006-12-30
Hello all,

I have followed this tutorial : 

[URL="https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-1e63934359df5734b0d85f653110de7e4ba224df"]https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-1e63934359df5734b0d85f653110de7e4ba224df
[/URL]

Everything works until I come to Step 6. iwconfig doesn't show wlan0.

Any ideas ?

P.S. I'm working on HP Pavilion dv6113, AMD Turion 64 Mobile Technology MK-36

---

### Post by Metaljaz on 2006-12-30
what does iwconfig show?

---

### Post by jurgenfr on 2006-12-31
I get this instead :

> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



thanks for helping out.

---

### Post by jurgenfr on 2006-12-31
I'm going to try the Windows 2000 drivers. Maybe that helps.

---

### Post by adamonline on 2006-12-31
Do you have a physical wired interface card named eth0?  Or is it supposed to be the wireless card?  Step 6 in the tut mentions that... 

From the tutorial:
> (If your wireless device initially shows up as eth1, go back to step 2 and comment out the eth1 line in /etc/iftab. Then resume the rest of the instructions. If you don't comment out the eth1 entry, ndiswrapper won't be able to alias the device as wlan0.) 

Sorry, you don't mention what all you have, so that's my .02 ;)

---

### Post by jurgenfr on 2007-01-01
Yes, I have a wired card eth0.
Do I have to comment that one out in /etc/network/interfaces to use the wireless card wlan0 ?

---

### Post by jurgenfr on 2007-01-01
I'll post my logfile /var/log/syslog :
maybe someone can read this, and tell me what to do

> Jan  1 16:29:44 relinda kernel: [   37.758924] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Jan  1 16:29:44 relinda kernel: [   37.759094] PCI: No IRQ known for interrupt pin A of device 0000:03:00.0. Probably buggy MP table.
Jan  1 16:29:44 relinda kernel: [   37.759117] PCI: Setting latency timer of device 0000:03:00.0 to 64
Jan  1 16:29:44 relinda kernel: [   37.762073] ndiswrapper: request for IRQ 0 failed
Jan  1 16:29:44 relinda kernel: [   37.762221] ndiswrapper (miniport_init:270): couldn't initialize device: C000009A
Jan  1 16:29:44 relinda kernel: [   37.762226] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
Jan  1 16:29:44 relinda kernel: [   37.762235] unregister_netdevice: device eth%%d/dfbf1000 never was registered
Jan  1 16:29:44 relinda kernel: [   37.762245] ndiswrapper (miniport_halt:326): device dfbf1260 is not initialized - not halting
Jan  1 16:29:44 relinda kernel: [   37.762247] Trying to free free IRQ0
Jan  1 16:29:44 relinda kernel: [   37.762256] ndiswrapper: device eth%%d removed
Jan  1 16:29:44 relinda kernel: [   37.762271] ndiswrapper: probe of 0000:03:00.0 failed with error -22
Jan  1 16:29:44 relinda kernel: [   37.762607] usbcore: registered new driver ndiswrapper


Thanks

---

### Post by jurgenfr on 2007-01-01
Ok, I got it working so far.

This was my solution : [http://http://www.linuxquestions.org/questions/showthread.php?t=507003]("http://http://www.linuxquestions.org/questions/showthread.php?t=507003")

Is was using the wrong version of ndiswrapper.

Thanks to all for helping me. :)

---

