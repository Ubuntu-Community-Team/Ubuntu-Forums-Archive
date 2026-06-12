---
title: "Linksys WMP54GS-RM Compatibility"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by brimorse on 2009-08-12
Has anyone installed a Linksys WMP54GS-RM with Jaunty and gotten it to work? I am considering purchasing the card but can't determine the maker of the chipset to check it against matrices available through this forum.
 
Any input is greatly appreciated!

---

### Post by ibuclaw on 2009-08-12
It should be a Broadcom or RaLink chipset. Either way it should work OOB Perfect.

Reference site: [http://linux-wless.passys.nl](http://linux-wless.passys.nl)


**edit: **no wai! I have the exact same card in a Windows machine owned by a friend: WMP54GS-UK (The UK is just the Locale Suffix).
will edit this post in 30 seconds with card information.

**edit: **Okie doke. I think you will need to ensure that you are already connected to the internet first via ethernet.

I got the following:
```

lspci: 02:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

lshw:      *-network:1
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb

Installation:
System -> Administration -> Hardware Drivers
				-> Broadcom B43 wireless driver
					-> Activate

```
It seemed to go fine, but then I got an error through dmesg asking me to get the latest firmware from [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

Upon reviewing that page:
> 
in latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package:
sudo apt-get install b43-fwcutter
when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter)

So make sure that you are connected first before you try to install. :)

Regards
Iain

---

### Post by brimorse on 2009-08-12
That is the news I was hoping for!  Thanks Iain!

---

### Post by brimorse on 2009-08-12
Great information- I appreciate it!
 
I will order the card and give it a shot.  I will post the results...

---

### Post by brimorse on 2009-08-22
Just as a follow up to close the topic- got the card and installed it with no problems.  Worked right out of the box- Ubuntu found it and installed the driver on its own.

Thanks again for the input Iain- it was spot on!

---

