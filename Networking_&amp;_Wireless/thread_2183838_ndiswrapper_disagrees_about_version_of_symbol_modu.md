---
title: "ndiswrapper: disagrees about version of symbol module_layout"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by phottomatt on 2013-10-26
[COLOR=#333333][FONT=UbuntuRegular]After updating my gateway to the latest 13.04 I am trying to trouble shoot why the wireless is not working so [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I followed the steps from the ndiswrapper trouble shooting page and that led me to these results.[/FONT][/COLOR][FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333] It seems that the drivers are installed and recognized but I am not getting any WiFi networks to show up in the connections drop down menu. One of my steps included this output. Can anyone help me here? let me know if you need anything else, thanks. [/COLOR][/FONT]

```
lshw -C Network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88W8362e [TopDog] 802.11a/b/g/n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f600ffff memory:f4000000-f400ffff


   dmesg | grep -e ndis -e wlan
[   36.729213] ndiswrapper: disagrees about version of symbol module_layout
[   36.757407] ndiswrapper: disagrees about version of symbol module_layout
[  163.326607] rndis_host 2-2:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-2,           RNDIS device, 02:50:56:54:61:61
[  163.326826] usbcore: registered new interface driver rndis_host
```

---

### Post by wildmanne39 on 2013-10-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by phottomatt on 2013-10-26
Will do, thanks for fixing.

---

### Post by phottomatt on 2013-10-30
Any help would be great, thanks.

---

### Post by phottomatt on 2013-11-04
Anyone? ](*,)](*,)](*,)

---

