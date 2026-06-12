---
title: "wifi keeps disconnecting with kubuntu ver 16.04.1"
date: 2016-08-16
forum: Networking &amp; Wireless
---

### Post by anon_private on 2016-08-16
Wifi keeps disconnecting with kubuntu ver 16.04.1.

I can restart it with sudo service network-manager restart, but I need a permanent fix,

Advice please.

---

### Post by banceu_sergiu_ione on 2016-08-16
A start is to see what wifi product your pc have. After try use its name  to see if you can find any thread that has a resolution. 
Use ```
 sudo lshw -c network 
``` to find out the wireless product name.

---

### Post by anon_private on 2016-08-30
All I see is:

```
andrew@andrew-Dell-DM061:~$ sudo lshw - C network
[sudo] password for andrew: 
Hardware Lister (lshw) - B.02.16
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.16)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -c CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          do not display status
        -sanitize       sanitise output (remove sensitive information like serial numbers, etc.)
        -numeric        output numeric IDs (for PCI, USB, etc.)
```

---

### Post by Keith_Helms on 2016-08-30
No space between the dash and the C  

-C

---

### Post by speartip on 2016-08-30
I've had nothing but problems with Network-Manager on 16.04.
Following these instructions solved my problems:
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
If it doesn't work for you, you can easily reverse the process.

---

### Post by slickymaster on 2016-08-30
*Thread moved to **Networking & Wireless**.*

---

### Post by anon_private on 2016-08-30
> **Keith_Helms said:**
> No space between the dash and the C  

-C

Thank you.


'*-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI'

Product is 
RT2561/RT61 802.11g PCI'

> **slickymaster said:**
> *Thread moved to **Networking & Wireless**.*

It is a bit late for a move

> **speartip said:**
> I've had nothing but problems with Network-Manager on 16.04.
Following these instructions solved my problems:
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
If it doesn't work for you, you can easily reverse the process.


I wonder why the developers simply do not re-write the network managers?

---

