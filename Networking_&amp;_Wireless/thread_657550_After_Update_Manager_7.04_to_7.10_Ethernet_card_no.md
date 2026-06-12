---
title: "After Update Manager 7.04 to 7.10 Ethernet card not working on Dell 530"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by AdamTheNewbie on 2008-01-03
Hello,
   
    I just upgraded my Dell 530 from Ubuntu Feisty (installed by Dell) to Gutsy (Update Manager).
    
    Now the network card (eth0) is not being loaded. Unfortunately, I’m somewhat fresh and don't 
    know how to proceed. Any help is appreciated. 

	The System – Administration – Network Tools only shows the loopback interface.

dmesg | grep eth
returns nothing.

lspci -v|grep -i ethernet
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)

ifconfig only shows the loopback:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:330889 (323.1 KB)  TX bytes:330889 (323.1 KB)

uname -r
2.6.22-14-386

The e1000 driver is in a subfolder unlike all the other drivers:
root@ubuntu:/lib/modules/2.6.22-14-386/kernel/drivers/net# ls -al e1000
total 150
drwxr-xr-x  2 root root   1024 2008-01-02 22:25 .
drwxr-xr-x 23 root root   3072 2008-01-02 22:25 ..
-rw-r--r--  1 root root 147644 2007-12-18 02:34 e1000.ko
modprobe returns with no information:
root@ubuntu:/lib/modules/2.6.22-14-386/kernel/drivers/net# modprobe e1000
root@ubuntu:/lib/modules/2.6.22-14-386/kernel/drivers/net# 

root@ubuntu:/var/run/network# lshw
ubuntu                    
    description: Desktop Computer
    product: Inspiron 530
    vendor: Dell Inc.
    version: OEM
    serial: xxxxxx
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5
    configuration: boot=normal chassis=desktop uuid=xxxxx-5900-1047-8056-C3C04F384631
  *-core
       description: Motherboard
       product: 0RY007
       vendor: Dell Inc.
       physical id: 0
       serial: ..xxxxxx.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.0.5 (09/14/2007)
          size: 128KB
          capacity: 1984KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot

...SNIP...
   *-network UNCLAIMED
             description: Ethernet controller
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
...SNIP...

root@ubuntu:/# ifup -a
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
 
I then went to Intel and downloaded this archive and only got so far.
root@ubuntu:/home/adam/MyNetwork/e1000-7.6.12/src# sudo make install
Makefile:71: *** Linux kernel source not found in any of these locations:
Makefile:72:                
Makefile:73: *** Install the appropriate kernel development package, e.g.
Makefile:74: *** kernel-devel, for building kernel modules and try again.  Stop.
root@ubuntu:/home/adam/MyNetwork/e1000-7.6.12/src# 

Thanks in advance for any hints on how to proceed!

Adam.

---

### Post by AdamTheNewbie on 2008-01-09
I spent a lot of time head-scratching. In the end the fix was simple:

The update was booting the “-386” kernel.

I changed the default to the -generic kernel. 

Network problems went away.

I’m sure this would have been obvious to the more experienced folks...

Hope this helps someone.

Adam.

---

