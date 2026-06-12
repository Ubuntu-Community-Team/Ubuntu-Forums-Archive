---
title: "not detecting my hp printer"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-09-03
I'm trying to get an HP psc 1315 all-in-one working, but it's not being detected. The output for lpinfo is
```
network ipp
direct scsi
network lpd
network socket
file cups-pdf:/
network beh
network http
network smb
direct hp
direct hpfax
```

so it *seems* to see something, but lsusb only turns up
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have hplip installed, so I don't know what else I'm supposed to do to get the thing working.

---

### Post by Chris1274 on 2010-09-03
.

---

### Post by Chris1274 on 2010-09-03
Well, I have no idea what I did, but hp-setup worked like a dream on the second try. Perhaps it was rebooting after installing python-qt4? All I know is that the printer was detected after I plugged it back in.

Only now it's eating the paper (obviously not an Ubuntu issue ;))

---

### Post by sydbat on 2010-09-03
> **Chris1274 said:**
> Well, I have no idea what I did, but hp-setup worked like a dream on the second try. Perhaps it was rebooting after installing python --qt4? All I know is that the printer was detected after I plugged it back in.

Only now it's eating the paper (obviously not an Ubuntu issue ;))Sometimes a reboot is all you need. And I had a similar printer that started eating paper, had to buy a new one (something inside broke and that was it for the printer).

---

### Post by Chris1274 on 2010-09-03
All it was in my case was a little plastic bag that somehow got stuck in there that was jamming things up. I pulled it out and it works great now.

I should add how much I appreciate Ubuntu here. This printer had been sitting around unused for about a year after I swtiched from windows XP to windows 7. The software it came with wasn't "compatible" anymore. Ubuntu has saved me from throwing another few hundred bucks at a new printer.

---

