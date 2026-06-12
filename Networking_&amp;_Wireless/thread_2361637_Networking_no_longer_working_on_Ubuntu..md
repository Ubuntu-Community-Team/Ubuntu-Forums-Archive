---
title: "Networking no longer working on Ubuntu."
date: 2017-05-18
forum: Networking &amp; Wireless
---

### Post by doctorgenesis on 2017-05-18
Ok, first of all the computer was 'killed' (the switch to the outlet my PC is on was cut off). After that I turned it back on, alas networking no lonber works, even with ethernet. Everything online is not helping and when I go to recovery menu dpkg doesn't work as it can't connect to the net.

---

### Post by wildmanne39 on 2017-05-18
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by doctorgenesis on 2017-05-18
Ok, thank you for replying and welcoming me, wildmanne39!

Here is my terminal input and output:

```
cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
Linux bee39-s5-1554 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:29:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


lspci -nk \ grep -iA2 netUsage: lspci [<switches>]


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
-i <file>    Use specified ID database instead of A2
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file


lsusb
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


iwconfig
lo        no wireless extensions.


rfkill list all


lsmod
Module                  Size  Used by
binfmt_misc            20480  1
kvm                   544768  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 20480  1 ghash_clmulni_intel
input_leds             16384  0
serio_raw              16384  0
video                  40960  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
uas                    24576  0
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
psmouse               131072  0
ahci                   36864  3
libahci                32768  1 ahci
```

---

### Post by doctorgenesis on 2017-05-18
Oh PS; when entering enable networking under recovery mode it shows this in the prompt;

Grep: /etc/resolv.conf: No such file or directory

---

### Post by wildmanne39 on 2017-05-19
We need to see the output of:
```
lspci -nnk | grep -iA2 net
```
please just copy and paste for accuracy.

Thanks

---

### Post by wildmanne39 on 2017-05-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

