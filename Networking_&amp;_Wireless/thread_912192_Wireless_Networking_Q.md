---
title: "Wireless Networking Q"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by bokodasu on 2008-09-06
I had Ubuntu installed, and everything worked fine. It got to the point where I couldn't upgrade it any more (too mighty for my ancient laptop), so I just wiped everything and installed Xubuntu 8.04.

I have a Xircom 802.11b wireless network card. The system sees the card and everything seems to be configured like it was under Ubuntu. My WAP (a Linksys D-Link 524) sees the laptop as connected to it, and recognizes when I turn it off, reboot, etc. The laptop, however, doesn't connect to anything. If I try to ping my router, it says "Network is unreachable". I've tried turning off security on the router, which doesn't help.

Last time I did this, it all just kind of worked, so I really don't know much about network configuration in Linux. Thanks!

---

### Post by Kevbert on 2008-09-06
Please post the output of 
```
lspci
iwconfig
```

---

### Post by bokodasu on 2008-09-06
Well, now I really don't know what's going on, because before when I ran iwconfig it did have my ESSID in it, and now it says "tsunami", even though it's still right in "Network Settings"

```
lspci:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus Bridge (Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus Bridge (Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS TEchnology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

iwconfig:

lo		no wireless extensions

eth0	IEEE 802.11-DS ESSID:"tsunami"
	Mode:Managed Frequency:2.437 GHz Access Point: Invalid
	Bit Rate:11 Mb/s Tx-Power=15 dBm Sensitivity=0/65535
	Retry limit:16 RTS thr:off Fragment thr:off
	Power Management:off
	Link Quality=0/100 Signal level=-95 dBm Noise level=0 dBm
	Rx invalid nwid:3584 Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0 Invalid misc:1059 Missed beacon:0
	
wifi0	IEEE 802.11-DS ESSID:"tsunami"
	Mode:Managed Frequency:2.437 GHz Access Point: Invalid
	Bit Rate:11 Mb/s Tx-Power=15 dBm Sensitivity=0/65535
	Retry limit:16 RTS thr:off Fragment thr:off
	Power Management:off
	Link Quality=0/100 Signal level=-95 dBm Noise level=0 dBm
	Rx invalid nwid:3584 Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0 Invalid misc:1059 Missed beacon:0
```

---

### Post by Kevbert on 2008-09-07
It doesn't appear under the commands shown, so I assume it's a PCMCIA card and not USB.  Please quote everything you can on the model, revision etc.  There seems to be a few posts on the forum for different Xircom cards.  The card is not powered which suggests you may need firmware.  You could try
```
sudo ifconfig eth0 up
```
or
```
sudo ifconfig wifi0 up
```
in terminal to see if you can power up the wireless and then
```
iwlist scanning
```
to see if any networks are available.  If this does not work, it confirms that you need firmware drivers.

---

