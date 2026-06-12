---
title: "Hardware information from network card"
date: 2005-05-14
forum: Networking &amp; Wireless
---

### Post by ola on 2005-05-14
Hi, 

I have some problems with one of my network cards (I use my ubuntubox as router/firewall). I get the feeling that the network is incredibly slow when connecting to the internal network card..

If I examine the dmesg output I can se this row
```
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
``` 
which tells me that my intel card runs at 100Mbit, full duplex.. and that seems fine

The other card is a 3com card. I can se the card from the dmesg output
```
3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
0000:00:0f.0: 3Com PCI 3cSOHO100-TX Hurricane at 0xa400. Vers LK1.1.19
```
But I can't find anymore output from this card..

To copy the Ubuntu 5.04 install image (~600MB) via the network takes ~10min which seems a bit to slow network speed, right?

Any ideas about where I can find more information about this would be great!

---

### Post by nad on 2005-05-14
You may wish to increase your send and receive buffers to 8192 and don't forget that your drive access speed has a hand in this.

You can use the drop down menu: Computer->System Configuration->Device Manager to view your hardware configuration.

---

### Post by ola on 2005-05-14
Here is the output from the: [Device Manager](http://oscar.onemanarmy.net/~ola/screenies/050514_3com.png). 

I'm really not sure if anything looks wrong? I can't se anything, sorry..

---

### Post by nad on 2005-05-14
Well... The 3com card is set at 100mb/s but I can't tell if it is running in full duplex. You may wish to review the driver manual for this card at the noted address.

The buffer size commands would be noted at mount time for your nfs shares: rsize=8192,wsize=8192

Hope this helps. 10 minutes isn't bad, but I should think that you would be able to halve that figure.

---

### Post by ola on 2005-05-15
The annoying thing is that I had the same problem when I ran Gentoo (before I installed Ubuntu). But for some reason I tripped over some option that should be passed too the module when it booted..

But now I can't fint that option (I have searched the 3c59x.c file without result... 

If it hadnt been such a mess to change card in this computer Ill be doing it right away..

Anyway, thanks alot for the help!

---

### Post by ola on 2005-05-15
I found a tool named vortex-config.. When I ran it, it looked like this

```

vortex-diag -p a400 -t 21 -a -e -m -f
vortex-diag.c:v2.14 12/28/2002 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Assuming a 3Com 3cSOHO100-TX adapter at 0xa400.
 Station address 00:04:76:d2:93:52.
  Receive mode is 0x07: Normal unicast and all multicast.
Initial window 0, registers values by window:
  Window 0: 0000 0000 0000 0000 f5f5 00bf 0000 0000.
  Window 1: 0000 0000 0000 0000 0000 0000 0000 2000.
  Window 2: 0400 d276 5293 0000 0000 0000 000a 4000.
  Window 3: 0000 0100 05ea 0000 000a 0800 0800 6000.
  Window 4: 0000 0000 0000 0058 0001 8880 0000 8000.
  Window 5: 1ffc 0000 0000 1ffc 0807 0000 0000 a000.
  Window 6: 0000 0000 0000 0000 0000 0000 0000 c000.
  Window 7: 0000 0000 8100 0000 0000 0000 0000 e000.
Vortex chip registers at 0xa400
  0xA410: 00000000 00000000 00000000 00000000
  0xA420: 00000000 00000000 00080000 00000004
  0xA430: 00000000 305fcfa1 00000000 00080004
  0xA440: 00cb3e9f 00000000 00000000 00000000
  0xA450: 00000000 00000000 00000000 00000000
  0xA460: 00000000 00000000 00000000 00000000
  0xA470: 00009000 00000000 00000000 00000000
  DMA control register is 00000000.
   Tx list starts at 00000000.
   Tx FIFO thresholds: min. burst 256 bytes, priority with 128 bytes to empty.
   Rx FIFO thresholds: min. burst 256 bytes, priority with 128 bytes to full.
   Poll period Tx 00 ns.,  Rx 0 ns.
   Maximum burst recorded Tx 0,  Rx 0.
 Indication enable is 0000, interrupt enable is 0000.
 No interrupt sources are pending.
 Transceiver/media interfaces available:  100baseTx 10baseT.
Transceiver type in use:  10baseT.
 MAC settings: half-duplex.
 Station address set to 00:04:76:d2:93:52.
 Configuration options 000a.
Saved EEPROM settings of a 3Com Vortex/Boomerang:
 3Com Node Address 00:04:76:D2:93:52 (used as a unique ID only).
 OEM Station address 00:04:76:D2:93:52 (used as the ethernet address).
  Device ID 7646,  Manufacturer ID 6d50.
  Manufacture date (MM/DD/YYYY) 11/11/2001, division H, product MM.
  No BIOS ROM is present.
 Transceiver selection: Autonegotiate.
   Options: negotiated duplex, link beat required.
 PCI Subsystem IDs: Vendor 10b7 Device 7646.
 100baseTx 10baseT.
  Vortex format checksum is incorrect (56 vs. 10b7).
  Cyclone format checksum is correct (0xcb vs. 0xcb).
  Hurricane format checksum is correct (0xcb vs. 0xcb).
 MII PHY found at address 24, status 7849.
 MII PHY found at address 0, status 784d.
 MII PHY 0 at #24 transceiver registers:
   3000 784d 0000 0000 01e1 45e1 0004 2001
   0000 0000 0000 0000 0000 0000 0000 0000
   0000 0081 1091 0000 0000 0005 2001 0000
   0000 2045 07cf 1c11 0011 1000 0000 0000.
 MII PHY 1 at #0 transceiver registers:
   3000 784d 0000 0000 01e1 45e1 0004 2001
   0000 0000 0000 0000 0000 0000 0000 0000
   0000 0080 0090 0000 0000 0005 2001 0000
   0000 2045 07cf 1c11 0011 1000 0000 0000.

```

Where the most interesting ouht to be this:

```

Transceiver/media interfaces available:  100baseTx 10baseT.
Transceiver type in use:  10baseT.
 MAC settings: half-duplex.

```

Now I just have to figure out how to force 100baseTx, full-duplex ^_^

I found some information here: [http://www.scyld.com/vortex.html](http://www.scyld.com/vortex.html)

> 
Special Usage Instructions
When loaded as a module the following variables may be set:
options 	 int[] 	 The media type override and card operation settings (See list below.)
....
4 	 100baseTx Symbol mode, valid for 3c595 only.
5 	100baseFx Symbol mode, valid for 3c595 only.
...
0x200 	 Add to above values to force full-duplex.

Note that the preferred method of using full duplex is to allow autonegotiation to take place. If you must force full duplex when communicating with older equipment use the full_duplex module parameter in preference to the options flag. 

Where do I set flags like this?

If I remove the module by hand
```
rmmod 3c59x
```
and then modprobe it with:
```
modprobe 3c59x options=4
```
and restart my network etc.. I get 2-3min to copy 600mb.. So I guess I'll have to find out how I can forde that 100mbit option for the network card.. 

I found a solution (thanks to the ppl on the Ubuntu IRC chanel):
I created a file in /etc/modprobe.d called 3c59x_o4 which contained the following
```
options 3c59x options=4 full_duplex=1
```
Rebooted and checked that the options were set
```
modprobe -c | grep 3c59x
options 3c59x options=4 full_duplex=1
```

and vortex-diag -p a400 -t 21 -a -e -m -f gives me:
```

Transceiver/media interfaces available:  100baseTx 10baseT.
Transceiver type in use:  100baseTX.
 MAC settings: full-duplex.

```

which seems to be correct and since the 600mb file takes 2 min, I'm happy!
Hope this will help someone! Thanks for the help!

---

### Post by nad on 2005-05-15
You're welcome.

Good work!

---

