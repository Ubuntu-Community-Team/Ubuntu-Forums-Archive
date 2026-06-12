---
title: "Netgear GA311r10 - No network connection, can't figure out why"
date: 2013-10-13
forum: Networking &amp; Wireless
---

### Post by stevejluke on 2013-10-13
I have a PCI network card: NetGear GA311.  I tried some trouble shooting to see what is wrong.  I used lspci -nn and got this:
```
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)

```When I get the verbose output with lspci -vv:
```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
    Subsystem: Netgear GA311
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at e800 [size=256]
    Region 1: Memory at fbeffc00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at fbec0000 [disabled] [size=128K]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: r8169

``` 

So I get that the device is there, looks to be recognized, and has a driver assigned to it (apparently).  But I get no blinking lights on the card, the no network connection.  When I do ifconfig I get this:
```
eth0      Link encap:Ethernet  HWaddr e0:91:f5:a0:39:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
As well as the lo.  lsmod gives me this:
```
r8169                  67446  0
```

modprobe r8169 doesn't give any feedback.  /etc/ifplugd/ifplugd.action doesn't exist (so I can't to /etc/ifplugd/ifplugd.action eth0 up or down).  ifup eth0 says "Ignoring unknown interface eth0=eth0" and ifdown eth0 says "Interface eth0 not configured."

Research suggests that the card should work well with Ubuntu.  As it is, I can't install packages or anything because I am not connected to the net.  Any suggestions on how to get this card working?

Thanks,
Steve

---

### Post by varunendra on 2013-10-14
Do you have any way to connect to internet on that system? If yes, please install ethtool -
```
sudo apt-get install ethtool
```

If not, replace above with -
```
apt-get install --print-uris ethtool
```
This one will give you download URIs for the package and its dependencies if any are required. You can then use this URI to download the packages on a different computer, then copy them back to this one > place them in an empty folder (say "eth") on your desktop, and install with -
```
cd Desktop eth
sudo dpkg -i *.deb
```

Once it is installed, please run the following commands and post back their output -
```
sudo ethtool eth0
cat /etc/network/interfaces
nm-tool
```

---

### Post by stevejluke on 2013-10-14
```
sudo apt-get install --print-uris ethtool
E: Package 'ethtool' has no installation candidate
```

---

### Post by stevejluke on 2013-10-14
Okay, I found it from a search.  Got ethtool installed.  output:

sudo ethtool eth0:
```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no
```
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]cat /etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

nm-tool:
```


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E0:91:F5:A0:39:21


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

---

### Post by varunendra on 2013-10-14
Eh, posted 'AFTER' your second last one.. please discard

[s]Doesn't look good. It is in the 'main' repository and so should not require an update to show up.

Can you try manually downloading and installing from here? The .deb package suitable to your architecture (32 or 64 bit). If using a version earlier than 12.04.3, try version 3.1, if on 13.04, try version 3.4.

Meanwhile please post the outputs of -
```
lsb_release -d
uname -mr
sudo lshw -C network
sudo mii-tool
nm-tool
cat /etc/network/interfaces
```[/s]

---

### Post by varunendra on 2013-10-14
> **stevejluke said:**
> 
```
Settings for eth0:
....
	Supported pause frame use: **No**
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: **[COLOR="#FF0000"]Symmetric Receive-only[/COLOR]**
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	**Duplex: [COLOR="#FF0000"]Half[/COLOR]**
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no
```
The pause frame support is normal (No) but the "Advertised pause frame use" value is something I've seen for the first time. Is the device on the other side a network switch or hub? What speeds and duplex does it support?

Please try -
```
sudo ethtool -s eth0 speed 10 duplex full autoneg off
```
This should change the connection mode to 10Mb/s full duplex. See if it allows you to connect (the connection LED should become steady). If yes, we can try speed 100 or even 1000 if the device on the other side supports it.

If the above fails, post back the output of -
```
sudo ethtool eth0
mii-tool
sudo ethtool -a eth0
```
..after running the "ethtool -s.." command given above.

---

### Post by stevejluke on 2013-10-14
So, the ethtool -s command finished with no error, but did't fix anything.  Output you asked for after doing the ethtool -s command:

sudo ethtool eth0
```
Settings for eth0:	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
```

mii-tool:
```
eth0: 10 Mbit, full duplex, no link
```

ethtool -a eth0 produced this:
```
Link detected: no
Pause parameters for eth0:
```
It also produced this error message:
```
Cannot get device pause settings: Operation not supported
```

---

### Post by varunendra on 2013-10-14
You didn't say anything about your 'other device' on the other side of the cable.
Is it a router/switch or hub?
Do you know what modes it supports? (speed/duplex) If not sure, are there any other computers connected to it to confirm that?

One more thing - have you tried changing the cable? Or somehow made sure it is not faulty?

---

### Post by stevejluke on 2013-10-14
Oh, sorry, I am plugged directly into the router.  It is 10/100/1000baseT full duplex.  The cable / port works fine in the computer I am using now to post to these forums.

---

### Post by varunendra on 2013-10-15
Frankly, I am out of ideas. The only one thing I can suggest is to try different duplex/speeds and changing the '**Port**' type as well. Currently it is of type "mii", which I suspect may be 'expecting' the link parameters from the other side, while the router may not be mii compatible.

Accordingly, please try -
```
sudo ethtool -s eth0 speed 100 duplex full **port [COLOR="#FF0000"]tp[/COLOR]** autoneg off
```
..and check "sudo ethtool eth0" again to see if it accepted the port type (Twisted Pair). The acceptable values to option "port" are "tp|aui|bnc|mii", and it is already set as "mii".

Not all settings are acceptable to all cards, so it is mostly a matter of trial and error.

There are a lot of things you can try with "ethtool" (check "man ethtool") but having no clear hint of what may be causing it to not detect any "Link", I'm afraid I can't get anywhere by trying random things.

One thing you may easily test is to boot the other computer, which is working fine, with a live Ubuntu CD/USB, install ethtool on it in the live session, and run it to see what is different there (of course assuming the connection works in the live session on it).

Maybe try the same settings on this card or try a different PCI slot.

**PS:**
You mentioned in your original post -
> /etc/ifplugd/ifplugd.action doesn't exist (so I can't to /etc/ifplugd/ifplugd.action eth0 up or down)
Where did you get that command from? There is indeed nothing like "ifplugd.action". There is only a single path with a single file "/etc/ifplugd/action.d/action_wpa" which is meant for wireless devices.

---

### Post by stevejluke on 2013-10-16
> **varunendra said:**
> ```
sudo ethtool -s eth0 speed 100 duplex full **port [COLOR=#FF0000]tp[/COLOR]** autoneg off
```
So this gave no errors, but when I checked ethtool again it still says it is "mii".

I tried all the other combos of speed, duplex, and port, but didn't find one that worked.

> **varunendra said:**
> One thing you may easily test is to boot the other computer, which is working fine, with a live Ubuntu CD/USB, install ethtool on it in the live session, and run it to see what is different there (of course assuming the connection works in the live session on it).
Great idea.  I will do this next - probably tomorrow.

> **varunendra said:**
> **PS:**
You mentioned in your original post -
[COLOR=#000000]*> /etc/ifplugd/ifplugd.action doesn't exist (so I can't to /etc/ifplugd/ifplugd.action eth0 up or down)*[/COLOR]
Where did you get that command from?

A forum post somewhere... might have been here.  I searched for Ubuntu and the card name, someone was having trouble with Ubuntu 12.04 so I thought it might be related.  Someone mentioned the above command which worked for the OP.  When I couldn't find the command I googled a bit more and found a man page for it ([http://manpages.ubuntu.com/manpages/lucid/man8/ifplugd.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ifplugd.8.html)) which basically said it used underlying ifup and ifdown, which is where I got those commands to try.

---

### Post by stevejluke on 2013-10-19
I checked the settings on another Ubuntu system using the same cable, port, and router.  The settings are pretty much the same, except that it uses 1000baseT/Full duplex, and the port type is mii.  I can't get the problematic computer to take those settings, whenever I try to set the speed to 1000 is says that there is an invalid argument.

So I went tried Ubuntu 13.10 32 bit, and things are a bit different.  I still can't get 1000baseT to work, but when I set it to 100baseT the lights on the card change and the network manager shows it trying to connect.  Running nm-tool shows it trying to get an IP address, but it tries and fails.  Manually configuring the IP address makes the link look complete, nm-tool shows the state is connected, and mii-tool says everything is ok.  But I can't actually connect to the internet or any computer on my network.  ifconfig shows lots of tx bytes but no rx bytes, so I don't think the 'connection' is real.

At this point I have tried Ubuntu 12.04, 13.04, and 13.10 64 bit and 13.10 32 bit.

---

### Post by stevejluke on 2013-10-20
I gave up and swapped the NIC for the card from a Windows machine.  That card is working fine (and the Netgear card I had a problem with in Ubuntu is working fine in Windows).  So I guess the Netegear GA311r10 NIC is one of those things Linux can't use.

---

