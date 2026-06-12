---
title: "another no wifi connection problem"
date: 2020-05-15
forum: Networking &amp; Wireless
---

### Post by smokeyone2 on 2020-05-15
I recently purchased a used Samsung Galaxy Book and after experiencing the wonders of Win 10 installed Ubuntu 20.04.
I have been researching the forums but I am still stuck..
I hope this information helps/assists
Thank you
```
ubuntu@ubuntu-Galaxy-Book-12:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

 *-network                 
       description: Network controller
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 32
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ath10k_pci latency=0
       resources: irq:131 memory:df400000-df5fffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:4.2.2
       logical name: enx00909e9dd80e
       serial: 00:90:9e:9d:d8:0e
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=192.168.1.64 link=yes multicast=yes port=MII speed=1Gbit/s

ubuntu@ubuntu-Galaxy-Book-12:~$ lwconfig

Command 'lwconfig' not found, did you mean:

  command 'iwconfig' from deb wireless-tools (30~pre9-13ubuntu1)
  command 'ldconfig' from deb libc-bin (2.31-0ubuntu9)

Try: sudo apt install <deb name>
```

---

### Post by grahammechanical on 2020-05-15
Well, there is a driver for the wireless adapter and it is ath10k and the adapter is neither Soft blocked or Hard blocked. So, things should be working. What specifically is the problem? The command that failed is

```
iwconfig
```

Look for a Bit Rate, Tx-Power level and signal strength. Also an ESSID (which would be the router you are connecting to)

Regards.

---

### Post by smokeyone2 on 2020-05-15
Thank you for trying to assist - Firefox cannot find a network connection although it does if I plug in the ethernet cable, nor is there the little wifi logo on the tablet. My phone can pick up the signal okay
so assume it's nothing to do with the strength...is there some ubuntu setting I need to adjust...
iwconfig returns no wireless extensions

---

