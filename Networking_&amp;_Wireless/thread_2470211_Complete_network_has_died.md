---
title: "Complete network has died"
date: 2021-12-22
forum: Networking &amp; Wireless
---

### Post by klbogotz on 2021-12-22
My network failed from one day to the next. Had tried to get into recovery mode and booted the computer several times with different key combinations. Obviously something has broken in the process.
Now the network manager icon no longer appears and every intend to connect fails.
Hardware works. I tried this with an installation CD.
I couldn't find any solution in Internet. Hope someone can help me.
Here are some informations of my system:

# ifconfig -a
```
 
enp1s0f0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 30:65:ec:3c:33:a8  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 33  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Lokale Schleife)
        RX packets 55700  bytes 3415082 (3.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 55700  bytes 3415082 (3.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp5s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 28:e3:47:8d:ec:d2  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

#uname
```
Linux acer-3 5.4.0-91-generic #102~18.04.1-Ubuntu SMP Thu Nov 11 14:46:36 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

# sudo lshw -C network
```
*-network DEAKTIVIERT
       Beschreibung: Ethernet interface
       Produkt: QCA8171 Gigabit Ethernet
       Hersteller: Qualcomm Atheros
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Logischer Name: enp1s0f0
       Version: 13
       Seriennummer: 30:65:ec:3c:33:a8
       Kapazität: 1Gbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       Ressourcen: irq:33 memory:f1000000-f103ffff ioport:2000(Größe=128)
  *-network DEAKTIVIERT
       Beschreibung: Kabellose Verbindung
       Produkt: QCA9565 / AR9565 Wireless Network Adapter
       Hersteller: Qualcomm Atheros
       Physische ID: 0
       Bus-Informationen: pci@0000:05:00.0
       Logischer Name: wlp5s0
       Version: 01
       Seriennummer: 28:e3:47:8d:ec:d2
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       Konfiguration: broadcast=yes driver=ath9k driverversion=5.4.0-91-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       Ressourcen: irq:36 memory:f0100000-f017ffff memory:f0180000-f018ffff

```

# rfkill_list_all
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

# lspci
```
01:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 13)
	Subsystem: Acer Incorporated [ALI] QCA8171 Gigabit Ethernet [1025:076b]
	Kernel driver in use: alx
	Kernel modules: alx
--
05:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0642]
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

If more information is needed please tell me.
Regards, Klaus

---

### Post by jeremy31 on 2021-12-22
What results for ```
sudo cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by klbogotz on 2021-12-22
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```
Just noticed that no Bluetooth too

---

### Post by praseodym on 2021-12-22
Please run the wireless script from the sticky thread and show the outputs

---

### Post by klbogotz on 2021-12-22
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs
How should I do that? No connection to nothing. I'm writing from my smartphone. If there is a way to download the script and run it without net connection ...
Ahh - RTM - just got it. Will be back soon.

---

### Post by jeremy31 on 2021-12-22
USB tether to the phone?

---

### Post by TheFu on 2021-12-22
> **klbogotz said:**
> How should I do that? No connection to nothing. I'm writing from my smartphone. If there is a way to download the script and run it without net connection ...
Ahh - RTFM - just got it. Will be back soon.

Boot from the "Try Ubuntu" ISO (install CD?) and save the script on the HDD where the other install is located?  It wouldn't hurt to run the script while in the *Try Ubuntu* environment, since that is working. Then you'd have a working example and a non-working version to compare.  Be certain to save the output file for each script run - use a compare tool - I like **meld**, but diff and sdiff are fine too, to see what is different between the two files.

But after the run on the non-working install, we should be able to tell what the problem is.

---

### Post by klbogotz on 2021-12-23
I'sorry. Run the script with ISO and saved result to pendrive. When y tried to enter in my original system it got frozen. No way to get it work.
Thanks all for your help! I will do a new install instead of wasting your and my time.
Regards Klaus

---

### Post by TheFu on 2021-12-23
> **klbogotz said:**
> I'sorry. Run the script with ISO and saved result to pendrive. When y tried to enter in my original system it got frozen. No way to get it work.
Thanks all for your help! I will do a new install instead of wasting your and my time.
Regards Klaus

Could there be a hardware issue that the Linux system logs would show?  **dmesg** or **journalctl -b** should show those, if they happen in a way that allows logging to happen.

I don't know about this brand of adapters, never used them myself, but with some other brands their drivers seem to treat a full power-off reboot different from just a reboot. I suspect the hardware registers aren't being properly cleared by the drivers, so the random initial values can change based on the initial power spike to the adapter.  Again, I don't know whether that is the case with these drivers or even if the other brand where I've seen something explained in that way still has the issue.

---

