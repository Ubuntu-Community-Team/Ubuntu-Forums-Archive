---
title: "Problem with Libertas USB8388 WLAN card"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by manadi on 2008-09-15
Hi all,
       I am using Libertas USB8388 WLAN card with Ubuntu 8.04(downloaded 4 days ago)but am not able to get it working.

       The error(dmesg) says "unable to load firmware" even if the
usb8388.bin file is there in the /lib/firmware.

       dmesg also says "probe of 3-1:1.1 failed with error -12"

Can anyone throw some light on this?:confused:  Any help would be gr8.

Exact dmesg o/p is:

[  875.798211] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.799820] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.802582] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.804291] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.806955] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.808690] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.811455] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.813013] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.815801] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.817536] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.819657] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.822398] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.824621] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.826236] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  875.828212] **usb8xxx: failed to load fw, resetting device!**
[  875.939180] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  876.073664] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  877.215218] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  877.348792] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  878.492852] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  878.629224] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  879.776186] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  879.910627] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  881.059118] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  881.195152] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  882.341802] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  882.477272] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  883.624898] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  883.760232] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  884.911478] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  885.047031] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  886.196476] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  886.330322] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  887.478930] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  887.614193] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff

any idea what is nommu_map_single??

finally


[  887.478930] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  887.614193] nommu_map_single: overflow 7f0000000012+1578 of device mask ffffffff
[  888.760375] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  888.894791] **usb8xxx: probe of 1-3:1.0 failed with error -12**
[  888.894848] usbcore: registered new interface driver usb8xxx

common geeks help me out..........

---

