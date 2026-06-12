---
title: "Wireless Network in Ubuntu Studio"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by SNR99 on 2010-02-07
Having tried Ubuntu 9.10, I decided Ubuntu Studio was more appropriate for my needs.  However, when I installed it, the wireless networking did not work.

This is strange as as soon as I first installed Ubuntu 9.10, the wireless networking worked fine and automatically detected my home network and all I had to do then was enter my password.  Ubuntu Studio does no such thing and there is no way as a newbie I can get it to work.

Can anyone help?

---

### Post by lotharmat on 2010-02-07
First things first; What wireless card do you have?

```
lspci
```

or

```
lsusb
```

---

### Post by SNR99 on 2010-02-07
Think this is what you are looking for...

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV41 [Quadro FX Go1400] (rev a2)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by SNR99 on 2010-02-07
I think my wireless adaptor is a Intel Corporation PRO/Wireless 2200BG.  As mentioned, this was identified no problems in Ubuntu but there is nothing in Ubuntu Studio on how to search for my home network.  Any ideas?

---

### Post by bkratz on 2010-02-07
> **SNR99 said:**
> I think my wireless adaptor is a Intel Corporation PRO/Wireless 2200BG.  As mentioned, this was identified no problems in Ubuntu but there is nothing in Ubuntu Studio on how to search for my home network.  Any ideas?

You can test scanning for wireless by entering the following in the terminal:

sudo iwlist scan

(will require the entry of your password with nothing echoed to the terminal, just hit enter when done)

---

### Post by orpheum on 2010-02-11
having the same problem with ubuntu studio

i did this suggestion

> **bkratz said:**
> You can test scanning for wireless by entering the following in the terminal:

sudo iwlist scan

(will require the entry of your password with nothing echoed to the terminal, just hit enter when done)

and got

```
lo     interface doesn't support scanning

eth0     interface doesn't support scanning

wmaster0     interface doesn't support scanning

wlan0  no scan results

pan0   interface doesn't support scanning
```

an explanation to this will be highly appreciated

thanks!

---

### Post by mcduck on 2010-02-11
Ubuntu Studio doesn't install the Network Manager by default, which is why you can't get wireless working like you do in normal Ubuntu installs. ;)

Just install network-manager-gnome yourself if you need it. I think the packgae is even included on the Ubuntu Studio DVD.

---

### Post by orpheum on 2010-02-11
thanks mcduck

---

