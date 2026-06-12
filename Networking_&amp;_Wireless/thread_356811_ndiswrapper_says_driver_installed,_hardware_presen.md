---
title: "ndiswrapper says driver installed, hardware present but lshw no driver installed ?"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by gavaiken on 2007-02-08
Hi,
    I have made some progress in getting my

D-link 520+ PCi wirless card

to work having started another thread yesterday. My problem has changed considerably so i thought it was work making a new thread.

I have blacklisted the default acx driver, installed ndiswrapper and configured it with the correct driver until I get to the stage where I can type

**sudo ndiswrapper -l** 
Installed ndis drivers:
gplus   driver present, hardware present 

I know the driver is correct as I got it from the wiki list, there's an entry for the exact card and chipset.

My problem however is that despite typing
> 
  sudo depmod -a
  sudo modprobe ndiswrapper

without error. The driver is still not associated with the card. 

Running dmesg gives...

> [17179890.024000] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
[17179890.044000] usbcore: registered new driver ndiswrapper

But i'm supposed to get a ndiswrapper: driver loaded... message?!!

sudo lshw tells me that my card is unclaimed and there is no configuration

 > *-network UNCLAIMED
                description: Network controller
                product: ACX 111 54Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:fe9fc000-fe9fdfff iomemory:fe9c0000-fe9dffff irq:5



After a reboot I get the exact same results, ndiswrapper says everything is perfect and everything else indicates there's no driver installed
and there are no wireless devices to configure.

 
Any ideas greatly appreciated!

Thanks,

Gav

---

### Post by dmizer on 2007-02-08
add the following line:
```
blacklist acx111
```
to the end of /etc/modprobe.d/blacklist

---

### Post by gavaiken on 2007-02-09
Hey, thanks for the suggestion, I added the line but no luck, the lshw report still reads exactly the same as above.

=(

Any other ideas?

---

### Post by dmizer on 2007-02-09
what does lsmod say?

---

### Post by ogrisel on 2007-02-11
I have the same problem here:

```

ptiyours% uname -r                                                                                                                                            
2.6.17-11-generic

ptiyours% sudo lshw -C network                                                                                                                                
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:dfdfc000-dfdfffff irq:177
  *-network
       description: Ethernet interface [snip]

ptiyours% ndiswrapper -l                                                                                                                                      
bcmwl5 : driver installed

ptiyours% lsmod |grep ndiswrapper                                                                                                                             
ndiswrapper           204436  0
usbcore               134912  4 ndiswrapper,ehci_hcd,uhci_hcd

ptiyours% ndiswrapper -v                                                                                                                                      
utils version: 1.9
driver version:        1.37
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
ptiyours% ndiswrapper -l                                                                                                                                      
bcmwl5 : driver installed

ptiyours% dmesg| tail -3                                                                                                                             
[17184432.960000] usbcore: deregistering driver ndiswrapper
[17184436.060000] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
[17184436.068000] usbcore: registered new driver ndiswrapper

```

If I modprobe bcm43xx (with the installed firmware with the cutter), the eth1 works but is very slow (feels like on an old 56k modem and speedtest.net confirms it).

Please also note that ndiswrapper used to work at full speed on this box before the last kernel upgrade from ubuntu edgy. I have also tried to use the ndiswrapper-utils-1.8 from the repository but I get the same behavior as with ndiswrapper compiled from the 1.37 src tarball ...

---

### Post by dmizer on 2007-02-12
well, i was looking for all of lsmod to see if there was possibly another module loading and conflicting with your card, but i have a hunch ...

just for trials sake, do this:
```
sudo modprobe -r uhci_hcd
sudo /etc/init.d/networking restart
```
if that doesn't work, try the same thing with ehci_hcd.

uhci_hcd drives usb1.0, so if all your usb ports are usb2 (most likely), you won't miss any functionality.  so if the above works for you, you should add uhci_hcd to the blacklist.

---

### Post by ogrisel on 2007-02-12
Hi again,

I have temporarly fixed the problem by selecting my old kernel in grub (2.6.17-10 instead of 11) and reverted my ndiswrapper conf in /etc/ndiswrapper to the first state that used to work with  2.6.17-10 (my /etc is under bzr revision control :)

FYI, my lsmod still shows a deps between ndiswrapper and  the usb modules :

```

ptiyours% lsmod |grep ndiswrapper                                                                                                                  
ndiswrapper           200724  0
usbcore               134912  4 ndiswrapper,ehci_hcd,uhci_hcd

```

So this is probably not the true source of the problem.

The current ndiswrapper I use version 1.34 from source. Maybe the true problem comes from the version of the windows driver in use. I cannot remember where I first found the one that works for me at the moment.

---

### Post by dmizer on 2007-02-12
yes ... but the kernel is what communicates with your hardware.

so what has happened to me in the past, and what MAY be happening to you, is that the new kernel has an irq conflict between the usb modules and your network card.  the old kernel may have the same deps, but without the irq conflict.

---

### Post by keflavich on 2007-03-11
I'm getting the same problems reported here but I've had no luck with the modprobe -r solutions

version: 2.6.17-11-386

lshw:
        *-network UNCLAIMED
             description: Network controller
             product: Dell Wireless 1390 WLAN Mini-PCI Card
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@03:00.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:b3200000-b3203fff

When I try /etc/init.d/network restart:
adam@adam-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth0.pid with pid 17518
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:92:65:9d
Sending on   LPF/eth0/00:16:36:92:65:9d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:92:65:9d
Sending on   LPF/eth0/00:16:36:92:65:9d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 41913 seconds.



adam@adam-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           198228  0 
usbcore               130304  2 ndiswrapper

The usbcore line did include ohci_hcd and possibly ehci and uhci also (I didn't check before modprobe -r 'ing them), but of course now doesn't.

If removing those modprobe entries is a fix, should I be doing something else?

Thanks,
Adam

---

