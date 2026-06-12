---
title: "3com British Naval Connector network problem"
date: 2005-03-30
forum: Networking &amp; Wireless
---

### Post by RamKrishnan on 2005-03-30
Ok, I have this common 3com ethernet card. It has a British Naval Connector (BNC) port in addition to the regular ethernet port. When I plug in the ethernet cable, the network is up and it works. But I do not know how to set up the BNC to work. Unfortunately, I can only use the BNC in my lab :confused:. I appreciate any help.

sudo lspci:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
0000:02:0f.0 Ethernet controller: 3Com Corporation 3c900B-TPC Etherlink XL [Cyclone] (rev 04)

sudo lsmod:

Module                  Size  Used by
ipv6                  229376  6
speedstep_lib           4228  0
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
freq_table              4100  0
r128                   41984  1
drm                    59412  2 r128
video                  16260  0
battery                10244  0
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
ide_floppy             16896  0
3c59x                  37160  0

(----truncated----------)

Thanks!

---

### Post by alastair on 2005-03-30
Not sure. You might want to see if "ethtool" reports, and lets you use, the additional link i.e.

ethtool eth0

man ethtool

---

