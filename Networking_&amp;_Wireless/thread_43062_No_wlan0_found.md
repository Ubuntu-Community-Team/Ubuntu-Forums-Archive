---
title: "No wlan0 found"
date: 2005-06-20
forum: Networking &amp; Wireless
---

### Post by stkaplan on 2005-06-20
I'm using a D-Link 122 USB wireless adapter with a fresh Ubuntu install, and I'm having quite a problem setting it up. I've tried what all the other forums have said, but I get errors during the process.

I installed linux-wlan-ng through Synaptic. No problems there.
Then I ran "modprobe prism2_usb prism2_doreset=1" without problems.
Then I ram "wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable" but got the error "wlanctl-ng: No such device"

Also, wlan0 does not show up in ifconfig or iwconfig.

Running /etc/init.d/wlan (which I thought might help me, not sure) gives me the error "/etc/wlan/shared: line 91: /etc/wlan/shared.*: No such file or diectory"

Is there something I have to do to set up my wireless that I'm missing? I couldn't find a way to add new interfaces through the Newtorking manager.

---

### Post by antwerx on 2005-06-20
Hello - 

Wireless card config can be very frustrating with a device that is not [supported](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) .

I highly suggest that you splurge for one of the devices from the supported hardware list that 'works out of the box' . 

I use a Netgear  WG511T PCMCIA card for my laptop that ended a week of trying and cussing and tweaking and cussing etc.

Hope this helps.  :)

---

