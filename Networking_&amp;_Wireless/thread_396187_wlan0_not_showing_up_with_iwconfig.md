---
title: "wlan0 not showing up with iwconfig"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by graabein on 2007-03-29
Hi, I have a Texas Instruments ACX111 54Mbps wireless interface. Subsystem D-Link DWL-G520+ wireless PCI adapter.

I have read some wikis but I'm still at a loss... Looks like my model should be running with acx driver. It appears with the aforementioned info with **lspci -v | less** and **lsmod | grep acx** gives me two lines:

```
acx            102540  0
usbcore        134912  5 acx,usb_storage,libusual,uhci_hcd
```

But **iwconfig** gives me:

```

lo         no wireless connections.
sit0       no wireless connections.
```

I am running Xubuntu Edgy Eft btw. My card worked on Ubuntu Dapper Drake before. 

What do I do next?


Here is some additional info [WirelessTroubleShootingGuide#lshw]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw"):
[I] If you do not see a driver listed here then there is not one loaded and assigned to the device and it will not show up in iwconfig output or the nework-admin gui.

TODO: describe what it means when it shows *-network UNCLAIMED, and no configuration line is present.[/I]

I have ***-network UNCLAIMED** so I'm guessing I have to assign the loaded **acx** to the device?

---

### Post by spd106 on 2007-03-29
Could you try this command?```
sudo lshw -class network
```

---

### Post by graabein on 2007-03-29
$ **sudo lshw -class network**
```
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 10
       bus info: pci@00:10.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:e8124000-e8125fff iomemory:e8100000-e811ffff irq:9
```

---

### Post by spd106 on 2007-03-29
I think your on the right track, have you tried this wiki page [https://help.ubuntu.com/community/WifiDocs/Driver/acx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111)?

---

### Post by graabein on 2007-03-29
Thanks for the link! That's exactly what I needed. 

[https://help.ubuntu.com/community/WifiDocs/Driver/acx111]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111"):
*Note: If you are using Ubuntu 6.10 Edgy Eft these devices work out of the box if you installed from the regular CD and will work with the Alternate CD if you install the linux-restricted-modules for your kernel. You do not need to continue with this fine instruction. *

I have finally installed the restricted modules and now I got the wireless device up in the networking app. But I can't seem to get online... How do I debug this? 

Here is my $ **iwconfig**:
```
wlan0     IEEE 802.11b+/g+  ESSID:"Kjellerstue"  Nickname:"Jon Oles rom"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:76:24:6A   
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=33/100  Signal level=6/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



[COLOR="SeaGreen"]EDIT: A reboot fixed me up! Thanks for helping, spd106!! :-D[/COLOR]

---

