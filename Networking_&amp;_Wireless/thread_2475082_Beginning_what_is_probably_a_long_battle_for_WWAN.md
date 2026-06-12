---
title: "Beginning what is probably a long battle for WWAN"
date: 2022-05-16
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2022-05-16
I have a newish Lenovo ThinkPad X1 running Ubuntu 20.04 and paid the extra chunk to have a WWAN card installed. I got a SIM card, put it in, activated it at the provider's website ... and now I'm stuck. My provider is not on the list the wizard wants me to use, and do not have a specific Mobile Broadband service, though they advertise that use for their unlimited data-only plan. (I think I may accidentally have gone on the regular plan, based on the email they sent, but I do not think this makes a difference).

All the information I wind up providing is the APN I found by googling "APN [provider_name]."

This information is not retained. It just gives me the option to connect, endlessly, and then opens the same "connection wizard" dialog when I accept.

I also currently can't find my WWAN device. Here is what I have done in the command line, based on advice online.

```
snap install modem-manager
sudo modem-manager.mmcli -L

```

This returns

```
error: couldn't get bus: Could not connect: Permission denied
```

mmcli -L yields
```
    /org/freedesktop/ModemManager1/Modem/1 [manufacturer unknown] model unknown
```

At present, ```mmcli -m 1``` [the number, here "1," varies[ gives

```

  --------------------------
  General  |           path: /org/freedesktop/ModemManager1/Modem/1
           |      device id: 52031fac785b312d931ed9df76a25344d6fe8bc7
  --------------------------
  Hardware |      supported: gsm-umts
           |        current: gsm-umts
  --------------------------
  System   |         device: /sys/devices/pci0000:00/0000:00:1c.0/0000:08:00.0
           |        drivers: mhi_net, mhi-pci-generic
           |         plugin: foxconn
           |   primary port: wwan0at0
           |          ports: mhi_mbim0 (net), wwan0at0 (at)
  --------------------------
  Status   |          state: failed
           |  failed reason: sim-missing
           |    power state: off
           | signal quality: 0% (cached)
  --------------------------
  Modes    |      supported: allowed: any; preferred: none
           |        current: allowed: any; preferred: none

```

As far as I can tell, the SIM is in. I put it in the tray the only way it fit (contacts *up*, if the structural supports are down, but weirdly facing *down* rather than up relative to the base of the computer). 

I am probably missing any number of basic things. Any ideas what I should do would be much appreciated.

---

