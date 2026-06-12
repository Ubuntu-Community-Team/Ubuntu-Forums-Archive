---
title: "Broadcom wireless trouble with 8.04"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by challman on 2008-08-26
I've read numerous threads and tried various things to the point that it's all bleeding together. The deal is, it was working fine yesterday and now it's not. The led is amber. The switch is set to on. There isn't a disable option in the BIOS. I've rebooted, lsmod, insmod, fwcutter, etc. and it's still amber. I'm desperate. Basically, it's not even seeing the hardware:

chris@dv9008nr:~$ lspci | grep Bro
chris@dv9008nr:~$    
chris@dv9008nr:~$ lsmod | grep b
Module                  Size  Used by
bluetooth              67748  4 rfcomm,l2cap
vboxdrv              1665840  0
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    17808  0
sbshc                   8960  1 sbs
iptable_filter          4608  0
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0
battery                16776  0
button                 10912  0
jbd                    57000  1 ext3
mbcache                11392  1 ext3
libata                176432  4 sata_nv,ata_generic,pata_amd,pata_acpi
ieee1394              106968  2 sbp2,ohci1394
scsi_mod              178488  5 sbp2,sd_mod,sg,sr_mod,libata
usbcore               169904  3 ohci_hcd,ehci_hcd
fbcon                  46336  0
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit

chris@dv9008nr:~$ uname -a
Linux dv9008nr 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

Any assistance will be greatly appreciated. I'm desperate!!

---

### Post by challman on 2008-08-30
Come to find out, the card is bad. HP has so graciously decided to replace it free even though it's out of warranty.

---

