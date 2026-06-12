---
title: "I have problem with USB RaLink"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by joojle on 2007-01-20
I have upgraded my ubuntu from 6.60 to 6.10. So i plug my usb wireless "Surecom ep-9001-g" to my computer but kernel does not load driver (maybe rt73usb) for my device.
please give me some solution
this is my output from lshw command
```
*-usb:3

             description: USB Controller

             product: USB 2.0

             vendor: VIA Technologies, Inc.

             physical id: 10.3

             bus info: pci@00:10.3

             version: 82

             width: 32 bits

             clock: 33MHz

             capabilities: ehci bus_master cap_list

             configuration: driver=ehci_hcd

             resources: iomemory:ec800000-ec8000ff irq:177

           *-usbhost

                product: EHCI Host Controller

                vendor: Linux 2.6.17-10-386 ehci_hcd

                physical id: 1

                bus info: usb@4

                logical name: usb4

                version: 2.06

                capabilities: usb-2.00

                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s

              *-usb UNCLAIMED

                   description: Generic USB device

                   product: 802.11 bg WLAN

                   vendor: Ralink

                   physical id: 6

                   bus info: usb@4:6

                   version: 0.01

                   capabilities: usb-2.00

                   configuration: maxpower=300mA speed=480.0MB/s


Bus 004

```

my device doesn't show in network section

thank you

---

### Post by hal10000 on 2007-01-20
Your driver should be rt2570, so first try (in aterminal window) [COLOR="Red"]lsmod |grep rt2570[/COLOR]
If you get no answer, just do [COLOR="Red"]sudo modprobe rt2570[/COLOR]
Then plug in your device and see what happens. You shold use [COLOR="Red"]sudo lshw[/COLOR] because then it gives you info about the driver.

---

### Post by joojle on 2007-01-20
I try those command, but it still not work. 
before I use 6.10 I use 6.60, In dapper, (In that time I have internet access with another wireless with ndiswrapper) I download and complie driver and it work fine.
 In 6.10 I heard that It can load driver automatically (on my friend computer).  and I look in the module folder it have many driver of Ralink (2570, 73usb, ...etc.) but why it can't recognize my wireless.

---

### Post by hal10000 on 2007-01-20
If you have updated to edgy and noe you have another kernel version then you might have to recompile the driver you have once downloaded.
Are there any Ralink driver modules loaded after booting? You can see it with [COLOR="Red"]lsmod | less [/COLOR]

---

### Post by joojle on 2007-01-21
Thank you for you answer.
So I just want to use installed driver but it can't work so now i complie driver (on ralink site) and it work fine

---

