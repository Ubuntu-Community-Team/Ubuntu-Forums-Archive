---
title: "Internet Connection Ubuntu 16.04"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by arcisd on 2016-07-27
Hello.

I cannot connect to WiFi, there are no connections. WiFi was working really well when I was using Ubuntu 14.04. So, I changed to Lubuntu 16.04, but some days later my WiFi connection dissapeared. Now, I have returned to Ubuntu (to maybe fix the problem), this time in its version 16.04, but I still have no WiFI connection.

Any idea?

```

dalerx@dalerx:~$ iwconfig
lo        no wireless extensions.
eno1      no wireless extensions.

```

```

dalerx@dalerx:~$ ifconfig
eno1      Link encap:Ethernet  direcciónHW 84:34:97:81:c2:ca  
          Direc. inet:192.168.1.41  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::7757:8fc0:8a56:457/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3711 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:2618 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:3811107 (3.8 MB)  TX bytes:374182 (374.1 KB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:659 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:659 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1 
          Bytes RX:66436 (66.4 KB)  TX bytes:66436 (66.4 KB)

```

[ATTACH=CONFIG]270390[/ATTACH]

---

### Post by jeremy31 on 2016-07-27
Please post the results for ```
lspci -nnk | grep -iA2 net; lsusb
```

---

### Post by arcisd on 2016-07-29
Thanks jeremy31. 
The result is the following:

```
dalerx@dalerx:~$ lspci - nnk | grep - iA2 net; lsusb
grep: iA2: No existe el archivo o el directorio
grep: net: No existe el archivo o el directorio
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>][:<class>]        Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
Bus 002 Device 002: ID 064e:d217 Suyin Corp. HP TrueVision HD
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by jeremy31 on 2016-07-29
I edited the post with the commands, please try again as it seems my phone inserted a space where they shouldn't be

---

### Post by arcisd on 2016-08-01
Thanks. Lamentably I am out of home for two weeks and I don't have the computer with me. I'll post the result when I arrive. Greetings!

---

