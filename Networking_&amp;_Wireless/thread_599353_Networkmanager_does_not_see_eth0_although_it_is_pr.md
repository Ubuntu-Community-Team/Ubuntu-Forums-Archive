---
title: "Networkmanager does not see eth0 although it is present"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by wbochum on 2007-11-01
Hello!

Networkmanager does not see eth0:

root@amdubuntu:/var/log# nm-tool

NetworkManager Tool

State: connected

print_devices(): didn't get a reply from NetworkManager.
**There are no available network devices.**



But at the same time:

root@amdubuntu:/var/log#** ifconfig**
**eth0**      Protokoll:Ethernet  Hardware Adresse 00:15:F2:3E:10:6D
          inet Adresse:192.168.1.96  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::215:f2ff:fe3e:106d/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27379 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:6925305 (6.6 MB)  TX bytes:15397872 (14.6 MB)
          Interrupt:10 Basisadresse:0x2000

...

This has the consequence, that some cifs-mounts in fstab are not present after the machine has booted. I can mount them manually by sudo mount -a.

Does anyone know the reason for this behaviour? I looked for documentation of networkmanager and knetworkmanager and elsewhere, but did not hit the solution.

It would help, if one of you could point me to some information as to how networkmanager finds the interfaces eth0 etc.!

---

